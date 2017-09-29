---
title: Mobile Reflash Before a Test Run
description: Mobile Reflash Before a Test Run
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 350AE7DA-0836-44C8-BA98-DEA1FD97F636
---

# Mobile Reflash Before a Test Run


This sample shows how to flash an OS image onto a mobile device as part of a test run.

>[!NOTE]
>  This feature is supported only on mobile devices.

 

## <span id="C_"></span><span id="c_"></span>**C#**


``` syntax
//-----------------------------------------------------------------------
// <copyright file="MobileReflashBeforeTestRun.cs" company="Microsoft">
//    Copyright (c) Microsoft Corporation. All rights reserved.
// </copyright>
//-----------------------------------------------------------------------

using System.Globalization;

[assembly: System.CLSCompliant(true)]

namespace Microsoft.Windows.Kits.Samples
{
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Xml;
    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;

    /// <summary>
    /// Sample for using a Target Family
    /// </summary>
    public static class MobileReflashBeforeTestRun
    {
        static ProjectManager ConnectToLocalServer()
        {
            // Note: Flashing an OS image during test scheduling is only supported for Mobile Devices
            // Note: And before running any tests on mobile devices, you would have to onboard the device to the controller
            XmlDocument doc = new XmlDocument();
            doc.Load(Environment.ExpandEnvironmentVariables(@"%WTTSTDIO%\\connect.xml"));
            XmlNode root = doc.SelectSingleNode("/Connection");
            string controllerName = root.Attributes["Server"].Value;
            string databaseName = root.Attributes["Source"].Value;

            DatabaseProjectManager manager = new DatabaseProjectManager(controllerName, databaseName);
            Console.WriteLine("Connected to database {0} on controller {1}", databaseName, controllerName);

            return manager;
        }

        /// <summary>
        /// main entry point
        /// </summary>
        /// <param name="args">standard parameter arguments</param>
        public static void Main(string[] args)
        {
            // first we need to connect to the Server
            ProjectManager manager = ConnectToLocalServer();

            //---------------
            // Machine and Machine pool management
            //---------------
            // now we need to create a machine pool
            const string poolName = "MobileTest";
            MachinePool rootPool = manager.GetRootMachinePool();
            MachinePool testPool = rootPool.GetChildPools().FirstOrDefault(x => x.Name == poolName) ?? rootPool.CreateChildPool(poolName);

            // Move all machines to the test pool and set them to ready state
            foreach (Machine machine in rootPool.DefaultPool.GetMachines())
            {
                // We're assuming all devices in the default pool are Mobile devices.
                rootPool.DefaultPool.MoveMachineTo(machine, testPool);
            }

            Machine testMachine = testPool.GetMachines().FirstOrDefault();
            if (testMachine == null)
            {
                throw new Exception("Could not find any machine to schedule tests.");
            }

            foreach (Machine machine in testPool.GetMachines())
            {
                machine.SetMachineStatus(MachineStatus.Ready, (long)TimeSpan.FromMinutes(1).TotalMilliseconds);
            }

            // create a device family. In production code, please check whether the device family or the hardware id exists already
            string[] hardwareIds = { @"ADCM\QCOM242E" };
            DeviceFamily deviceFamily = manager.CreateDeviceFamily(@"ADCM\QCOM242E", hardwareIds);

            // Create a test project
            Project project = manager.CreateProject(string.Format(CultureInfo.InvariantCulture, "My Device Family Project {0}", DateTime.Now));

            //---------------
            // create a product instance
            //---------------
            ProductInstance productInstance = project.CreateProductInstance("My Product instance", testPool, testMachine.OSPlatform);
            TargetFamily targetFamily = productInstance.CreateTargetFamily(deviceFamily);

            // next we enumerate all of the devices in the system that use one of the hardware IDs in the device family
            foreach (TargetData data in productInstance.FindTargetFromDeviceFamily(deviceFamily))
            {
                // check this first, to see if this can be added
                if (targetFamily.IsValidTarget(data))
                {
                    targetFamily.CreateTarget(data);
                }
            }

            string testName = "DF - Sleep with IO Before and After (Bring Up)";

            Test sampleTest = targetFamily.GetTests().FirstOrDefault(test => test.Name.Equals(testName, StringComparison.OrdinalIgnoreCase));
            if (sampleTest == null)
            {
                throw new Exception(string.Format(CultureInfo.InvariantCulture, "Failed to schedule mobile test. Could not find test '{0}'.", testName));
            }

            TemplateParameters templateParameters = sampleTest.GetDefaultTemplateParameters();

            // Flash image file should be copied to the below path
            templateParameters[TemplateParameter.ImagePath] = string.Format(CultureInfo.InvariantCulture, @"\\{0}\HLKInstall\ProxyTools\Images\flash_lab.ffu", ((DatabaseProjectManager)manager).ControllerName);
            templateParameters[TemplateParameter.ForceReflash] = "1";

            // run test after flashing a new OS image on the mobile device
            sampleTest.QueueTest(templateParameters);
        }
    }
}
        
```

## <span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>**PowerShell**


``` syntax
#Note: Flashing an OS image during test scheduling is only supported for Mobile Devices

. "$PSScriptRoot\Initialization.ps1"

$ErrorActionPreference = "Stop"

Clear-Host
$Manager = Initialize

# create the project name
$now = [System.DateTime]::Now
$ProjectName = "ProxyTest $now"

$RootPool = $Manager.GetRootMachinePool()
$DefaultPool = $RootPool.DefaultPool

# create the pool
$TestPool = $RootPool.GetChildPools() | Where {$_.Name -eq "MobileTest" }[0]
if ($TestPool -eq $null)
{
    $TestPool = $RootPool.CreateChildPool("MobileTest")
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

# Get device family
$DeviceFamily = $Manager.GetDeviceFamilies() | Where-Object {$_.Name -eq "ADCM\QCOM242E"}
$TargetFamily = $ProductInstance.CreateTargetFamily($DeviceFamily)

foreach($targetData in $ProductInstance.FindTargetFromDeviceFamily($DeviceFamily))
{
    if($TargetFamily.IsValidTarget($targetData))
    {
        $TargetInfo = $TargetFamily.CreateTarget($targetData)
        Write-Host Successfully created a target for $TargetInfo.Name
    }
}

Write-Host Total tests for target family $TargetFamily.GetTests().Count

# Find a specific test
$TestName = "DF - Sleep with IO Before and After (Bring Up)"

$Test = $TargetFamily.GetTests() | where { $_.Name -eq $TestName }

if ($Test -eq $null)
{
    Write-Host "Could not find test $TestName"
    
    Write-Host "Deleting project..."
    $Manager.DeleteProject($ProjectName)

    exit -1
}

Write-Host "Successfully found test $Test.Name"

#get Proxy template parameters
$TemplateParameters = $Test.GetDefaultTemplateParameters()

#set Proxy template parameters
$ControllerName = $Manager.ControllerName
$TemplateParameters["ImagePath"] = "\\$ControllerName\HLKInstall\ProxyTools\Images\flash_lab.ffu"
$TemplateParameters["ForceReflash"] = "1"

#run test on mobile device
$Test.QueueTest($TemplateParameters)        
        
```

 

 






