---
title: Extracting Log Files from a Package
description: Extracting Log Files from a Package
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f0ed3889-8880-4e42-9261-6b7bc72a9f53
---

# Extracting Log Files from a Package


The following code sample shows you how to extract log files from a package.

## <span id="C_"></span><span id="c_"></span>C#


``` syntax
//-----------------------------------------------------------------------
// <copyright file="PackageLogExtractor.cs" company="Microsoft">
//    Copyright (c) Microsoft Corporation. All rights reserved.
// </copyright>
//-----------------------------------------------------------------------

[assembly: System.CLSCompliant(true)]
namespace Microsoft.Windows.Kits.Samples
{
    using System;
    using System.Collections.ObjectModel;
    using System.IO;
    using System.Linq;
    using System.Collections.Generic;
    using System.Xml;
    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.Submission;


    internal static class ProgramSettings
    {
        internal static string PackagesDir = null;
        internal static string PackageFile = null;
        internal static bool ExtractLogs = false;
        internal static string LogsDir = null;
        internal static TextWriter Log = null;
        internal static string LogFile = null;
        internal static List<string> DevelopmentPhases = null;
    }

    internal static class Constants
    {
        internal const string PackageExt = ".hlkx";
        internal const string DefaultLogName = "PackageAnalysisLog.txt";
    }

    public class PackageLogExtractor
    {
        static void Main(string[] args)
        {
            if (false == ParseArgs(args))
            {
                ShowUsage();
                return;
            }
            PackageAnalyze(); // all the command line work.

            if (ProgramSettings.Log != null)
            {
                ProgramSettings.Log.Dispose();
            }
        }
        static void ShowUsage()
        {
            string usage = "";


            usage += Environment.NewLine + "PackageLogExtractor.exe [/PackagesDir=<path>]" +
                     Environment.NewLine + "                   [/PackageFile=<path>]" +
                     Environment.NewLine + "                   [/ExtractLogsTo=<path>]" +
                     Environment.NewLine + "                   [/LogFile=<path>]" +
                     Environment.NewLine + "                   [/PhaseFilters=<Level1,Level2,...>]" +
                     Environment.NewLine +
                     Environment.NewLine + "Any parameter in [] is optional." +
                     Environment.NewLine + "Atleast /PackagesDir or /PackageFile must be specified" +
                     Environment.NewLine +
                     Environment.NewLine + "PackageLogExtractor.exe /PackageFile=[FullPathwithHCKFILE.hlkx] /LogFile=[FullPathwithLogFileName]" +
                     Environment.NewLine +
                     Environment.NewLine + "Parameter Descriptions:" +
                     Environment.NewLine + "======================================================================" +
                     Environment.NewLine +
                     Environment.NewLine + "PackagesDir:   Directory to recursively search for package files." +
                     Environment.NewLine +
                     Environment.NewLine + "PackageFile:   Path to single package file to process" +
                     Environment.NewLine +
                     Environment.NewLine + "ExtractLogsTo: Path to directory where extracted logs will be stored" +
                     Environment.NewLine +
                     Environment.NewLine + "LogFile:       Path to file where to write the logging output to." +
                     Environment.NewLine +
                     Environment.NewLine + "PhaseFilters:    A CSV list of HLK Development Phases. Any combination of the following is supported: " +
                     Environment.NewLine + "                        BringUp, DevelopmentAndIntegration, Manufacturing, Reliability, Support, TuningAndValidation." +
                     Environment.NewLine + "                        Default is all phases." +
                     Environment.NewLine +
                     Environment.NewLine;
            //*** Need to update that

            Console.WriteLine(usage);

        }


        static bool ParseArgs(string[] args)
        {

            if ((args.Length == 0) || (args[0].Contains("?")))
            {
                return false;
            }

            foreach (string arg in args)
            {
                if (arg.StartsWith("/PackagesDir=", StringComparison.OrdinalIgnoreCase))
                {
                    ProgramSettings.PackagesDir = Path.GetFullPath(arg.Substring("/PackagesDir=".Length));
                }
                else if (arg.StartsWith("/PackageFile=", StringComparison.OrdinalIgnoreCase))
                {
                    ProgramSettings.PackageFile = Path.GetFullPath(arg.Substring("/PackageFile=".Length));
                }
                else if (arg.StartsWith("/ExtractLogsTo=", StringComparison.OrdinalIgnoreCase))
                {
                    ProgramSettings.LogsDir = Path.GetFullPath(arg.Substring("/ExtractLogsTo=".Length));
                    ProgramSettings.ExtractLogs = true;
                }
                else if (arg.StartsWith("/LogFile=", StringComparison.OrdinalIgnoreCase))
                {
                    string logFile = Path.GetFullPath(arg.Substring("/LogFile=".Length));

                    if (!Directory.Exists(Path.GetDirectoryName(logFile)))
                    {
                        Directory.CreateDirectory(Path.GetDirectoryName(logFile));
                    }
                    ProgramSettings.LogFile = logFile;
                    if (false == string.IsNullOrWhiteSpace(ProgramSettings.LogFile))
                    {
                        try
                        {
                            ProgramSettings.Log = new StreamWriter(ProgramSettings.LogFile);
                        }
                        catch (Exception e)
                        {
                            Console.WriteLine(e.ToString());
                        }
                    }

                }
                else if (arg.StartsWith("/PhaseFilters=", StringComparison.OrdinalIgnoreCase))
                {
                    ProgramSettings.DevelopmentPhases =
                        new List<String>(arg.Substring("/PhaseFilters=".Length).ToUpperInvariant().Split(','));
                }
                else
                {
                    Console.WriteLine("Unrecognized parameter: " + arg);
                    return false;
                }
            }
            return true;
        }

        private static void WriteMessage(string message, params object[] args)
        {
            if (ProgramSettings.Log != null)
            {
                if (args.Length > 0)
                {
                    ProgramSettings.Log.WriteLine(message, args);
                }
                else
                {
                    ProgramSettings.Log.WriteLine(message);
                }
            }
            else
            {
                Console.WriteLine(message, args);
            }
        }

        /// 
        /// <summary>
        /// The Parse engine.
        /// </summary>
        /// 
        public static void PackageAnalyze()
        {
            string[] packageFiles;
            PackageManager manager = null;
            List<DevelopmentPhase> developmentPhases = null;

            //
            // Check development phases
            //
            if (null == ProgramSettings.DevelopmentPhases)
            {
                var phases = (DevelopmentPhase[])Enum.GetValues(typeof(DevelopmentPhase));
                developmentPhases = new List<DevelopmentPhase>(phases);
            }
            else if (0 != ProgramSettings.DevelopmentPhases.Count)
            {
                developmentPhases = new List<DevelopmentPhase>();

                Func<string, string, bool> PhasesMatch = (left, right) => {
                    return string.Equals(left, right, StringComparison.OrdinalIgnoreCase);
                };

                foreach (string phase in ProgramSettings.DevelopmentPhases)
                {
                    if (PhasesMatch("BringUp", phase))
                    {
                        developmentPhases.Add(DevelopmentPhase.BringUp);
                    }
                    else if (PhasesMatch("DevelopmentAndIntegration", phase))
                    {
                        developmentPhases.Add(DevelopmentPhase.DevelopmentAndIntegration);
                    }
                    else if (PhasesMatch("Manufacturing", phase))
                    {
                        developmentPhases.Add(DevelopmentPhase.Manufacturing);
                    }
                    else if (PhasesMatch("Reliability", phase))
                    {
                        developmentPhases.Add(DevelopmentPhase.Reliability);
                    }
                    else if (PhasesMatch("Support", phase))
                    {
                        developmentPhases.Add(DevelopmentPhase.Support);
                    }
                    else if (PhasesMatch("TuningAndValidation", phase))
                    {
                        developmentPhases.Add(DevelopmentPhase.TuningAndValidation);
                    }
                    else
                    {
                        Console.WriteLine(
                            string.Format(
                            "Invalid category level supplied {0}. \nAborting filtering and using all category levels.",
                            phase));

                        //
                        // Just stomp on it with a new one.
                        //
                        var phases = (DevelopmentPhase[])Enum.GetValues(typeof(DevelopmentPhase));
                        developmentPhases = new List<DevelopmentPhase>(phases);
                    }
                }
            }
            if (string.IsNullOrEmpty(ProgramSettings.PackageFile) == false)
            {
                packageFiles = new string[] { ProgramSettings.PackageFile };
            }
            else
            {
                //*** Same extension?
                packageFiles = Directory.GetFiles(ProgramSettings.PackagesDir, "*.hlkx", SearchOption.AllDirectories);
            }

            if (packageFiles.Count() == 0)
            {
                Console.WriteLine("No files in the specified directory");
            }
            else
            {
                foreach (var file in packageFiles)
                {
                    try
                    {
                        ProcessFile(manager, file, developmentPhases);
                    }
                    catch (Exception e)
                    {
                        WriteMessage(e.ToString());
                        Console.WriteLine(e);
                    }
                    finally
                    {
                        if (manager != null)
                        {
                            manager.Dispose();
                        }
                        manager = null;
                    }

                    if (ProgramSettings.Log != null)
                    {
                        ProgramSettings.Log.Flush();
                    }
                }
            }
        }

        static void ProcessFile(ProjectManager manager, string file, List<DevelopmentPhase> developmentPhases)
        {
            WriteMessage("Process package {0}.", file);
            manager = new PackageManager(file);

            List<Project> packageProjects = new List<Project>();
            ReadOnlyCollection<string> projectNames = manager.GetProjectNames();

            foreach (var projectName in projectNames)
            {
                WriteMessage("Validating project: " + projectName);

                bool packageHasResults = false;
                ProjectInfo info = manager.GetProjectInfo(projectName);

                //
                // There wasn't anything run, so no files are going to exist.
                // The OM is going to choke if you try to extract the log files later
                // on.
                //
                if (info.TotalCount == 0)
                {
                    WriteMessage("No results.");
                    continue;
                }
                else
                {
                    WriteMessage(
                        string.Format(
                        ("Results count: \n\t" +
                        "Pass - {0} Fail - {1} Running - {2} NotRun - {3} Total - {4}"),
                        info.PassedCount,
                        info.FailedCount,
                        info.RunningCount,
                        info.NotRunCount,
                        info.TotalCount));

                    packageHasResults = true;
                }

                if (packageHasResults)
                {
                    var project = manager.GetProject(projectName);
                    packageProjects.Add(project);

                    //
                    // Create a list of tests which satisfy filtering condition  
                    //
                    IList<Test> testList = project.GetTests().SelectMany((t => t.DevelopmentPhases.Join(developmentPhases, p => p, d => d, (p, d) => t))).ToList();

                    //
                    // Report only tests which have results > 0.
                    //
                    foreach (Test test in testList.Where(t => (t.GetTestResults().Count > 0)))
                    {
                        ProcessTest(test, project.Name);
                    }
                }
            }
        }

        static void ProcessTest(Test test, string projectName)
        {
            int resultCounter = 1;

            foreach (var result in test.GetTestResults())
            {
                WriteMessage("=============================================");
                string testTargetDevice = string.Join("; ", from a in test.GetTestTargets()
                                                            select a.Name);

                WriteMessage("Test         : " + test.Name);
                WriteMessage("Target       : " + testTargetDevice);
                WriteMessage("RunTime (min): " + System.Math.Round((result.CompletionTime - result.StartTime).TotalMinutes));

                string logsDir = ProgramSettings.LogsDir;

                if (false == string.IsNullOrWhiteSpace(ProgramSettings.LogsDir))
                {
                    logsDir = Path.Combine(ProgramSettings.LogsDir, projectName, test.Name, "Result" + resultCounter.ToString(), test.GetTestTargets().First().Name);

                    foreach (var log in result.GetLogs().Where(x => x.LogType == LogType.TestRun))
                    {
                        log.WriteLogTo(Path.Combine(logsDir, "JobLogs", log.Name));
                    }
                    foreach (var log in result.GetLogs().Where(x => x.LogType == LogType.Gatherer))
                    {
                        log.WriteLogTo(Path.Combine(logsDir, "GathererLogs", log.Name));
                    }
                    foreach (var target in test.GetTestTargets())
                    {
                        string targetXmlDir = Path.Combine(logsDir, @"..\", "TargetXml");
                        if (!Directory.Exists(targetXmlDir))
                        {
                            try
                            {
                                Directory.CreateDirectory(targetXmlDir);
                            }
                            catch (Exception e)
                            {
                                Console.WriteLine("Directory creation failed", e.ToString());

                            }
                        }
                        string fileName = target.Name.Replace(" ", "_") + "_" + target.Machine.Name + ".xml";
                        File.WriteAllText(Path.Combine(targetXmlDir, fileName), target.XmlData);
                    }
                    ProcessResult(result.GetTasks(), Path.Combine(logsDir, "TaskLogs"), test);
                }
                else
                {
                    ProcessResult(result.GetTasks(), null, test);
                }
                WriteMessage("=============================================");
                resultCounter++;
            }
        }


        /// <summary>
        /// The primary result processing engine.  Extracts log files for test tasks, validates results should
        /// be reported for the task based on the WTT Task configuration extracted from the WTT infrastructure
        /// log(s) and stored in the WTTTaskLogData list.
        /// 
        /// This is a recursive method as a particular task can have many child tasks.
        /// </summary>
        /// <param name="taskToProcess">
        /// The HLK Task to process results for.
        /// </param>
        /// <param name="baseLogsDir">
        /// Root log directory for the WTT Log files.
        /// </param>
        /// <param name="test">
        /// The root HLK Test Object.
        /// </param>
        /// <param name="mergedWttLog">
        /// Instance of the WTT Log we're pushing context in and out of
        /// </param>
        /// <param name="indentLevel">
        /// For output purposes, indentation of the task information presented in the console window.
        /// </param>
        static void ProcessResult(IEnumerable<Task> tasksToProcess, string baseLogsDir, Test test, int indentLevel = 1)
        {
            List<Task> tasks = tasksToProcess.OrderBy(x => x.TestResult.StartTime).ToList();

            if (tasks.Count == 0)
            {
                return;
            }

            string msgIndent = new string('\t', indentLevel - 1);
            foreach (var task in tasks)
            {
                if (string.IsNullOrWhiteSpace(baseLogsDir))
                {
                    if (task.TaskType.Equals("RunJob", StringComparison.OrdinalIgnoreCase))  // recurse
                    {
                        ProcessResult(task.GetChildTasks(), null, test, indentLevel + 1);
                    }
                }
                else
                {
                    string taskLogsDir = Path.Combine(baseLogsDir, task.Stage, task.Name);

                    if (task.TaskType.Equals("RunJob", StringComparison.OrdinalIgnoreCase))  // recurse
                    {
                        taskLogsDir = Path.Combine(baseLogsDir, task.Stage, "RunJob-" + task.Name);
                        ProcessResult(task.GetChildTasks(), taskLogsDir, test, indentLevel + 1);
                    }
                    else
                    {
                        foreach (var log in task.GetLogFiles())
                        {
                            log.WriteLogTo(Path.Combine(taskLogsDir, log.Name));
                        }
                    }
                }
            }
        }

    }
}
```

 

 






