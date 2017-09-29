---
title: Test.GetMachineRole Method
description: Test.GetMachineRole Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c152370c-da18-4f13-bacc-19ed5c15b2b4
---

# Test.GetMachineRole Method


This method returns a logical Machine Set.

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

`Dim returnValue As MachineSet`

`returnValue = instance.GetMachineRole`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetMachineRole As MachineSet`

**C#**

`public abstract MachineSet GetMachineRole ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns the [MachineSet](machineset-class.md) needed by this Test. Null is returned if the test does not use MachineRoles.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Most tests do not have machine roles which will return NULL.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






