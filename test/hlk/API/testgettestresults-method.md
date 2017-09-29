---
title: Test.GetTestResults Method
description: Test.GetTestResults Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3c8183e5-06b0-41b2-9c2b-9d89b17cf6cf
---

# Test.GetTestResults Method


This method retrieves the list of the test results generated during runs of this certification test.

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

`Dim returnValue As ReadOnlyCollection(Of TestResult)`

`returnValue = instance.GetTestResults`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetTestResults As ReadOnlyCollection(Of TestResult)`

**C#**

`public abstract ReadOnlyCollection<TestResult> GetTestResults ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a collection of results for the test.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






