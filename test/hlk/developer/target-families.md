---
title: Target Families
description: Target Families
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6888f5cc-b3be-4e48-9c7d-5303aefd7db9
---

# Target Families


These samples show how to create target families and run tests against them.

## <span id="C_"></span><span id="c_"></span>C#


``` syntax
//-----------------------------------------------------------------------
// <copyright file="AdvancedTargetFamily.cs" company="Microsoft">
//    Copyright © Microsoft Corporation. All rights reserved.
// </copyright>
//-----------------------------------------------------------------------

namespace Samples
{
    using System.Collections.Generic;
    using System.Linq;
    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;

    public class AdvancedTargetFamily
    {
        public static void Main(string[] args)
        {
            string projectName = "my new project";
            string controllerName = args[1];

            // first, connect to the server
            ProjectManager manager = new DatabaseProjectManager(controllerName);

            //---------------
            // machine and machine pool management
            //---------------
            // now, create a machine pool
            MachinePool rootPool = manager.GetRootMachinePool();
            MachinePool testPool = manager.GetRootMachinePool().CreateChildPool("TestPool");

            // find all the computers in the default pool, and move them into the test pool
            foreach (Machine machine in rootPool.DefaultPool.GetMachines())
            {
                rootPool.DefaultPool.MoveMachineTo(machine, testPool);
            }

            // now, make sure that the computers are in a ready state
            foreach (Machine machine in testPool.GetMachines())
            {
                machine.SetMachineStatus(MachineStatus.Ready, -1);
            }

            // create a device family
            string[] HardwareIds = { @"HID\VID_045E&PID_006A&REV_1717&Col01", @"HID\VID_045E&PID_006A&Col01", @"HID_DEVICE_SYSTEM_MOUSE" };
            DeviceFamily mouseDeviceFamily = manager.CreateDeviceFamily("My Device Family", HardwareIds);

            //---------------
            // creating a project
            //---------------
            Project project = manager.CreateProject(projectName);

            // now you have a group of computers in your test pool
            // you must figure out what distinct list of OSPlatfoms are in there
            HashSet<OSPlatform> platformList = new HashSet<OSPlatform>();
            foreach (Machine machine in testPool.GetMachines())
            {
                if (platformList.Contains(machine.OSPlatform) == false)
                {
                    platformList.Add(machine.OSPlatform);
                }
            }

            //---------------
            // creating a product instance, one for each OSType
            //---------------
            foreach (OSPlatform platform in platformList)
            {
                ProductInstance pi = project.CreateProductInstance("Product instance for " + platform.Description, testPool, platform);
                TargetFamily targetFamily = pi.CreateTargetFamily(mouseDeviceFamily);
                
                // next, enumerate all the devices in the system that use one of the hardware IDs in the device family
                foreach (TargetData data in pi.FindTargetFromDeviceFamily(mouseDeviceFamily))
                {
                    // check this first, to see if this can be added
                    if (targetFamily.IsValidTarget(data))
                    {
                        targetFamily.CreateTarget(data);
                    }
                }

                // start running these tests now
                pi.QueueTest();
            }

            //-----------------
            // some time passes, and no more computers are available to run these tests
            // so now you must add more computers to the pool
            //-----------------
            foreach (Machine machine in testPool.DefaultPool.GetMachines())
            {
                // filter out any computer where the OSPlatform is not already part of the project
                if (platformList.Contains(machine.OSPlatform))
                {
                    rootPool.DefaultPool.MoveMachineTo(machine, testPool);
                    machine.SetMachineStatus(MachineStatus.Ready, -1);

                    // get the target family again
                    ProductInstance pi = project.GetProductInstances().Where(x => x.OSPlatform == machine.OSPlatform).First();
                    TargetFamily targetFamily = pi.GetTargetFamilies().Where(x => x.Family == mouseDeviceFamily).First();

                    foreach (TargetData data in pi.FindTargetFromDeviceFamily(mouseDeviceFamily))
                    {
                        if (targetFamily.IsValidTarget(data))
                        {
                            targetFamily.CreateTarget(data);
                        }
                    }
                }
            }

            // now, reschedule any job that hasn't run yet
            foreach (Test test in project.GetTests().Where(x => (x.Status == TestResultStatus.InQueue) || (x.Status == TestResultStatus.NotRun)))
            {
                foreach (TestResult result in test.GetTestResults().Where(x => x.Status == TestResultStatus.InQueue))
                {
                    result.Cancel();
                }

                // this will reschedule the tests on the new hardware/targets, as needed
                test.QueueTest();
            }
        }
    }
}
```

## <span id="Windows_PowerShell_"></span><span id="windows_powershell_"></span><span id="WINDOWS_POWERSHELL_"></span>Windows PowerShell®


``` syntax
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "microsoft.windows.Kits.Hardware.objectmodel.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "microsoft.windows.Kits.Hardware.objectmodel.dbconnection.dll")

Clear-Host

write-Host "Usage: %SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe -file TargetFamily.ps1 <<ControllerMachineName>> "

$ControllerName = $args[0]
if ($ControllerName -eq $null -OR $ControllerName -eq "")
{
    write-host "Need to supply the controller Name as a parameter to this script"
    return
}
else
{
    write-host connecting to the controller $ControllerName
}


# connect to the controller
$Manager = new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection.DatabaseProjectManager -Args $ControllerName, HLKJobs


$RootPool = $Manager.GetRootMachinePool()
$DefaultPool = $RootPool.DefaultPool

# create the pool
$TestPool = $RootPool.CreateChildPool("TestPool")

# find all the computers in the default pool, and move them into the test pool
$DefaultPool.GetMachines() | foreach {
    write-host $_.Name
    $DefaultPool.MoveMachineTo($_, $TestPool)
    }

# now, make sure that the computers are in a ready state
$TestPool.GetMachines() | foreach { $_.SetMachineStatus([Microsoft.Windows.Kits.Hardware.ObjectModel.MachineStatus]::Ready, 1) }

# create a device family
[string[]]$HardwareIds = "HID\VID_045E&PID_006A&REV_1717&Col01", "HID\VID_045E&PID_006A&Col01", "HID_DEVICE_SYSTEM_MOUSE"
$DeviceFamily = $Manager.CreateDeviceFamily("My Device Family", $HardwareIds)

# create a project
$Project = $Manager.CreateProject("My Device Family Project {0}" -f [DateTime]::Now.ToString())

# create a product instance by using the operating system platform of the first computer that you find
$ProductInstance = $Project.CreateProductInstance("My Product Instance", $TestPool, $TestPool.GetMachines()[0].OSPlatform)

# create a target family by using the device family that you created earlier
$TargetFamily = $ProductInstance.CreateTargetFamily($DeviceFamily)

#find all the devices in this machine pool that are in this device family
$ProductInstance.FindTargetFromDeviceFamily($DeviceFamily) | foreach {
    "attempting to add target $_.Name on machine $_.Machine.Name to TargetFamily"
# and add those to the target family
    
# check this first, to make sure that this can be added to the target family
    if ($TargetFamily.IsValidTarget($_)) {
        $TargetFamily.CreateTarget($_)
        }
    }

#schedule all tests
$Project.GetTests() | foreach {
    "test {0} is {1}" -f  $_.Name, $_.ScheduleOptions.ToString()
    Write-Host "running test {0} " -f $_.Name
    $_.QueueTest();        
    }
```

 

 






