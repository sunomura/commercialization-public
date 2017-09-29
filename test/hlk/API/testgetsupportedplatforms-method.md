---
title: Test.GetSupportedPlatforms Method
description: Test.GetSupportedPlatforms Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a77d3974-b812-466d-928f-3c826c45f34d
---

# Test.GetSupportedPlatforms Method


This method returns a enumerable list of the architectures supported by this certification test.

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

`Dim returnValue As ReadOnlyCollection(Of OSPlatform)`

`returnValue = instance.GetSupportedPlatforms`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetSupportedPlatforms As ReadOnlyCollection(Of OSPlatform)`

**C#**

`public abstract ReadOnlyCollection<OSPlatform> GetSupportedPlatforms ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a collection of platforms on which this test can be run.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






