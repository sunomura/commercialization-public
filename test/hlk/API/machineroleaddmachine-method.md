---
title: MachineRole.AddMachine Method
description: MachineRole.AddMachine Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d0379b38-fd9c-4df0-8b45-3b3f6a51a7ec
---

# MachineRole.AddMachine Method


This method adds a machine (test computer) to this role.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachineRole`

`Dim machineToAdd As Machine`

`instance.AddMachine(machineToAdd)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub AddMachine ( _`

          `machineToAdd As Machine _`

`) `

**C#**

`public void AddMachine (`

          `Machine machineToAdd`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*machineToAdd*

     The machine (test computer) to add to this role.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown when the machine is not valid for this role, but only if the parameter *throwOnError* is true. The following are the cases where the machine would not be appropriate:

-   Machine is from a different Machine Pool.

-   Machine has already been added.

-   Maximum number of Machines for the role has been reached.

-   The Machine has a dimension value that is out of the expected range.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






