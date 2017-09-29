---
title: MachineRole.RemoveMachine Method
description: MachineRole.RemoveMachine Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ded79d30-e3a5-41dc-b195-00747980b3de
---

# MachineRole.RemoveMachine Method


This method removes a machine (test computer) from the machine role.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachineRole`

`Dim machineToRemove As Machine`

`instance.RemoveMachine(machineToRemove)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

``` syntax
Public Sub RemoveMachine(ByVal machineToRemove As Machine)
    If (machineToRemove <> Nothing) Then
        If (Me.machines.Contains(machineToRemove)) Then
            Me.machines.Remove(machineToRemove)
            Return
        Else
            Throw ScheduleException.BuildException("MachineRole::RemoveMachine() - Instance of Machine does not exist in the machine list.")
        End If
    Else
        Throw New ArgumentNullException("machineToRemove")
    End If
End Sub
```

**C#**

``` syntax
public void RemoveMachine(Machine machineToRemove)
{
    if (machineToRemove != null)
    {
        if (this.machines.Contains(machineToRemove))
        {
            this.machines.Remove(machineToRemove);
            return;
        }
        else
        {
            throw ScheduleException.BuildException("MachineRole::RemoveMachine() - Instance of Machine does not exist in the machine list.");
        }
    }
    else
    {
        throw new ArgumentNullException("machineToRemove");
    }
}
```

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*machineToRemove*

     The machine (test computer) to remove.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown if

-   The *machineToRemove* parameter is null.

-   The *machineToRemove* does not exist in the current machine list.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






