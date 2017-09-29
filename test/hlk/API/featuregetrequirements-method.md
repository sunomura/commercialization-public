---
title: Feature.GetRequirements Method
description: Feature.GetRequirements Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b6a16008-ab8b-4cdc-bf84-2aed95bc79c1
---

# Feature.GetRequirements Method


This method retrieves the requirements associated with this **Feature**.

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Feature`

`Dim returnValue As ReadOnlyCollection(Of Requirement)`

`returnValue = instance.GetRequirements`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetRequirements As ReadOnlyCollection(Of Requirement)`

**C#**

`public abstract ReadOnlyCollection<Requirement> GetRequirements ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a read-only collection of requirements.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






