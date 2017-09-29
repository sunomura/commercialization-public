---
title: MachineRole.IsValidMachine Method
description: MachineRole.IsValidMachine Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f7b85bcf-8669-4518-9b3a-aa9a80791328
---

# MachineRole.IsValidMachine Method


**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachineRole`

`Dim machineToAdd As Machine`

`Dim throwOnError As Boolean`

`Dim returnValue As Boolean`

`returnValue = instance.IsValidMachine(machineToAdd, throwOnError)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function IsValidMachine ( _`

          `machineToAdd As Machine, _`

          `throwOnError As Boolean _`

`) As Boolean`

**C#**

`public bool IsValidMachine (`

          `Machine machineToAdd,`

          `bool throwOnError`

`) `

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*machineToAdd*

          The machine (test computer) to test against.

*throwOnError*

          A flag determining if this function should throw exceptions.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the machine (test computer) is appropriate for this machine role; otherwise, **false**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown when the *machineToAdd* parameter represents a test computer that is not valid for this role, but only if the *throwOnError* flag is set to **true**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






