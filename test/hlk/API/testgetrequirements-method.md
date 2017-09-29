---
title: Test.GetRequirements Method
description: Test.GetRequirements Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 38fb0ae1-9f17-41ce-b906-e0d0a818353b
---

# Test.GetRequirements Method


This method retrieves the enumerable list of certification requirements that this test verifies.

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

`Dim returnValue As ReadOnlyCollection(Of Requirement)`

`returnValue = instance.GetRequirements`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetRequirements As ReadOnlyCollection(Of Requirement)`

**C#**

`public abstract ReadOnlyCollection<Requirement> GetRequirements ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a collection of requirements that this test can validate.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






