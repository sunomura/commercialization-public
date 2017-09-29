---
title: Test.GetTestTargets Method
description: Test.GetTestTargets Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5b239092-5c61-47d0-af1e-a6fb18b92f61
---

# Test.GetTestTargets Method


This method retrieves a list of possible test targets for this test.

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

`Dim returnValue As ReadOnlyCollection(Of Target)`

`returnValue = instance.GetTestTargets`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetTestTargets As ReadOnlyCollection(Of Target)`

**C#**

`public abstract ReadOnlyCollection<Target> GetTestTargets ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a read-only list of test targets.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






