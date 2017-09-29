---
title: Finding missing tests
description: Finding missing tests
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7F3AA24F-5289-4391-9A97-A4F40DD6AE75
---

# Finding missing tests


This sample shows how to find tests that are missing from a package. The sample is divided into four files:

-   [Program.cs](#program-cs): main program file
-   [PlaylistDL.cs](#playlistdl-cs): class used to represent a playlist file for downlevel operating systems
-   [PlaylistHelper.cs](#playlisthelper-cs): helper class used for deserialization of downlevel playlists
-   [PlaylistDL.xsd](#playlistdl-xsd): schema that is used to validate the output playlist XML file. Place this file next to your executable.

## <span id="program_cs"></span><span id="PROGRAM_CS"></span>Program.cs


``` syntax
//--------------------------------------------------------------------------------------------------------------------
// <copyright file="Program.cs" company="Microsoft">
//    Copyright (c) Microsoft. All rights reserved.
// </copyright>
//--------------------------------------------------------------------------------------------------------------------

namespace Sample.MissingTest
{
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Collections.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.Submission;


    /// <summary>
    /// Find missing tests in a package
    /// </summary>
    public class Program
    {
        static string playlistRS1;
        static string playlistRS2;
        static bool bShowPassingResults = false;

        /// <summary>
        /// Entry point for the sample
        /// <param name="args"></param>
        /// </summary>
        public static void Main(string[] args)
        {
            int missingTestCount = 0;
            if (args.Length != 4)
            {
                Console.WriteLine("Invalid Parameters!");
                Console.WriteLine("Usage:");
                Console.WriteLine("Sample.MissingTest.exe <path to hlkx package> <path to RS1 playlist> <path to RS2 playlist> <True or False for showing pass results>");
                return;
            }

            playlistRS1 = args[1];
            playlistRS2 = args[2];
            if (String.Compare("true", args[3], true) == 0)
            {
                bShowPassingResults = true;
            }
            missingTestCount = FindMissingResults(args[0]);



        }

        /// <summary>
        /// Uses the given <see cref="PlaylistDL"/> to find tests for each <see cref="Target"/> in the the given list 
        /// of <see cref="ProductInstance"/> objects that should be present but are not.
        /// </summary>
        /// <param name="packagePath">Path to the package.</param>
        /// <param name="playlistPath">Path to the playlist to be applied</param>
        /// <returns>
        /// Count of missing tests for a given package/>.
        /// </returns>
        private static int FindMissingResults(string packagePath)
        {
            int missingTestCount = 0;

            PackageManager manager = new PackageManager(packagePath);

            Console.WriteLine("Package version : " + manager.PackageVersion);

            foreach (ProjectInfo projectInfo in manager.GetProjectInfoList())
            {
                Console.WriteLine("Project name : " + projectInfo.Name);

                if (!string.IsNullOrEmpty(projectInfo.Name))
                {
                    Project project = manager.GetProject(projectInfo.Name);

                    foreach (ProductInstance pi in project.GetProductInstances())
                    {
                        missingTestCount = 0;
                        Console.WriteLine();
                        Console.WriteLine("\r\nTest results for package: {0}, OS: {1}, Controller Veriosn:{2}\r\n", manager.FileName, pi.OSPlatform.Name, pi.Project.ProjectManager.Version.Build);

                        ReadOnlyCollection<Target> currentPiTargets = pi.GetTargets();
                        if (pi.GetPlaylists().Count() == 0)
                        {
                            Console.WriteLine("Using playlist: {0} for validation", playlistRS1);
                            Console.WriteLine();

                            PlaylistDL playlistDL = PlaylistHelper.DeserializePlaylistDL(playlistRS1);
                            Dictionary<Target, List<PlaylistTestDL>> missingTests = PlaylistHelper.GetMissingTests(playlistDL, pi);
                            Console.WriteLine("Missing Tests:");
                            missingTests.ToList().ForEach(item => Console.WriteLine("{0}:{1}", item.Value[0].Name, item.Value[0].Id));
                            Console.WriteLine();
                            missingTestCount = missingTests.Count();

                            List<Test> projectTotalTestList = PlaylistHelper.GetTestsFromProjectThatMatchPlaylistDL(playlistDL, pi);
                            // List results for tests in playlist matching to currently loaded project   
                            GetTestDetails(projectTotalTestList, currentPiTargets, false);
                        }
                        else
                        {
                            Console.WriteLine("Using playlist: {0} for validation", playlistRS2);
                            Console.WriteLine();

                            // Get all the tests for current project from playlist
                            PlaylistManager playlistlManger = new PlaylistManager(project);
                            Playlist playlist = PlaylistManager.DeserializePlaylist(playlistRS2);
                            List<Test> projectTotalTestList = playlistlManger.GetTestsFromProjectThatMatchPlaylist(playlist);
                            missingTestCount = GetTestDetails(projectTotalTestList, currentPiTargets);
                        }

                        Console.WriteLine();
                        Console.WriteLine("Missing Tests = {0}", missingTestCount);
                    }
                }
            }

            return missingTestCount;
        }

        private static int GetTestDetails(List<Test> projectTotalTestList, ReadOnlyCollection<Target> targets, bool bRS2 = true)
        {
            int missingTestCount = 0;
            List<Test> missingTests = new List<Test>();
            List<Test> testResults = new List<Test>();
            projectTotalTestList.ForEach(
                                item =>
                                {
                                    var testTargets = item.GetTestTargets();
                                    bool targetResult = !testTargets.Except(targets).Any();
                                    if (item.GetTestResults().Count == 0 && bRS2 && targetResult)
                                    {
                                        missingTests.Add(item);
                                        missingTestCount++;
                                    }
                                    else if (targetResult)
                                    {
                                        testResults.Add(item);
                                    }
                                });


            if (bRS2)
            {
                Console.WriteLine("Missing Tests:");
                missingTests.ForEach(item => Console.WriteLine("{0}:{1}", item.Name, item.Id));
                Console.WriteLine();
            }

            Console.WriteLine("Test Results:");
            testResults.ForEach(
                    item =>
                    {
                        var allResults = item.GetTestResults().OrderByDescending(r => r.CompletionTime);
                        var passedResult = allResults.Where(test => test.Status == TestResultStatus.Passed).Count();
                        var failledResult = allResults.Where(test => test.Status == TestResultStatus.Failed).Count();
                        var canceledResult = allResults.Where(test => test.Status == TestResultStatus.Canceled).Count();
                        var notRun = allResults.Where(test => test.Status == TestResultStatus.NotRun).Count();
                        if (passedResult == 0 || failledResult > 0 || canceledResult > 0 || notRun > 0)
                        {
                            Console.WriteLine("{0}:{1} - Passed Test:{2}, Failed Test:{3}, Canceled Test:{4}, Not Run:{5} ", item.Name, item.Id, passedResult, failledResult, canceledResult, notRun);
                        }
                        else
                        {
                            if (bShowPassingResults)
                            {
                                Console.WriteLine("{0}:{1} - Passed Test:{2}, Failed Test:{3}, Canceled Test:{4}, Not Run:{5} ", item.Name, item.Id, passedResult, failledResult, canceledResult, notRun);
                            }
                        }
                    });

            return missingTestCount;
        }
    }
}
```

## <span id="playlistdl_cs"></span><span id="PLAYLISTDL_CS"></span>PlaylistDL.cs


``` syntax
//--------------------------------------------------------------------------------------------------------------------
// <copyright file="PlaylistDL.cs" company="Microsoft">
//    Copyright (c) Microsoft. All rights reserved.
// </copyright>
//--------------------------------------------------------------------------------------------------------------------

namespace Sample.MissingTest
{
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Xml.Serialization;

    /// <summary>
    /// Represents a Playlist file as a .NET Class
    /// </summary>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("xsd", "4.0.30319.33440")]
    [System.SerializableAttribute]
    [System.Diagnostics.DebuggerStepThroughAttribute]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(TypeName = "Playlist", Namespace = "http://schemas.microsoft.com/hlk/playlist/2014")]
    [System.Xml.Serialization.XmlRootAttribute(ElementName = "Playlist", Namespace = "http://schemas.microsoft.com/hlk/playlist/2014", IsNullable = false)]
    public partial class PlaylistDL
    {
        /// <summary>
        /// Playlist's list of tests
        /// </summary>
        private PlaylistTestDL[] testSetField;

        /// <summary>
        /// Playlist Id
        /// </summary>
        private string idField;

        /// <summary>
        /// Playlist version
        /// </summary>
        private string versionField;

        /// <summary>
        /// Playlist name
        /// </summary>
        private string nameField;

        /// <summary>
        /// Gets or sets the list of <see cref="PlaylistTestDL"/>s.
        /// </summary>
        [System.Xml.Serialization.XmlElementAttribute("Test")]
        public PlaylistTestDL[] TestSet
        {
            get
            {
                return this.testSetField;
            }

            set
            {
                this.testSetField = value;
            }
        }

        /// <summary>
        /// Gets or sets the Playlist Id
        /// </summary>
        [System.Xml.Serialization.XmlAttributeAttribute]
        public string Id
        {
            get
            {
                return this.idField;
            }

            set
            {
                this.idField = value;
            }
        }

        /// <summary>
        /// Gets or sets the Playlist Version
        /// </summary>
        [System.Xml.Serialization.XmlAttributeAttribute]
        public string Version
        {
            get
            {
                return this.versionField;
            }

            set
            {
                this.versionField = value;
            }
        }

        /// <summary>
        /// Gets or sets the Playlist Version
        /// </summary>
        [System.Xml.Serialization.XmlAttributeAttribute]
        public string Name
        {
            get
            {
                return this.nameField;
            }

            set
            {
                this.nameField = value;
            }
        }
    }

    /// <summary>
    /// Represents a test element inside of a Playlist file.
    /// </summary>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("xsd", "4.0.30319.33440")]
    [System.SerializableAttribute]
    [System.Diagnostics.DebuggerStepThroughAttribute]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(TypeName = "Test", Namespace = "http://schemas.microsoft.com/hlk/playlist/2014")]
    public partial class PlaylistTestDL
    {
        /// <summary>
        /// Test's list of features
        /// </summary>
        private PlaylistFeature[] featureSetField;

        /// <summary>
        /// Test's list of platforms 
        /// </summary>
        private PlaylistOSPlatform[] osPlatformSetField;

        /// <summary>
        /// Test Id
        /// </summary>
        private string idField;

        /// <summary>
        /// Test name
        /// </summary>
        private string nameField;

        /// <summary>
        /// Test version
        /// </summary>
        private string versionField;

        /// <summary>
        /// Gets or sets the test Id
        /// </summary>
        [System.Xml.Serialization.XmlAttributeAttribute]
        public string Id
        {
            get
            {
                return this.idField;
            }

            set
            {
                this.idField = value;
            }
        }

        /// <summary>
        /// Gets or sets the test name
        /// </summary>
        [System.Xml.Serialization.XmlAttributeAttribute]
        public string Name
        {
            get
            {
                return this.nameField;
            }

            set
            {
                this.nameField = value;
            }
        }

        /// <summary>
        /// Gets or sets the test version 
        /// </summary>
        [System.Xml.Serialization.XmlAttributeAttribute]
        public string Version
        {
            get
            {
                return this.versionField;
            }

            set
            {
                this.versionField = value;
            }
        }

        /// <summary>
        /// Gets or sets the list of <see cref="PlaylistFeature"/> objects.
        /// </summary>
        [System.Xml.Serialization.XmlElementAttribute("Feature")]
        public PlaylistFeature[] FeatureSet
        {
            get
            {
                return this.featureSetField;
            }

            set
            {
                this.featureSetField = value;
            }
        }

        /// <summary>
        /// Gets or sets the list of <see cref="PlaylistOSPlatform"/> objects.
        /// </summary>
        [System.Xml.Serialization.XmlElementAttribute("OSPlatform")]
        public PlaylistOSPlatform[] OSPlatformSet
        {
            get
            {
                return this.osPlatformSetField;
            }

            set
            {
                this.osPlatformSetField = value;
            }
        }
    }

    /// <summary>
    /// Represents a Feature element inside of a Test element.
    /// </summary>
    [System.SerializableAttribute]
    [System.Diagnostics.DebuggerStepThroughAttribute]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(TypeName = "Feature", Namespace = "http://schemas.microsoft.com/hlk/playlist/2014")]
    public partial class PlaylistFeature
    {
        /// <summary>
        /// Feature name
        /// </summary>
        private string nameField;

        /// <summary>
        /// Gets or sets the Feature name
        /// </summary>
        [System.Xml.Serialization.XmlAttributeAttribute]
        public string Name
        {
            get
            {
                return this.nameField;
            }

            set
            {
                this.nameField = value;
            }
        }
    }

    /// <summary>
    /// Represents an OS Platform element inside of a Test.
    /// </summary>
    [System.SerializableAttribute]
    [System.Diagnostics.DebuggerStepThroughAttribute]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(TypeName = "OSPlatform", Namespace = "http://schemas.microsoft.com/hlk/playlist/2014")]
    public partial class PlaylistOSPlatform
    {
        /// <summary>
        /// OS Platform name
        /// </summary>
        private string nameField;

        /// <summary>
        /// Gets or sets the OS Platform name
        /// </summary>
        [System.Xml.Serialization.XmlAttributeAttribute]
        public string Name
        {
            get
            {
                return this.nameField;
            }

            set
            {
                this.nameField = value;
            }
        }
    }
}
```

## <span id="playlisthelper_cs"></span><span id="PLAYLISTHELPER_CS"></span>PlaylistHelper.cs


``` syntax
//--------------------------------------------------------------------------------------------------------------------
// <copyright file="PlaylistHelper.cs" company="Microsoft">
//    Copyright (c) Microsoft. All rights reserved.
// </copyright>
//--------------------------------------------------------------------------------------------------------------------

namespace Sample.MissingTest
{
    using System;
    using System.Collections.Generic;
    using System.Globalization;
    using System.IO;
    using System.Linq;
    using System.Xml;
    using System.Xml.Schema;
    using System.Xml.Serialization;
    using Microsoft.Windows.Kits.Hardware.ObjectModel;

    /// <summary>
    /// Class containing helper methods for finding missing tests for
    /// down level (RS1/TH2) OSes
    /// </summary>
    public class PlaylistHelper
    {
        /// <summary>
        /// Playlist file extension
        /// </summary>
        private const string PlaylistFileExtension = ".xml";

        /// <summary>
        /// Uses the given <see cref="PlaylistDL"/> to find tests for each <see cref="Target"/> in the the given list 
        /// of <see cref="ProductInstance"/> objects that should be present but are not.
        /// </summary>
        /// <param name="playlistDL">The <see cref="PlaylistDL"/> for which missing tests will be found.</param>
        /// <param name="pi">The <see cref="ProductInstance"/> objects to check in.</param>
        /// <returns>
        /// A dictionary containing a list of missing tests for each <see cref="Target"/> in the <paramref name="pis"/>.
        /// </returns>
        /// <remarks>
        /// Tests are determined to be missing if they have features that match the features of a Target, but the Test
        /// itself does not exist for the Target.
        /// This functionality should only be used in conjunction with official Playlist files for the Compact program.
        /// </remarks>
        internal static Dictionary<Target, List<PlaylistTestDL>> GetMissingTests(PlaylistDL playlistDL, ProductInstance pi)
        {
            if (playlistDL == null)
            {
                throw new ArgumentNullException("playlist");
            }

            if (pi == null)
            {
                throw new ArgumentNullException("pi");
            }

            Dictionary<Target, List<PlaylistTestDL>> missingTestsDL = new Dictionary<Target, List<PlaylistTestDL>>();

            string productInstancePlatformName = pi.OSPlatform.Name;

            foreach (TargetFamily tf in pi.GetTargetFamilies())
            {
                if (tf.GetTargets().Count < 1)
                {
                    continue;
                }

                List<Test> targetFamilyTests = tf.GetTests().ToList();
                List<Feature> targetFamilyFeatures = new List<Feature>(tf.GetFeatures());
                List<PlaylistTestDL> targetFamilyMissingTestsDL = new List<PlaylistTestDL>();

                foreach (PlaylistTestDL playlistTestDL in playlistDL.TestSet)
                {
                    if (FeaturesMatch(targetFamilyFeatures, playlistTestDL) &&
                        OSPlatformsMatch(productInstancePlatformName, playlistTestDL))
                    {
                        if (!targetFamilyTests.Exists(test => test.Id.Equals(playlistTestDL.Id, StringComparison.OrdinalIgnoreCase)))
                        {
                            targetFamilyMissingTestsDL.Add(playlistTestDL);
                        }
                    }
                }

                if (targetFamilyMissingTestsDL.Count > 0)
                {
                    // since all Targets in a TargetFamily should be equivalent, just return the first one
                    missingTestsDL.Add(tf.GetTargets().FirstOrDefault(), targetFamilyMissingTestsDL);
                }
            }

            return missingTestsDL;
        }

        /// <summary>
        /// Deserializes a playlist file into a <see cref="PlaylistDL"/> object
        /// </summary>
        /// <param name="playlistImportPath">full path to the playlist file</param>
        /// <returns>a <see cref="PlaylistDL"/> created from the given file.</returns>
        /// <exception cref="ArgumentNullException">When the given path is null.</exception>
        /// <exception cref="ArgumentException">When the given path is empty or has invalid characters.</exception>
        /// <exception cref="PlaylistException">When the given Playlist file does not conform to the schema.</exception>
        internal static PlaylistDL DeserializePlaylistDL(string playlistImportPath)
        {
            if (playlistImportPath == null)
            {
                throw new ArgumentNullException("playlistImportPath");
            }

            playlistImportPath = GetCleanFilePath(playlistImportPath);

            if (!File.Exists(playlistImportPath))
            {
                string message = string.Format(CultureInfo.InvariantCulture, "Playlist file could not be found: '{0}'.", playlistImportPath);
                throw new PlaylistException(message);
            }

            try
            {
                ValidateSchema(playlistImportPath);
            }
            catch (XmlException xmlException)
            {
                string message = string.Format(
                    CultureInfo.InvariantCulture,
                    "The Playlist file '{0}' has malformed XML contents.\n{1}",
                    playlistImportPath,
                    xmlException.Message);
                throw new PlaylistException(message, xmlException);
            }
            catch (PlaylistException playlistException)
            {
                string exMessage = playlistException.InnerException != null ? playlistException.InnerException.Message : string.Empty;
                string message = string.Format(CultureInfo.InvariantCulture, "Playlist file '{0}' has an incorrect format: '{1}'.", playlistImportPath, exMessage);
                throw new PlaylistException(message, playlistException);
            }

            PlaylistDL playlistDL = new PlaylistDL();
            XmlSerializer serializer = new XmlSerializer(typeof(PlaylistDL));

            try
            {
                using (FileStream fs = File.Open(playlistImportPath, FileMode.Open, FileAccess.Read, FileShare.Read))
                {
                    playlistDL = (PlaylistDL)serializer.Deserialize(fs);
                }
            }
            catch (Exception ex)
            {
                if (ex is IOException || ex is UnauthorizedAccessException)
                {
                    string message = string.Format(
                        CultureInfo.InvariantCulture,
                        "Could not open the Playlist file '{0}': {1}",
                        playlistImportPath,
                        ex.Message);
                    throw new PlaylistException(message, ex);
                }

                throw;
            }

            if (playlistDL.TestSet == null)
            {
                string message = string.Format(
                    CultureInfo.InvariantCulture,
                    "The Playlist file '{0}' does not contain any tests.",
                    playlistImportPath);
                throw new PlaylistException(message);
            }

            // check that the Guids are correctly formed
            foreach (PlaylistTestDL playlistTestDL in playlistDL.TestSet)
            {
                try
                {
                    Guid guid = new Guid(playlistDL.Id);
                }
                catch (FormatException badGuidException)
                {
                    string message = string.Format(CultureInfo.InvariantCulture, "A Playlist Test has an invalid Id: '{0}'.", playlistDL.Id);
                    throw new PlaylistException(message, badGuidException);
                }
            }

            return playlistDL;
        }
        
        /// <summary>
        /// Determines whether any of the given <see cref="Feature"/> objects match the features for the given <see cref="PlaylistTest"/>.
        /// </summary>
        /// <param name="features">list of <see cref="Feature"/> objects</param>
        /// <param name="playlistTestDL">test from a playlist that contains features to check against <paramref name="features"/></param>
        /// <returns>whether <paramref name="features"/> and <paramref name="playlistTestDL"/> have any features in common</returns>
        private static bool FeaturesMatch(List<Feature> features, PlaylistTestDL playlistTestDL)
        {
            if (features == null)
            {
                return false;
            }

            if (playlistTestDL == null)
            {
                return false;
            }

            if (playlistTestDL.FeatureSet == null)
            {
                return false;
            }

            if (features.Count == 0)
            {
                return false;
            }

            foreach (PlaylistFeature feature in playlistTestDL.FeatureSet)
            {
                if (features.Exists(feat => feat.FullName.Equals(feature.Name, StringComparison.OrdinalIgnoreCase)))
                {
                    return true;
                }
            }

            return false;
        }

        /// <summary>
        /// Determines whether the given <see cref="OSPlatform"/> name matches any of the OSPlatforms for the given <see cref="PlaylistTest"/>.
        /// </summary>
        /// <param name="osPlatformName">platform name to check for</param>
        /// <param name="playlistTestDL">test from a playlist that contains OS platforms to check against <paramref name="osPlatformName"/></param>
        /// <returns>whether <paramref name="osPlatformName"/> and <paramref name="playlistTestDL"/> have any OS Platforms in common</returns>
        private static bool OSPlatformsMatch(string osPlatformName, PlaylistTestDL playlistTestDL)
        {
            if (osPlatformName == null)
            {
                return false;
            }

            if (playlistTestDL == null)
            {
                return false;
            }

            if (playlistTestDL.OSPlatformSet == null)
            {
                return false;
            }

            if (playlistTestDL.OSPlatformSet.Length == 0)
            {
                return false;
            }

            if (playlistTestDL.OSPlatformSet.Any(platform => osPlatformName.Equals(platform.Name, StringComparison.OrdinalIgnoreCase)))
            {
                return true;
            }

            return false;
        }

        /// <summary>
        /// Validates the given Playlist file against the Playlist schema
        /// </summary>
        /// <param name="filePath">full path to the Playlist file</param>
        /// <exception cref="XmlException">If the file's XML is not well-formed XML.</exception>
        private static void ValidateSchema(string filePath)
        {
            XmlReaderSettings readerSettings = new XmlReaderSettings();
            readerSettings.Schemas.Add("http://schemas.microsoft.com/hlk/playlist/2014", "PlaylistDL.xsd");
            readerSettings.ValidationType = ValidationType.Schema;

            XmlReader xmlReader = XmlReader.Create(filePath, readerSettings);
            XmlDocument document = new XmlDocument();
            document.Load(xmlReader);

            ValidationEventHandler eventHandler = new ValidationEventHandler(PlaylistSchemaValidationEventHandler);
            document.Validate(eventHandler);
        }

        /// <summary>
        /// Handles the case where a Playlist schema validation has failed.
        /// </summary>
        /// <param name="sender">the object this handler was called from</param>
        /// <param name="e">the validation information</param>
        /// <exception cref="PlaylistException">throws whenever this method is called</exception>
        private static void PlaylistSchemaValidationEventHandler(object sender, ValidationEventArgs e)
        {
            throw new PlaylistException("The playlist's contents do not match the Playlist schema.", e.Exception);
        }

        /// <summary>
        /// Performs checks and actions on the given <paramref name="filePath"/> string:
        /// 1) Checks that the file name does not contain any invalid characters
        /// 2) Checks that the file path does not contain any invalid characters
        /// 3) Expands environment variables before returning a guaranteed clean path.
        /// </summary>
        /// <param name="filePath">path string to check/clean</param>
        /// <exception cref="ArgumentException">
        /// The given <paramref name="filePath"/> is empty or fails one of the above checks.
        /// </exception>
        /// <returns>a checked/cleaned file path string with environment variables expanded</returns>
        private static string GetCleanFilePath(string filePath)
        {
            // Ensure that the playlist path is not null.
            if (filePath == null)
            {
                throw new ArgumentNullException("filePath");
            }

            if (string.IsNullOrEmpty(filePath))
            {
                throw new ArgumentException("Parameter filePath is empty.", "filePath");
            }

            // Ensure that the file name provided does not contain invalid file name characters.
            if (Path.GetFileName(filePath).IndexOfAny(Path.GetInvalidFileNameChars()) != -1)
            {
                ArgumentException exception = new ArgumentException("filePath contains invalid file name characters");
                throw exception;
            }

            // Ensure that the path provided does not contain invalid path characters
            if (Path.GetFullPath(filePath).IndexOfAny(Path.GetInvalidPathChars()) != -1)
            {
                ArgumentException exception = new ArgumentException("filePath contains invalid path characters");
                throw exception;
            }

            if (!Path.GetExtension(filePath).Equals(PlaylistFileExtension, StringComparison.OrdinalIgnoreCase))
            {
                string msg = string.Format(
                    CultureInfo.InvariantCulture,
                    "filePath contains an invalid extension: '{0}'.",
                    Path.GetExtension(filePath));
                ArgumentException exception = new ArgumentException(msg);
                throw exception;
            }

            string expandedPlaylistName = Environment.ExpandEnvironmentVariables(filePath);

            return expandedPlaylistName;
        }
    }
}
```

## <span id="playlistdl_xsd"></span><span id="PLAYLISTDL_XSD"></span>PlaylistDL.xsd


``` syntax
<?xml version="1.0" encoding="utf-8"?>
<xs:schema 
  elementFormDefault="qualified"
  xmlns:xs="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/hlk/playlist/2014"
  targetNamespace="http://schemas.microsoft.com/hlk/playlist/2014">
  <xs:simpleType name="Guid">
    <xs:annotation>
      <xs:documentation>
        The 'guid' type requires a 32 digit hyphen separated string, with digits in groups of 8-4-4-4-12 in that order. 
        The correct format: 00000000-0000-0000-0000-000000000000.
        Each digit must be a hex value.
      </xs:documentation>
    </xs:annotation>
    <xs:restriction base="xs:string">
      <xs:pattern value="[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="Version">
    <xs:annotation>
      <xs:documentation>
        The 'version' type requires a 'Major.Minor' format composed of integers.
        For example, '3.15', or '15.1'.
        Both Major and Minor may have up to 4 characters. E.g. 9999.9999
      </xs:documentation>
    </xs:annotation>
    <xs:restriction base="xs:string">
      <xs:pattern value="[0-9]{1,4}\.[0-9]{1,4}"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="FeatureName">
    <xs:annotation>
      <xs:documentation>
        A FeatureName type consists of strings separated by periods.
        There should be no spaces in the FeatureName.
        The max length for FeatureName is 150 characters.
      </xs:documentation>
    </xs:annotation>
    <xs:restriction base="xs:string">
      <xs:pattern value="^([a-zA-Z0-9]+\.?)+[^\. ]$"/>
      <xs:maxLength value="150"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Playlist">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Test" minOccurs="0" maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Feature" minOccurs="0" maxOccurs="unbounded">
                <xs:complexType>
                  <xs:attribute name="Name" type="FeatureName" use="required"/>
                </xs:complexType>
              </xs:element>
              <xs:element name="OSPlatform" minOccurs="0" maxOccurs="unbounded">
                <xs:complexType>
                  <xs:attribute name="Name" type="xs:string" use="required"/>
                </xs:complexType>
              </xs:element>
            </xs:sequence>
            <xs:attribute name="Id" type="Guid" use="required"/>
            <xs:attribute name="Name" type="xs:string"/>
            <xs:attribute name="Version" type="Version"/>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
      <xs:attribute name="Id" type="Guid" use="required"/>
      <xs:attribute name="Name" type="xs:string"/>
      <xs:attribute name="Version" type="Version" />
    </xs:complexType>
  </xs:element>
</xs:schema>
```

 

 






