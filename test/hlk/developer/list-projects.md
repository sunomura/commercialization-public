---
title: List Projects
description: List Projects
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9e633249-4e36-4d17-aa28-1274d1298cca
---

# List Projects


These samples list all projects in a controller and print basic information about each project.

## <span id="C_"></span><span id="c_"></span>**C#**


```CSharp
//-----------------------------------------------------------------------
// <copyright file="ListProjects.cs" company="Microsoft">
//    Copyright (c) Microsoft Corporation. All rights reserved.
// </copyright>
//-----------------------------------------------------------------------

namespace Samples
{
    using System;
    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;

    class ListProjects
    {
        public static void Main(string[] args)
        {
            string controllerName = args[1];

            // first, connect to the server
            ProjectManager manager = new DatabaseProjectManager(controllerName);

            // list all projects
            Console.WriteLine("Listing all projects");
            foreach (string name in manager.GetProjectNames())
            {
                Console.WriteLine("Project {0}", name);
            }
            
            // list all projects, and get the basic status of each
            Console.WriteLine("\nGetting all project status");
            foreach (ProjectInfo info in manager.GetProjectInfoList())
            {
                Console.WriteLine("Project {0}", info.Name);
                Console.WriteLine("\t status : {0}", info.Status);
                Console.WriteLine("\t not run: {0}", info.NotRunCount);
                Console.WriteLine("\t passed : {0}", info.PassedCount);
                Console.WriteLine("\t Failed : {0}", info.FailedCount);
                Console.WriteLine("\t Running: {0}", info.RunningCount);
            }

            // list all the tests for each project
            Console.WriteLine("\nGetting all projects and their tests");
            foreach (string name in manager.GetProjectNames())
            {
                Project project = manager.GetProject(name);

                Console.WriteLine("Project name : {0}, status: {1}", project.Name, project.Info.Status);

                foreach (ProductInstance pi in project.GetProductInstances())
                {
                    Console.WriteLine("Product Instance : {0}, Machine Pool : {1}, Platform type : {2}", pi.Name, pi.MachinePool.Name, pi.OSPlatform.Description);

                    foreach (Target target in pi.GetTargets())
                    {
                        Console.WriteLine("Target Name : {0}", target.Name);

                        foreach (Test test in target.GetTests())
                        {
                            Console.WriteLine("\tTest : {0}, status : {1}", test.Name, test.Status);
                        }
                    }
                }
            }

        }
    }
}

```

## <span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>PowerShell


```PowerShell
. ..\Initialization.ps1

write-Host "Usage: %SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe -file ListProjects.ps1 "
write-host "or to connect to a package file "
write-Host "Usage: %SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe -file ListProjects.ps1 <<PackageFileName>>"

$PackageName = $args[0]

# we need to connect to the Server
if ($PackageName -eq $null -OR $PackageName -eq "")
{
    # create the default manager
    $Manager = initialize
}
else
{
    write-host connecting to the package $PackageName
    # need to call into the init function to load the DLLS
    # assign to unused to prevent the default manager from writing to the console
    $Unused = initialize

    # now load from a package
    $Manager = new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.Submission.PackageManager -Args $PackageName
}

$RootPool = $Manager.GetRootMachinePool();

# first get a list of all projects
write "All project names on this controller"
$Manager.GetProjectNames() 

# List all projects, and get the basic status of each
$Manager.GetProjectInfoList() | foreach {
    write-host "Name   : " $_.Name
    write-host "`tStatus : " $_.Status
    write-host "`tNotRun : " $_.NotRunCount.ToString()
    write-host "`tPassed : " $_.PassedCount
    write-host "`tFailed : " $_.FailedCount
    write-host "`tRunning: " $_.RunningCount
    }

# Listing all of the Tests for each project
$Manager.GetProjectNames() | foreach {
    $Project = $Manager.GetProject($_)

    write-host "Project Name  : " $Project.Name  -ForegroundColor DarkCyan
    write-host "`tProject Status: " $Project.Info.Status

    # Listing all of the product instances
    $Project.GetProductInstances() | foreach {
        write-host "Product Instance : " $_.Name  -ForegroundColor DarkCyan
        write-host "`tMachine pool : " $_.MachinePool.Name 
        write-host "`tOS Platform : " $_.OSPlatform.Description

        $_.GetTargetFamilies() | foreach {

            write-host "Target Family : " $_.Family.Name -ForegroundColor DarkCyan

            # get target data
            $_.GetTargets() | foreach {
                write-host "Target : " $_.Name  -ForegroundColor DarkCyan
                write-host "`tType : " $_.TargetType
                write-host "`tKey   : " $_.Key 
                
                # there is more infomation if this is a device type
                $DeviceData =  $_ –AS [Microsoft.Windows.Kits.Hardware.ObjectModel.IDeviceTargetData]
                if ($DeviceData -ne $null)
                {
                    write-host "`tManufacturer : " $DeviceData.Manufacturer
                    write-host "`tVendorId : " $DeviceData.VendorId
                    write-host "`tDeviceClass : " $DeviceData.DeviceClass
                    write-host "`tInBox : " $DeviceData.AllInboxDrivers
                    write-host "`tDriver : "
                    $DeviceData.Drivers
                    write-host "`tDriverHash : "
                    $DeviceData.DriverHash
                }

                # there is more infomation if this is a System type
                $SystemData = $_ -AS [Microsoft.Windows.Kits.Hardware.ObjectModel.ISystemTargetData]
                if ($SystemData -ne $null)
                {
                    write-host "`tManufacturer : " $SystemData.Manufacturer
                    write-host "`tModel : " $SystemData.Model                    
                }

                # there is more infomation if this is a System type
                $FilterData = $_ -AS [Microsoft.Windows.Kits.Hardware.ObjectModel.IFilterTargetData] 
                if ($FilterData -ne $null)
                {
                    write-host "`tManufacturer : " $FilterData.Manufacturer
                    write-host "`tVersion : " $FilterData.Version                    
                    write-host "`tAllInbox : " $FilterData.AllInboxDrivers                    
                }
                
                write-host "`tFeatures : " 
                $_.GetFeatures() | foreach { 
                    write-host "`t`t" $_.FullName 

                    $_.GetRequirements() | foreach {
                        write-host "`t`t`tRequirement: " $_.FullName
                    }
                }                
            }

            # now list all of the tests for this family
            write-host "Tests:"
            $_.GetTests() | foreach {
                write-host "`t" $_.Name -NoNewline
                if ($_.GetTestTargets().Count -ne 1)
                    { write-host " - shared" }
                else
                    { write-host " -  not shared" }
            }
        }
    }
}
```

 

 






