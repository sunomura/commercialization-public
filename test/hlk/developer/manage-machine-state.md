---
title: Manage Machine State
description: Manage Machine State
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a2750940-fc66-4469-a376-e5bef3800efb
---

# Manage Machine State


The following code sample shows how to manage machine stated.

## <span id="C_"></span><span id="c_"></span>C#


``` syntax
// ------------------------------------------------------------------------------------------------
// <copyright file="MachineStateManagement.cs" company="Microsoft">
//   Copyright (c) Microsoft Corporation. All rights reserved.
// </copyright>
// ------------------------------------------------------------------------------------------------

//[assembly: System.CLSCompliant(true)]

namespace Microsoft.Windows.Kits.Samples
{
    using System;

    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;

    /// <summary>
    /// Sample code for getting test roll-up by content level
    /// </summary>
    public class MachineStateManagement
    {
        /// <summary>
        /// Prevents a default instance of the <see cref="MachineStateManagement"/> class from being created.
        /// </summary>
        private MachineStateManagement()
        {
        }

        /// <summary>
        /// Entry point method for the machine state management sample application
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
                Console.WriteLine("Usage:\tMachineStateManagement.exe [ControllerMachineName] [ProjectName]");
                return;
            }

            // first we need to connect to the controller
            ProjectManager manager = new DatabaseProjectManager(controllerName);

            // let's first get the root machine pool; root pool is represented as '$'
            MachinePool rootMachinePool = manager.GetRootMachinePool();

            // now let's get child pools for the root pool; root pool will also contain 'Default Pool'
            // Note: By default, new client machines are added to the 'Default Pool'; For running tests, we have to create a new machine pool (say, TestPool) and move client machines from 'Default Pool' to 'TestPool'
            foreach (MachinePool machinePool in rootMachinePool.GetChildPools())
            {
                if (machinePool.Equals(machinePool.DefaultPool))
                {
                    // Skip - can't change status of a machine in the 'Default Pool' or root pool ('$').
                    // Note: To skip any machine operations for root pool, when you're not sure whether the current machine pools is a root pool or not, then you can do an additional check for:  machinePool.Equals(machinePool.RootPool) 
                    continue;
                }

                foreach (Machine machine in machinePool.GetMachines())
                {
                    if (machine.Status == MachineStatus.NotReady)
                    {
                        // timeout is set to 30 seconds
                        Console.WriteLine("Changing machine '{0}' status to 'Ready'", machine.Name);
                        if (machine.SetMachineStatus(MachineStatus.Ready, 30000))
                        {
                            Console.WriteLine("Machine '{0}' was successfully set to Ready state", machine.Name);
                        }
                    }
                }
            }


            // If you're only interested in the machine pool for a specific project, you can also do this:
            // load the project
            Project project = manager.GetProject(projectName);

            // enumerate the machine pools in the product instances for the current project
            foreach (ProductInstance productInstance in project.GetProductInstances())
            {
                MachinePool machinePool = productInstance.MachinePool;

                if (machinePool == null || 
                    machinePool.Equals(machinePool.RootPool) ||
                    machinePool.Equals(machinePool.DefaultPool))
                {
                    // Skip - can't change status of a machine in the 'Default Pool' or root pool ('$')
                    continue;
                }

                // this code snippet is same as in the above example. It's added here again for clarity
                foreach (Machine machine in machinePool.GetMachines())
                {
                    if (machine.Status == MachineStatus.NotReady)
                    {
                        // timeout is set to 30 seconds
                        Console.WriteLine("Changing machine '{0}' status to 'Ready'", machine.Name);
                        if (machine.SetMachineStatus(MachineStatus.Ready, 30000))
                        {
                            Console.WriteLine("Machine '{0}' was successfully set to Ready state", machine.Name);
                        }
                    }
                }
            }
        }
    }
}
```

## <span id="Windows_PowerShell_"></span><span id="windows_powershell_"></span><span id="WINDOWS_POWERSHELL_"></span>Windows PowerShell®


``` syntax
. ..\Initialization.ps1

Clear-Host
$Manager = Initialize

#let's first get the root machine pool; root pool is represented as '$'
$rootMachinePool = $Manager.GetRootMachinePool()

$ReadyStatus = [Microsoft.Windows.Kits.Hardware.ObjectModel.MachineStatus]::Ready
$NotReadyStatus = [Microsoft.Windows.Kits.Hardware.ObjectModel.MachineStatus]::NotReady

#now let's get child pools for the root pool; root pool will also contain 'Default Pool'
#Note: By default, new client machines are added to the 'Default Pool'; For running tests, we have to create a new machine pool (say, TestPool) and move client machines from 'Default Pool' to 'TestPool'
foreach ($machinePool in $rootMachinePool.GetChildPools())
{
if ($machinePool.Equals($machinePool.DefaultPool))
{
# Skip - can't change status of a machine in the 'Default Pool' or root pool ('$').
# Note: To skip any machine operations for root pool, when you're not sure whether the current machine pools is a root pool or not, then you can do an additional check for:  $machinePool.Equals($machinePool.RootPool) 
continue;
}

foreach ($machine in $machinePool.GetMachines())
{
if ($machine.Status -eq $NotReadyStatus)
{
#timeout is set to 30 seconds
Write-Host ("Changing machine '{0}' status to 'Ready'" -f $machine.Name)
if($machine.SetMachineStatus($ReadyStatus, 30000))
{
Write-Host ("Machine '{0}' was successfully set to Ready state" -f $machine.Name)
}
}
}
}

#If you're only interested in the machine pool for a specific project, you can also do this:
#load Project
$Project = $Manager.GetProject("TestProject")

#enumerate the machine pools in the product instances for the current project
foreach ($productInstance in $Project.GetProductInstances())
{
$machinePool = $productInstance.MachinePool

if (($machinePool -eq $null) -or
$machinePool.Equals($machinePool.RootPool) -or
$machinePool.Equals($machinePool.DefaultPool))
{
#Skip - can't change status of a machine in the 'Default Pool' or root pool ('$')
continue;
}

#this code snippet is same as in the above example. It's added here again for clarity
foreach ($machine in $machinePool.GetMachines())
{
if ($machine.Status -eq $NotReadyStatus)
{
#timeout is set to 30 seconds
Write-Host ("Changing machine '{0}' status to 'Ready'" -f $machine.Name)
if($machine.SetMachineStatus($ReadyStatus, 30000))
{
Write-Host ("Machine '{0}' was successfully set to Ready state" -f $machine.Name)
}
}
}
}
```

 

 






