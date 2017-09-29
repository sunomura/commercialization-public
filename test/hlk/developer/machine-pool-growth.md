---
title: Machine Pool Growth
description: Machine Pool Growth
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d02b214d-e656-49c2-8373-f2c687b2def6
---

# Machine Pool Growth


This sample uses the Machine Pool Growth feature to add and automatically redistribute tests to targets after a test has been scheduled.

Before running this sample, you must do the following:

1.  Set up two systems running the same CPU family and operating system with the same target or sets of targets on both (e.g. same Hardware IDs).

2.  Create a project on one system, add the target(s) and queue up lots of tests.

3.  Move the second to the same machine pool (using HLK Studio or programmatically) as the first system and run the sample.

## <span id="C_"></span><span id="c_"></span>**C#**


``` syntax
//-----------------------------------------------------------------------
// <copyright file="MachinePoolGrowthSample.cs" company="Microsoft">
//    Copyright (c) Microsoft Corporation. All rights reserved.
// </copyright>
//-----------------------------------------------------------------------
[assembly: System.CLSCompliant(true)]

namespace Microsoft.Windows.Kits.Samples
{
    using System;
    using System.Collections.Generic;
    using System.Linq;

    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;

    /// <summary>
    /// This sample for using the Machine Pool Growth feature to add and automatically redistribute tests to targets after 
    /// a test has been scheduled. 
    /// 
    /// Before running this sample, 
    /// 1. Set up two systems running the same CPU family and operating system with the same target or sets of targets on both (e.g. same Hardware Ids).
    /// 2. Create a project on one system, add the target(s) and queue up lots of tests.
    /// 3. Move the second to the same machine pool (using HLK Studio or programmatically) as the first system and run the sample.
    /// </summary>
    class MachinePoolGrowthSample
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
            Project project = manager.GetProject( runningProject );

            List<Target> addedTargets = new List<Target>();

            // walk through each product instance...
            foreach (ProductInstance instance in project.GetProductInstances())
            {
                // get any matching targets from machines in the same pool that are not a part of the current target set
                Console.WriteLine("Looking for any targets in Machine Pool {0}{1} that contain similar targets", instance.MachinePool.Path, instance.MachinePool.Name);

                // loop through product instance's target family
                foreach (TargetFamily targetFamily in instance.GetTargetFamilies())
                {
                    // loop through any targets compatible with the current target family
                    foreach( TargetData targetData in instance.FindTargetFromDeviceFamily(targetFamily.Family) )
                    {
                        if (targetFamily.IsValidTarget(targetData))
                        {
                            // create target and add it to the added target set if we can.
                            addedTargets.Add(targetFamily.CreateTarget(targetData));
                        }
                    }
                }
            }

            // nothing to do if there are no targets compatible with the specified project that have not already been added.
            if (addedTargets.Count == 0)
            {
                Console.WriteLine("No targets were added to the project, no tests to redistribute.");
                return;
            }

            IList<TestResult> cancelFailedResults;
            IList<TestResult> cancelledResults;
            IList<TestResult> reScheduledResults;
            IList<Test> rescheduleFailedTests;

            // do test redistribution across newly added targets
            Target.RedistributeScheduledTests(addedTargets, out cancelFailedResults, out cancelledResults, out reScheduledResults, out rescheduleFailedTests);

            // print out results that were successfully rescheduled.
            if (reScheduledResults.Count > 0)
            {
                Console.WriteLine("Test results which were successfully rescheduled:");
                foreach (TestResult result in reScheduledResults)
                {
                    LogTestResultData(result);
                }
            }

            // print out tests that could not be successfully rescheduled.
            if (rescheduleFailedTests.Count > 0)
            {
                Console.WriteLine("The following tests could not be rescheduled:");
                foreach (Test test in rescheduleFailedTests)
                {
                    Console.WriteLine("Test '{0}' for device {1}'", test.Name, test.GetTestTargets()[0].TargetFamily.Family.Name);
                }
            }

            // print out tests that could not be cancelled, if any
            if (cancelFailedResults.Count > 0)
            {
                Console.WriteLine("Test results which could not be cancelled:");
                foreach (TestResult result in cancelFailedResults)
                {
                    LogTestResultData(result);
                }
            }

            // print out results that were successfuly cancelled.
            if (cancelledResults.Count > 0)
            {
                Console.WriteLine("Test results which weres successfully cancelled:");
                foreach (TestResult result in cancelledResults)
                {
                    LogTestResultData(result);
                }
            }
        }

        /// <summary>
        /// Dump out information about the result that was cancelled/rescheduled/failed to reschedule.
        /// </summary>
        /// <param name="result">The result object to dump name/info for.</param>
        static void LogTestResultData(TestResult result)
        {
            List<Test> tests = new List<Test>();

            // Note: Calling IsMultiDevice and GetAllTests on results that have not run or are not capable of running in MultiDevice mode
            //       will work, but checking if the test is capable of running in MultiDevice mode can make the code run a bit quicker.
            if (result.Test.ScheduleOptions.HasFlag(DistributionOption.ConsolidateScheduleAcrossTargets) && result.IsMultiDevice)
            {
                Console.WriteLine("Test {0} for multiple targets running as a Multi-Device test:", result.Test.Name);

                // Get all targets for all tests that were rolled up into the result for MultiDevice tests
                foreach (Test test in result.GetAllTests())
                {
                    Console.WriteLine("  {0}", test.GetTestTargets()[0].TargetFamily.Family.Name);
                }
            }
            else
            {
                // For non-multidevice results, there will always be only one test associated with the results and can result.Test.
                Console.WriteLine("Test {0} for target {1}", result.Test.Name, result.Test.GetTestTargets()[0].TargetFamily.Family.Name);
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


# Dump out information about a test result
Function LogTestResultData( $testResult )
{
    if( ( ($testResult.Test.ScheduleOptions -band [Microsoft.Windows.Kits.Hardware.ObjectModel.DistributionOption]::ConsolidateScheduleAcrossTargets ) -eq [Microsoft.Windows.Kits.Hardware.ObjectModel.DistributionOption]::ConsolidateScheduleAcrossTargets ) -and $testResult.IsMultiDevice )
    {
        Write-Host "Test $($testResult.Test.Name) for multiple targets running as a Multi-Device test";

        foreach( $test in $testResult.GetAllTests() )
        {
            Write-Host "  $($test.GetTestTargets()[0].TargetFamily.Family.Name)";
        }
    }
    else
    {
        Write-Host "Test $($testResult.Test.Name) for target $($testResult.Test.GetTestTargets()[0].TargetFamily.Family.Name)";
    }
}

$connectFileName = $env:WTTSTDIO + "connect.xml"
Write-Host Opening connection file $connectFileName
$connectFile = [xml](Get-Content $connectFileName)

$ControllerName = $connectFile.Connection.GetAttribute("Server")
$DatabaseName = $connectFile.Connection.GetAttribute("Source")


$Manager =  new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection.DatabaseProjectManager -Args $ControllerName, $DatabaseName

$addedTargetList = New-Object -TypeName  System.Collections.Generic.List``1[Microsoft.Windows.Kits.Hardware.ObjectModel.Target];


#Load Project
$Project = $Manager.GetProject("Test");

foreach($productInstance in $Project.GetProductInstances())
{
    $currentPool = $productInstance.MachinePool;
    Write-Host "Looking for any targets in $($currentPool.Path)$($CurrentPool.Name) that are compatible with the current project"

    foreach ($targetFamily in $productInstance.GetTargetFamilies())
    {
        foreach($targetData in  $productInstance.FindTargetFromDeviceFamily($targetFamily.Family))
        {
            if($targetFamily.IsValidTarget($targetData))
            {
                $addedTargetList.Add($targetFamily.CreateTarget($targetData));
            }
        }
    }
}

# no targets to expand project to -- nothing to do
if($addedTargetList.Count -eq 0 )
{
    Write-Host "No compatible targets were found, returning";
    return;
}

foreach($addedTarget in $addedTargetList)
{
    Write-Host "Added target $($addedTarget.Name) on machine $($addedTarget.Machine.Name)"
}

$cancelFailedResults= New-Object -TypeName  System.Collections.Generic.List``1[Microsoft.Windows.Kits.Hardware.ObjectModel.TestResult];
$cancelledResults= New-Object -TypeName  System.Collections.Generic.List``1[Microsoft.Windows.Kits.Hardware.ObjectModel.TestResult];
$rescheduledResults= New-Object -TypeName  System.Collections.Generic.List``1[Microsoft.Windows.Kits.Hardware.ObjectModel.TestResult];
$rescheduleFailedTests= New-Object -TypeName  System.Collections.Generic.List``1[Microsoft.Windows.Kits.Hardware.ObjectModel.Test];

[Microsoft.Windows.Kits.Hardware.ObjectModel.Target]::RedistributeScheduledTests($addedTargetList, [ref]$cancelFailedResults, [ref]$cancelledResults, [ref]$reScheduledResults, [ref]$rescheduleFailedTests);

# display test results which were rescheduled using machine pool growth
if($rescheduledResults.Count -gt 0 )
{
    Write-Host
    Write-Host "Test results which were successfully rescheduled:";

    foreach($rescheduledResult in $rescheduledResults)
    {
        LogTestResultData( $rescheduledResult );
    }
}

# display tests that could not be rescheduled
if( $rescheduleFailedTests.Count -gt 0 )
{
    Write-Host
    Write-Host "The following tests could not be rescheduled:";

    foreach( $test in $rescheduleFailedTests )
    {
        Write-Host "Test $($test.Name) for device $($test.GetTestTargets()[0].TargetFamily.Family)";
    }
}

# display tests that were successfully cancelled after it was rescheduled
if($cancelledResults.Count -gt 0 )
{
    Write-Host
    Write-Host "Test results which were successfully cancelled";

    foreach($cancelledResult in $cancelledResults)
    {
        LogTestResultData( $cancelledResult );
    }
}

# display tests that could not be cancelled after it was rescheduled 
if($cancelFailedResults.Count -gt 0 )
{
    Write-Host
    Write-Host "Test results which could not be cancelled:";

    foreach($cancelFailedResult in $cancelFailedResults)
    {
        LogTestResultData( $cancelFailedResult );
    }
}
```

 

 






