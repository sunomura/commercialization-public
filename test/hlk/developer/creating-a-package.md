---
title: Creating a Package
description: Creating a Package
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9ec549c4-5b26-48e6-9fbf-f7fd3a810d7d
---

# Creating a Package


The following code samples show how to:

**C#**

-   [Create a submission package from a project](#bkmk-cs-createsubmissionpackage)

-   [Sign a package using a digital signature stored in a pfx file](#bkmk-cs-signpackage)

**Windows PowerShell®**

-   [Create a submission package from a project](#bkmk-ps-createsubmissionpackage)

-   [Sign a package using a digital signature stored in a pfx file](#bkmk-signpackage)

-   [Determine for what operating systems a driver passes the signing checks](#bkmk-checkos)

-   [Verify a digital certificate](#bkmk-verifiycertificate)

## <span id="C_"></span><span id="c_"></span>**C#**


### <span id="BKMK_CS_CreateSubmissionPackage"></span><span id="bkmk-cs-createsubmissionpackage"></span><span id="BKMK_CS_CREATESUBMISSIONPACKAGE"></span>Create a submission package from a project

This sample shows how to create a submission package from a project.

``` syntax
//-----------------------------------------------------------------------
// <copyright file="CreateAPackage.cs" company="Microsoft">
//    Copyright © Microsoft Corporation. All rights reserved.
// </copyright>
//-----------------------------------------------------------------------

namespace Samples
{
    using System;
    using System.Collections.ObjectModel;
    using System.Linq;
    using System.Collections.Generic;
    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.Submission;
    using System.Collections.Specialized;

    public class CreateAPackage
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Usage: CreateAPackage.exe [ControllerMachineName] [ProjectName] [PathToDrivers] [SaveFileName]");

            if (args.Length != 4)
            {
                Console.WriteLine("Controller Name, Project Name, Path-to-drivers and SaveFile all need to be supplied as an argument.");
                return;
            }

            // first, connect to the controller
            string controllerName = args[0];
            Console.WriteLine("Connecting to controller : {0}", controllerName);
            ProjectManager manager = new DatabaseProjectManager(controllerName);

            // next, load the project
            string projectName = args[1];
            Console.WriteLine("Opening project : {0}", projectName);
            Project project;
            try
            {
                project = manager.GetProject(projectName);
            }
            catch (ProjectManagerException e)
            {
                Console.WriteLine("could not open project {0} \nError : {1}",
                    projectName,
                    e.Message);
                return;
            }

            string driverPath = args[2];
            Console.WriteLine("adding drivers found at {0}", driverPath);

            string saveFileName = args[3];
            Console.WriteLine("saving package to {0}", saveFileName);

            // the steps to create a package are:
            // 1) create a LogoPackageWriter
            // 2) add drivers
            // 3) [optional] add supplemental content
            // 4) save to disk

            PackageWriter packageWriter = new PackageWriter(project);

            // packaging can be somewhat slow because it may have a lot of files to read, so compress and write
            // the packaging information does have an alerting mechanism
            // this will also be alerted for events when processing drivers
            packageWriter.SetProgressActionHandler(SubmissionCreationProgressHandler);


            // the AddDriver method has this definition
            //  public bool AddDriver(
            //        string pathToDriver, 
            //        string pathToSymbols, 
            //        ReadOnlyCollection<Target> targets, 
            //        ReadOnlyCollection<string> locales, 
            //        out StringCollection errorMessages,
            //        out StringCollection warningMessages)
            // the path to symbols is optional and can be null
            
            // each driver package can be associated with one or more targets, and can be from targets in different product instances
            // the possible locales can be retrieved from LogoManager.GetLocaleList()
            // when adding a driver, the driver package is validated that it will be signalable, and additional checks will be performed
            // this means that if this task fails, errorMessages and warningMessages will be filled out to provide information about any
            // problems that are encountered

            // for simplicity, add one driver package as received from the command line, 
            // and associate that with all of the targets in the project
            List<Target> targetList = new List<Target>();
            foreach (ProductInstance pi in project.GetProductInstances())
            {
                targetList.AddRange(pi.GetTargets());
            }

            // also for simplicity, use the first 3 locales returned by GetLocaleList
            List<string> localeList = new List<string>();
            localeList.Add(ProjectManager.GetLocaleList()[0]);
            localeList.Add(ProjectManager.GetLocaleList()[1]);
            localeList.Add(ProjectManager.GetLocaleList()[2]);

            StringCollection errorMessages;
            StringCollection warningMessages;
            
            // call this method
            if (packageWriter.AddDriver(driverPath, null, targetList.AsReadOnly(), localeList.AsReadOnly(), out errorMessages, out warningMessages) == false)
            {
                Console.WriteLine("Add driver failed to add this driver found at : {0}", driverPath);
                foreach (string message in errorMessages)
                {
                    Console.WriteLine("Error: {0}", message);
                }
            }

            // warnings might not cause the method to fail, but may still be present
            if (warningMessages.Count != 0)
            {
                Console.WriteLine("Add driver found warnings in the package found at : {0}", driverPath);                
                foreach (string message in warningMessages)
                {
                    Console.WriteLine("Warning: {0}", message);
                }
            }

            // and now call the save as
            // this save as does the bulk of the work
            packageWriter.Save(saveFileName);

            // now that you're finished writing the package, dispose of it to make sure that the file handle is closed
            packageWriter.Dispose();            
        }

        public static void SubmissionCreationProgressHandler(PackageProgressInfo info)
        {
            Console.WriteLine("Package progress {0} of {1} : {2}", info.Current, info.Maximum, info.Message);
        }
    }
}
```

### <span id="BKMK_CS_SignPackage"></span><span id="bkmk-cs-signpackage"></span><span id="BKMK_CS_SIGNPACKAGE"></span>Sign a package using a digital signature stored in a pfx file

This sample shows how to sign a package using a digital signature stored in a pfx file.

``` syntax
namespace HLK
{
    using System;
    using System.Security.Cryptography.X509Certificates;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.Submission;
 
    class Program
    {
        static void Main(string[] args)
        {
            string packageFile = args[0];
            string pfxFile = args[1];

            Console.WriteLine("Enter the password for the pfx file:");

            string password = Console.ReadLine();

            X509Certificate certificate = new X509Certificate(pfxFile, password);

            PackageManager.Sign(packageFile, certificate);
        }
    }
}
```

## <span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>**PowerShell**


### <span id="BKMK_PS_CreateSubmissionPackage"></span><span id="bkmk-ps-createsubmissionpackage"></span><span id="BKMK_PS_CREATESUBMISSIONPACKAGE"></span>Create a submission package from a project

This sample shows how to create a submission package from a project.

``` syntax
$ObjectModel  = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "microsoft.windows.Kits.Hardware.objectmodel.dll")
$DbConnection = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "microsoft.windows.Kits.Hardware.objectmodel.dbconnection.dll")
$Submission   = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "microsoft.windows.Kits.Hardware.objectmodel.submission.dll")
$Submission   = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "microsoft.windows.Kits.Hardware.objectmodel.submission.package.dll")

    write-Host "Usage: %SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe -file CreateAPackage.ps1 [ControllerMachineName] [ProjectName] [PathToDrivers] [SaveFileName]"

    if ($args.count -ne 4)
    {
        write-host "error: need to provide the controller name, name of the project to package, path to drivers, and save file location "
        return
    }

    $ControllerName = $args[0]
    $projectName = $args[1];
    $driverPath = $args[2];
    $saveFileName = $args[3];
    
# we need to connect to the Server

    if ($ControllerName -eq $null -OR $ControllerName -eq "")
    {
        write-host "Need to supply the controller Name as a parameter to this script"
        return
    }

    if ($projectName -eq $null -OR $projectName -eq "")
    {
        write-host "Need to supply the Project Name as a parameter to this script"
        return
    }

    Write-host "connecting to controller : $ControllerName"
    $Manager = new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection.DatabaseProjectManager -Args $ControllerName, HLKJobs


# next load the project
    write-host "Opening project :$projectName"
    $project = $Manager.GetProject($projectName)
    if ($project -eq $null)
    {
        write-host "unable to load project `n" $error.ToString()
    }

    write-host "adding drivers found at $driverPath"

    write-host "saving package to $saveFileName"

# the steps needed to create a package are:
# 1) create a LogoPackageWriter
# 2) add drivers
# 3) [optional] add supplemental content
# 4) save to disk

    $packageWriter = new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.Submission.PackageWriter -Args $project
   
# the AddDriver method has this definition.
#  public bool AddDriver(
#        string pathToDriver, 
#        string pathToSymbols, 
#        ReadOnlyCollection<Target> targets, 
#        ReadOnlyCollection<string> locales, 
#        out StringCollection errorMessages,
#        out StringCollection warningMessages)
# the path to symbols are optional, and can be null
            
# each driver package can be associated with one or more targets, and can be from targets in different product instances.
# the possible locales can be retrieved from LogoManager.GetLocaleList()
# when adding a driver, the driver package is validated that it will be signal-able, and additional checks will be performed
# this means that if this task fails, the errorMessages and warningMessages will be filled out to provide information about any
# problems encountered

# for simplicity, we are going to add one driver package that we received from the command line, 
# and associate that with all of the targets in the project
    $targetList = New-Object "System.Collections.Generic.List``1[Microsoft.Windows.Kits.Hardware.ObjectModel.Target]"
            
    $Project.GetProductInstances() | foreach {
        $targetlist.AddRange($_.GetTargets())
        }            
            
# also for simplicity, we are going to use the first 3 locales returned by the GetLocaleList.
    $localeList = New-Object "System.Collections.Generic.List``1[System.string]"
    $localeList.Add([Microsoft.Windows.Kits.Hardware.ObjectModel.ProjectManager]::GetLocaleList()[0])
    $localeList.Add([Microsoft.Windows.Kits.Hardware.ObjectModel.ProjectManager]::GetLocaleList()[1])
    $localeList.Add([Microsoft.Windows.Kits.Hardware.ObjectModel.ProjectManager]::GetLocaleList()[2])
            
    $errorMessages = New-Object "System.Collections.Specialized.StringCollection"
    $warningMessages = New-Object "System.Collections.Specialized.StringCollection"
            
# go ahead and call this API
    if ($packageWriter.AddDriver($driverPath, [System.Management.Automation.Language.NullString]::Value, $targetList.AsReadOnly(), $localeList.AsReadOnly(), [ref] $errorMessages, [ref] $warningMessages) -eq $false)
    {
        Write-Host "Add driver failed to add this driver found at : $driverPath"
        foreach ($msg in $errorMessages)
        {
            Write-Host "Error: $msg" 
        }
    }

# warnings might not cause the method to fail, but may still be present
    if ($warningMessages.Count -ne 0)
    {
        Write-Host "Add driver found warnings in the package found at : $driverPath"
        foreach ($msg in $warningMessages)
        {
            Write-Host "Warning: $msg"
        }
    }
                                   
# Since packaging can be somewhat slow, as it may have a lot of files to read, compress and write
# the packaging information does have an alerting mechanism
#  This is not implemented in the PowerShell example, but it is implemented in the C# version
# packageWriter.SetProgressActionHandler(SubmissionCreationProgressHandler);

# and now call the save as
# this save as does the bulk of the work
    $packageWriter.Save($saveFileName);

# now that we're done with writing the package, dispose it to make sure the file handle is closed
    $packageWriter.Dispose();
        

       
```

### <span id="BKMK_SignPackage"></span><span id="bkmk-signpackage"></span><span id="BKMK_SIGNPACKAGE"></span>Sign a package using a digital signature stored in a pfx file

This sample shows how to sign a package using a digital signature stored in a pfx file.

``` syntax
# Load DLLs.
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.submission.dll")

    Write-Host "Usage: %SystemRoot%\System32\WindowsPowershell\v1.0\powershell.exe -file sign_package.ps1 <<Full Path To Package>> <<Full Path to PFX>>"

# The package to sign.
    $packageFile = $args[0]

# The pfx file to use.
    $pfxfile = $args[1]

# The password for the pfx file.
    $pfxpassword = Read-host "Please enter the password for the pfx file" -AsSecureString

# Load the certificate.
    $cert = new-object -typename System.Security.Cryptography.X509Certificates.X509Certificate($pfxfile, $pfxpassword)

# Sign the package.
    [Microsoft.Windows.Kits.Hardware.ObjectModel.Submission.PackageManager]::Sign($packageFile, $cert)
```

>[!NOTE]
>  
When signing some (large) packages using PowerShell, you might see an exception such as "Unable to determine the identity of domain". When this exception occurs, please use the managed API (see [http://msdn.microsoft.com/en-us/library/windows/hardware/jj123504.aspx\#BKMK\_CS\_SignPackage](http://msdn.microsoft.com/en-us/library/windows/hardware/jj123504.aspx)) as a work-around."

 

### <span id="BKMK_CheckOS"></span><span id="bkmk-checkos"></span><span id="BKMK_CHECKOS"></span>Determine for what operating systems a driver passes the signing checks

This sample shows how to determine for what operating systems a driver passes the signing checks.

``` syntax
# Load DLLs.
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.submission.dll")

    Write-Host "Usage: %SystemRoot%\System32\WindowsPowershell\v1.0\powershell.exe -file check_downlevel_os.ps1 <<Full Path To Package>>"

# The package file.
    $packageFile = $args[0]

# Create a package manager.
    $Manager = new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.Submission.PackageManager -Args $packageFile

    $Manager.GetProjectNames() | foreach {
        Write-Host Examining Project $_
        $Project = $Manager.GetProject($_)
        $Project.GetProductInstances() | foreach {
            $_.GetTargetFamilies() | foreach {
                $_.GetTargets() | foreach {
                    Write-Host Examining Target $_.Name
                    $_.GetDrivers() | foreach {
                        Write-Host Driver is signable for the following platforms
                        Write-Host $_.SignabilityResults
                    }
                }
            }
        }
    }

# Clean up.
    $Manager.Dispose()
```

### <span id="BKMK_VerifiyCertificate"></span><span id="bkmk-verifiycertificate"></span><span id="BKMK_VERIFIYCERTIFICATE"></span>Verify a digital certificate

This sample shows how to verify a digital certificate.

``` syntax
# Load DLLs.
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.submission.dll")

    Write-Host "Usage: %SystemRoot%\System32\WindowsPowershell\v1.0\powershell.exe -file verify_certificate.ps1 <<Full Path To Package>>"

# The package file.
    $packageFile = $args[0]

# Create a package manager.
    $Manager = new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.Submission.PackageManager -Args $packageFile

# Write out the certificate object.
    Write-host $Manager.Certificate

# Clean Up.
    $Manager.Dispose()
```

 

 






