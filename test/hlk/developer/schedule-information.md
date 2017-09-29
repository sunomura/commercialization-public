---
title: Schedule Information
description: Schedule Information
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7c4665bd-034c-4df1-a9f9-0ab92d785cf7
---

# Schedule Information


This sample shows the usage of the DistributionOption enumeration and associated test metadata flags.

## <span id="C_"></span><span id="c_"></span>**C#**


``` syntax
namespace Microsoft.Windows.Kits.Samples  
{  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
  
    using Microsoft.Windows.Kits.Hardware.ObjectModel;  
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;  
  
    /// <summary>
    /// Sample for changes for new usage of test's Distribution options and new test metadata flags.
    /// </summary>
    class UpdatedScheduleInformationSample  
    {  
        /// <summary>
        /// Main entry point.
        /// </summary>
        /// <param name="args"> 
        /// The command line arguments for the application.
        /// The first argument is the controller name to connect to.
        /// The second argument is the project to redistribute tests for newly added targets.
        /// </param>
        /// <exception cref="ArgumentException">Thrown if two arguments are not specified.</exception>
        static void Main(string[] args)  
        {  
            if (args.Length != 2)  
            {  
                throw new ArgumentException("args");  
            }  
  
            string serverName = args[0];  
            string runningProject = args[1];  
  
            // get a server name
            ProjectManager manager = new DatabaseProjectManager(serverName);  
            Project project = manager.GetProject(runningProject);  
  
            // just the first 50 tests.
            foreach (Test test in project.GetTests().Take(50))  
            {  
                Console.WriteLine();  
                Console.WriteLine("Distribution options for {0}:", test.Name);  
  
//                these commented out expressions are no longer valid and will not return the correct values.
//
//                bool incorrectMultiMachineTestValue = test.ScheduleOptions == DistributionOption.RequiresMultipleMachines;
//                bool incorrectNonDistributableTestValue = test.ScheduleOptions == DistributionOption.ScheduleOnAnyTarget;
//                bool incorrectDistributableTestValue = test.ScheduleOptions == DistributionOption.ScheduleOnAnyTarget;
//                bool incorrectMultiDeviceTestValue = test.ScheduleOptions == DistributionOption.ConsolidateScheduleAcrossTargets;

                // using bitwise comparison is faster, especially for large sets of tests
                bool multiMachineTest = (test.ScheduleOptions | DistributionOption.RequiresMultipleMachines) == DistributionOption.RequiresMultipleMachines;  
                bool nonDistributableTest = (test.ScheduleOptions | DistributionOption.ScheduleOnAllTargets) == DistributionOption.ScheduleOnAllTargets;  
  
                // using HasFlag is cleaner but can be slower
                bool distributableTest = test.ScheduleOptions.HasFlag(DistributionOption.ScheduleOnAnyTarget);  
                bool multiDeviceCapableTest = test.ScheduleOptions.HasFlag(DistributionOption.ConsolidateScheduleAcrossTargets);  
  
                bool manualTest = test.TestType == TestType.Manual;  
  
                // print out values for each test.    
                Console.WriteLine("Test information for {0}", test.Name);  
                Console.WriteLine(" Requires supplemental content to be downloaded and installed : {0}", test.RequiresSupplementalContent);  
                Console.WriteLine(" Configuration steps on client required before running        : {0}", test.RequiresSpecialConfiguration);  
                Console.WriteLine(" Requires manual input                                        : {0}", manualTest);  
                Console.WriteLine(" Requires multimachine configuration to run test              : {0}", multiMachineTest);  
                Console.WriteLine(" Must run on each instance of a target in a target family     : {0}", nonDistributableTest);  
                Console.WriteLine(" Can run on any instance of a target in a target family       : {0}", distributableTest);  
                Console.WriteLine(" Can run multiple tests/targets at once in one test run       : {0}", multiDeviceCapableTest);  
            }  
        }  
    }  
}  
```

## <span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>**PowerShell**


```PowerShell
Clear-Host;

$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dbconnection.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.submission.dll")

$connectFileName = $env:WTTSTDIO + "connect.xml"
Write-Host Opening connection file $connectFileName
$connectFile = [xml](Get-Content $connectFileName)

$ControllerName = $connectFile.Connection.GetAttribute("Server")
$DatabaseName = $connectFile.Connection.GetAttribute("Source")

$Manager =  new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection.DatabaseProjectManager -Args $ControllerName, $DatabaseName

#Load Project
$Project = $Manager.GetProject("Test");

foreach( $test in $Project.GetTests())
{
    $multiMachineTest = $test.ScheduleOptions.HasFlag([Microsoft.Windows.Kits.Hardware.ObjectModel.DistributionOption]::RequiresMultipleMachines);
    $nonDistributableTest = $test.ScheduleOptions.HasFlag([Microsoft.Windows.Kits.Hardware.ObjectModel.DistributionOption]::ScheduleOnAllTargets);
    $distributableTest = $test.ScheduleOptions.HasFlag([Microsoft.Windows.Kits.Hardware.ObjectModel.DistributionOption]::ScheduleOnAnyTarget);
    $multiDeviceCapableTest = $test.ScheduleOptions.HasFlag([Microsoft.Windows.Kits.Hardware.ObjectModel.DistributionOption]::ConsolidateScheduleAcrossTargets);

    $manualTest = $test.TestType -eq ([Microsoft.Windows.Kits.Hardware.ObjectModel.TestType]::Manual);

    Write-Host;
    Write-Host "Test information for $($test.Name)";
    Write-Host " Requires supplemental content to be downloaded and installed    : $($test.RequiresSupplementalContent)";
    Write-Host " Configuration steps on client required before running           : $($test.RequiresSpecialConfiguration)" ;
    Write-Host " Requires manual input                                           : $manualTest" ;
    Write-Host " Requires multimachine configuration to run test                 : $multiMachineTest";
    Write-Host " Must run on each instance of a target in a target family to pass: $nonDistributableTest";
    Write-Host " Can run on any instance of a target in a target family to pass  : $distributableTest";
    Write-Host " Can run multiple tests/targets at once in one test run          : $multiDeviceCapableTest";
}
```

 

 






