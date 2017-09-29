---
title: Machines in use
description: Machines in use
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: FAE612C8-0F90-4FFD-9092-9AA3262177DA
---

# Machines in use


This sample shows how to retrieve the names of machines on which tests are currently running.

## <span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>**PowerShell**


``` syntax
. ..\Initialization.ps1

write-Host "Usage: %SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe -file MachinesInUse.ps1 <<ProjectName>>"

$Manager = Initialize


$ProjectName = $Args[0]
Write-Host Getting Project named : $ProjectName
$Project = $Manager.GetProject($ProjectName)

$Project.GetProductInstances() | foreach {    
    $_.GetTargetFamilies() | foreach {
# get all of the running tests
        $_.GetTests() | where {$_.Status -eq [Microsoft.Windows.Kits.Hardware.ObjectModel.TestResultStatus]::InQueue } | foreach {
            
# this is a test
            $Test = $_
            Write-Host Test is running or queued : $_.Name
# it should have children, see where they are running on
            
            $Results = $_.GetTestResults()
            
#Running tests
            $Results | where {$_.Status -eq [Microsoft.Windows.Kits.Hardware.ObjectModel.TestResultStatus]::InQueue} | foreach {
                Write-Host test is waiting
                $Test.GetTestTargets() | foreach { Write-Host `tMachine: $_.Machine.Name $_.Name $_.Machine.Status }
            }
        
            $Results | where {$_.Status -eq [Microsoft.Windows.Kits.Hardware.ObjectModel.TestResultStatus]::Running} | foreach {
                Write-Host test is Running
                $_.Machine.Name
            }
        }       
    }
}
```

 

 






