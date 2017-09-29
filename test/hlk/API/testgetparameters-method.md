---
title: Test.GetParameters Method
description: Test.GetParameters Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b61d5d2d-e95c-4411-82ff-b8545aab34f9
---

# Test.GetParameters Method


This method retrieves a dictionary collection of test parameters, sorted by parameter name.

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

`Dim returnValue As Dictionary(Of String, TestParameter)`

`returnValue = instance.GetParameters`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetParameters As Dictionary(Of String, TestParameter)`

**C#**

`public abstract Dictionary<string,TestParameter> GetParameters ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **Dictionary**, which is a dictionary of [TestParameter Class](testparameter-class.md) objects used when scheduling this test.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






