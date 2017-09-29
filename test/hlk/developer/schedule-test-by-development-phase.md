---
title: Schedule test by Development Phase
description: Schedule test by Development Phase
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: CC2D3F1B-729F-4E84-B0EF-2EBEE2A33E3A
---

# Schedule test by Development Phase


This sample demonstrates a few ways to schedule tests.

## <span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>**PowerShell**


``` syntax
Clear-Host
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dbconnection.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.submission.dll")

$connectFileName = $env:WTTSTDIO + "connect.xml"
Write-Host Opening connection file $connectFileName
$connectFile = [xml](Get-Content $connectFileName)

$ControllerName = $connectFile.Connection.GetAttribute("Server")
$DatabaseName = $connectFile.Connection.GetAttribute("Source")

$Manager = new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection.DatabaseProjectManager -Args $ControllerName, $DatabaseName

#Load Project
$Project = $Manager.GetProject("TestProject")

#let's define enumerations for all development phases
$TuningAndValidation = [Microsoft.Windows.Kits.Hardware.ObjectModel.DevelopmentPhase]::TuningAndValidation
$BringUp = [Microsoft.Windows.Kits.Hardware.ObjectModel.DevelopmentPhase]::BringUp
$DevelopmentAndIntegration = [Microsoft.Windows.Kits.Hardware.ObjectModel.DevelopmentPhase]::DevelopmentAndIntegration
$Reliability = [Microsoft.Windows.Kits.Hardware.ObjectModel.DevelopmentPhase]::Reliability
$Manufacturing = [Microsoft.Windows.Kits.Hardware.ObjectModel.DevelopmentPhase]::Manufacturing
$Support = [Microsoft.Windows.Kits.Hardware.ObjectModel.DevelopmentPhase]::Support

#Project test summary for each development phasent))

$Tests = $Project.GetTests()

Write-Host ("Test summary for project {0}" -f $Project.Name)
Write-Host ("   TuningAndValidation tests: {0}" -f ($Tests | where { $_.DevelopmentPhases.Contains($TuningAndValidation)}).Length)
Write-Host ("   BringUp tests: {0}" -f ($Tests | where { $_.DevelopmentPhases.Contains($BringUp)}).Length)
Write-Host ("   DevelopmentAndIntegration tests: {0}" -f ($Tests | where { $_.DevelopmentPhases.Contains($DevelopmentAndIntegration)}).Length)
Write-Host ("   Reliability tests: {0}" -f ($Tests | where { $_.DevelopmentPhases.Contains($Reliability)}).Length)
Write-Host ("   Manufacturing tests: {0}" -f ($Tests | where { $_.DevelopmentPhases.Contains($Manufacturing)}).Length)
Write-Host ("   Support tests: {0}" -f ($Tests | where { $_.DevelopmentPhases.Contains($Support)}).Length)
Write-Host ("   Total tests: {0}" -f ($Tests.Count))

#schedule all Reliability tests in the project
$DevelopmentPhases = New-Object "System.Collections.Generic.List[Microsoft.Windows.Kits.Hardware.ObjectModel.DevelopmentPhase]"
$DevelopmentPhases.Add($Reliability)
foreach($Test in $Project.GetTests() | where { $_.DevelopmentPhases.Contains($Reliability)})
{
    Write-Host ("Scheduling 'Reliability' test: {0}" -f $Test.Name)
    
    $Test.QueueTest()
}

#schedule all BringUp tests in the project
$DevelopmentPhases = New-Object "System.Collections.Generic.List[Microsoft.Windows.Kits.Hardware.ObjectModel.DevelopmentPhase]"
$DevelopmentPhases.Add($BringUp)
foreach($Test in $Project.GetTests() | where { $_.DevelopmentPhases.Contains($BringUp)})
{
    Write-Host ("Scheduling 'BringUp' test: {0}" -f $Test.Name)
    $Test.QueueTest()
}


# Sample code for creating a new project and scheduling BringUp tests
# create the project name
$now = [System.DateTime]::Now
$ProjectName = "SampleDevelopmentPhasesTestProject $now" 


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
Write-Host "Creating a target for " $data[0].Name
$Target = $ProductInstance.CreateTarget($data[0])
write-Host Successfully created a Target for $Target.Name that has $Target.GetTests().Count tests

# Schedule "BringUp" test - i.e., tests that is marked as "BringUp" for Development Phases
# Get the first "BringUp" test and schedule it
$Test = $Target.GetTests() | where { $_.DevelopmentPhases.Contains($BringUp)}[0]
$Test.QueueTest()
```

 

 






