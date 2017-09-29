---
title: MachineRole.IsValidRole Method
description: MachineRole.IsValidRole Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d9acdf0c-4bd8-43a9-ac16-f6be453ded2f
---

# MachineRole.IsValidRole Method


This method checks to see if the other machine role is sufficient to enable this machine role.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachineRole`

`Dim otherMachineRole As MachineRole`

`Dim returnValue As Boolean`

`returnValue = instance.IsValidRole(otherMachineRole)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function IsValidRole ( _`

          `otherMachineRole As MachineRole _`

`) As Boolean`

**C#**

`public bool IsValidRole (`

          `MachineRole otherMachineRole`

`) `

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*otherMachineRole*

          The **MachineRole** object to compare against this **MachineRole** object.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the two objects being compared are the same; otherwise, **false**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown when the *otherMachineRole* parameter is **null**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






