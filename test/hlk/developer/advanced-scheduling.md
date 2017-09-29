---
title: Advanced scheduling
description: Advanced scheduling
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 71955C64-0D02-4D42-B90B-A75184EE7AAE
---

# Advanced scheduling


These samples demonstrate various scheduling scenarios.

## <span id="C_"></span><span id="c_"></span>**C#**


``` syntax
//-----------------------------------------------------------------------
// <copyright file="AdvancedScheduling.cs" company="Microsoft">
//    Copyright (c) Microsoft Corporation. All rights reserved.
// </copyright>
//-----------------------------------------------------------------------

[assembly: System.CLSCompliant(true)]
namespace Microsoft.Windows.Kits.Samples
{
    using System.Linq;
    using System.Threading;
    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;

    public class AdvancedScheduling
    {
        private AdvancedScheduling()
        {
        }

        public static void Main(string[] args)
        {
            string projectName = "my new project";
            string controllerName = args[1];

            // first we need to connect to the Server
            ProjectManager manager = new DatabaseProjectManager(controllerName);

            // next we need to load our project
            Project project = manager.GetProject(projectName);

            // this will schedule any jobs which have already run, and have failed
            foreach (Test test in project.GetTests().Where(x => x.Status == TestResultStatus.Failed))
            {
                test.QueueTest();
            }

            // wait some time
            Thread.Sleep(5 * 60 * 1000 /* 5 minutes */);

            // cancel all test which have not started yet
            foreach (Test test in project.GetTests().Where(x => x.Status == TestResultStatus.InQueue))
            {
                // tests are definitions, each instance of the QueueTests creates a result.
                // so to cancel a test, you need to cancel it's instance, aka the result
                foreach (TestResult result in test.GetTestResults().Where(x => x.Status == TestResultStatus.InQueue))
                {
                    result.Cancel();
                }
            }
        }
    }
}
```

## <span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>**PowerShell**


``` syntax
. ..\Initialization.ps1

Clear-Host
$Manager = Initialize

# create the project name
$now = [System.DateTime]::Now
$ProjectName = "My new Advanced scheduling project $now" 


$RootPool = $Manager.GetRootMachinePool()
$DefaultPool = $RootPool.DefaultPool

# create the pool
$TestPool = $RootPool.GetChildPools() | Where {$_.Name -eq "TestPool" }[0]
if ($TestPool -eq $null)
{
    $TestPool = $RootPool.CreateChildPool("TestPool")
}

# move all machines in the default pool
$DefaultPool.GetMachines() | foreach {
    write-host $_.Name
    $DefaultPool.MoveMachineTo($_, $TestPool)
    }

#reset all machines
$TestPool.GetMachines() | foreach { $_.SetMachineStatus([Microsoft.Windows.Kits.Hardware.ObjectModel.MachineStatus]::Ready, 1) }

#-----------
# Creating a project
#-----------
$Project = $manager.CreateProject($ProjectName)
Write-Host "created a project named : "$Project.Name

$OSPlatform = $TestPool.GetMachines()[0].OSPlatform
$ProductInstance = $Project.CreateProductInstance("My Product Instance",
                                                 $TestPool,
                                                 $OSPlatform)

# this will find all systems in the test pool, and return those as a list of system test targets
$data = $ProductInstance.FindTargetFromSystem()


# for now, just use the first one found
Write-Host "Createing a target for " $data[0].Name
$Target = $ProductInstance.CreateTarget($data[0])
write-Host Successfully created a Target for $Target.Name that has $Target.GetTests().Count tests


# Find a specific test
#
# this test is named 
$TestName = "Debug Capability Test (Logo)"

$Test = $Target.GetTests() | where { $_.Name -eq $TestName }[0]

Write-Host "Verifying $($Test.Name) requires multiple machines: " $Test.ScheduleOptions.HasFlag( [Microsoft.Windows.Kits.Hardware.ObjectModel.DistributionOption]::RequiresMultipleMachines );

# List the parameters for this test
$Test.GetParameters().Values | foreach {
    Write-Host 
    Write-Host Name         : $_.Name
    Write-Host Description  : $_.Description
    Write-Host Visible      : $_.Visible
    Write-Host DefaultValue : $_.DefaultValue
    Write-Host ActualValue  : $_.ActualValue
    }

# for purposes of demonstration, this job has a parameter to indicate which debug transport (bus) to use
# set this to USB

$Test.SetParameter("Transport", "usb", [Microsoft.Windows.Kits.Hardware.ObjectModel.ParameterSetAsDefault]::DoNotSetAsDefault)
$Test.SetParameter("UsbTargetName", "someDevice", [Microsoft.Windows.Kits.Hardware.ObjectModel.ParameterSetAsDefault]::DoNotSetAsDefault)

Write-Host Displaying paramters again, to show that theyve been set
$Test.GetParameters().Values | foreach {
    Write-Host 
    Write-Host Name         : $_.Name
    Write-Host Description  : $_.Description
    Write-Host Visible      : $_.Visible
    Write-Host DefaultValue : $_.DefaultValue
    Write-Host ActualValue  : $_.ActualValue
    }

# to run this test, we'd be expected to set this up against 2 machines, 
# so new need to find another machine to use
$SecondMachine =  $TestPool.GetMachines() | Where { $_ -ne $Target.Machine }

$MachineSet = $Test.GetMachineRole();

#write each of these roles to the console
$MachineSet.Roles | foreach { 
    $_ 
    Write-Host Machines currently in this role:  $_.GetMachines().Count
    Write-Host
    }

# I know that the primary role is already filled by the machine under test.
# and that adding a machine to that role will result in a failure

Write-Host this should return a failure
$MachineSet.Roles[0].AddMachine($SecondMachine)

# however adding this machine to a secondary role should succeed
Write-Host this should Succeed
$MachineSet.Roles[1].AddMachine($SecondMachine)

# Now that the machine set has been created, 
# we can schedule this test
$test.QueueTest($MachineSet);
```

 

 






