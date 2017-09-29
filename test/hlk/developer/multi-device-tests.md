---
title: Multi-Device Tests
description: Multi-Device Tests
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 235abea3-3345-439d-8992-0cd684863aaf
---

# Multi-Device Tests


This sample code show illustrates running multi-device tests.

>[!NOTE]
>  
The method returns the base target for multi-device tests (that is the base test device into which additional tests were consolidated). The TestResults.GetAllTests() method should return the list of tests that were actually run together; from that list, you can derive the actual targets against which the test ran.

 

## <span id="C_"></span><span id="c_"></span>**C#**


``` syntax
// ------------------------------------------------------------------------------------------------
// <copyright file="MultiDeviceScheduling.cs" company="Microsoft">
//   Copyright (c) Microsoft Corporation. All rights reserved.
// </copyright>
// ------------------------------------------------------------------------------------------------
[assembly: System.CLSCompliant(true)]

namespace Microsoft.Windows.Kits.Samples.MultiDevice
{
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using System.Linq;

    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;

    /// <summary>
    /// Sample code for running multi-device tests
    /// </summary>
    public static class MultiDeviceScheduling
    {
        /// <summary>
        /// Entry point method for the sample application
        /// </summary>
        /// <param name="args">standard parameter arguments</param>
        public static void Main(string[] args)
        {
            string controllerName;
            string projectName;

            if (args.Length == 2)
            {
                controllerName = args[0];
                projectName = args[1];
            }
            else
            {
                Console.WriteLine("Usage:\tScheduleTestsByContentLevel.exe [ControllerMachineName] [ProjectName]");
                return;
            }

            // get all content levels
            ContentLevelType[] levels = (ContentLevelType[])Enum.GetValues(typeof(ContentLevelType));

            // first we need to connect to the Server
            ProjectManager manager = new DatabaseProjectManager(controllerName);

            // load the project
            Project project = manager.GetProject(projectName);

            // get tests that can be run without user intervention
            List<Test> tests = project.GetTests(levels).Where(test => test.ScheduleOptions.HasFlag(DistributionOption.RequiresMultipleMachines) && !test.RequiresSupplementalContent && !test.RequiresSpecialConfiguration && test.TestType == TestType.Automated).ToList();

            // get current count of tests
            int originalTestCount = tests.Count;

            // create scheduling groups
            List<List<Test>> testGroups = Test.FilterMultiDeviceTestGroups(tests);

            // after call, tests that cannot be consolidated are removed from the list.
            int removedTests = tests.Count - originalTestCount;

            // if the count of tests removed from the list is zero, there were no multidevice tests in the list.
            if (removedTests == 0)
            {
                Console.WriteLine("No tests were found that could be consolidated.");
                MultiDeviceScheduling.PrintNoMultiDeviceReasonsMessage();
                return;
            }

            if (testGroups.All(testGroup => 0 == testGroup.Count))
            {
                Console.WriteLine("Multidevice tests were found, but no tests could be consolidated.");
                MultiDeviceScheduling.PrintNoMultiDeviceReasonsMessage();
                return;
            }

            // otherwise start scheduling multidevice tests with consolidation where possible.
            Console.WriteLine("{0} MultiDevice tests will be consolidated into {1} tests runs.", removedTests, testGroups.Count);

            List<TestResult> multiDeviceResults = new List<TestResult>();
            // schedule multidevice tests (if any)
            foreach (List<Test> testGroup in testGroups)
            {
                Console.WriteLine("Consolidating {0} instances of test {1} with the following devices:", testGroup.Count, testGroup[0].Name);
                testGroup.ForEach(testGroupItem => Console.WriteLine(testGroupItem.GetTestTargets()[0].TargetFamily.Family.Name));

                multiDeviceResults.AddRange(testGroup[0].QueueTest(testGroup.GetRange(1, testGroup.Count - 1)));
            }

            // schedule the rest of the tests
            foreach (Test test in tests)
            {
                test.QueueTest();
            }

            // performance optimization
            Console.WriteLine("The following tests were scheduled to test multiple devices as one test instance as a performance optimization");
            foreach (TestResult multiDeviceResult in multiDeviceResults)
            {
                if (multiDeviceResult.IsMultiDevice)
                {
                    Console.WriteLine( "The following instances of the test '{0}' were consolidated into one scheduling unit:", multiDeviceResult.Test.Name);

                    foreach (Test test in multiDeviceResult.GetAllTests())
                    {
                        Console.WriteLine("  Instance {0} for target family {0}", test.InstanceId, test.GetTestTargets()[0].TargetFamily.Family.Name);
                    }
                }
            }
        }

        /// <summary>
        /// Print error messages with possible reasons why tests could not be consolidated
        /// </summary>
        private static void PrintNoMultiDeviceReasonsMessage()
        {
            Console.WriteLine("Please verify that:");
            Console.WriteLine(" 1. The submission is a device or driver submission and contains two different target families on the same machine");
            Console.WriteLine(" 2. Both targets run the same multidevice test in the submission (e.g. Test.ScheduleOptions == DistributionOption.ConsolidateScheduleAcrossTargets");
            Console.WriteLine(" 3. Machines that contain both targets are in the ready state");
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

$TestResultList = New-Object -TypeName  System.Collections.Generic.List``1[Microsoft.Windows.Kits.Hardware.ObjectModel.TestResult];


#Load Project
$Project = $Manager.GetProject("Test");

#Get tests
$tests = $Project.GetTests()| where { $_.ScheduleOptions.HasFlag([Microsoft.Windows.Kits.Hardware.ObjectModel.DistributionOption]::ScheduleOnAnyTarget)};

#Get test count
$originalTestCount = $tests.Count;

#Create scheduling groups$test
$testGroups = [Microsoft.Windows.Kits.Hardware.ObjectModel.Test]::FilterMultiDeviceTestGroups($tests);

# get number of tests run will be consolidated into
$consolidatedCount = $testGroups.Count;

Write-Output "MultiDevice tests will be consolidated into $consolidatedCount test runs."

foreach( $testGroup in $testGroups )
{
    $baseTest = [Microsoft.Windows.Kits.Hardware.ObjectModel.Test]$testGroup[0];
    $TestResultList.AddRange($baseTest.QueueTest( $testGroup.GetRange(1, $testGroup.Count - 1 )));
}

Write-Output "The following tests were scheduled using Multi-device scheduling optimizations"

foreach( $testResult in $TestResultList)
{
    $testName = $testResult.Test.Name;

    # not all tests get may get consolidated if additional tests/targets to run with are not available at the time tests are scheduled.  
    if( $testResult.IsMultiDevice )
    {
        Write-Output ""
        Write-Output "Multiple instances for $testName were consolidated into a single run as a performance optimization";

        # get all tests in the list if it&#39;s a multidevice test
        $consolidatedTests = $testResult.GetAllTests();

        # dump information about how the result was scheduled.
        foreach($consolidatedTest in $consolidatedTests)
        {
            # print which instance of the test was scheduled and what targets are running together in a single instance.
            $testInstance = $consolidatedTest.InstanceId;
            $targetFamily = $consolidatedTest.GetTestTargets()[0].TargetFamily.Family.Name;
            Write-Output "Instance $testInstance for target $targetFamily";
        }
    }
    else
    {
        $testName = $testResult.Test.Name;
        $targetFamily = $consolidatedTest.GetTestTargets()[0].TargetFamily.Family.Name;
        Write-Output "Test $testName testing device $targetFamily was scheduled singly"
    }
}
```

 

 






