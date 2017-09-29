---
title: Task.GetAppliedFilters Method
description: Task.GetAppliedFilters Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 277423fd-31c2-4b46-9c52-62e2744783da
---

# Task.GetAppliedFilters Method


This method retrieves the filters applied for this task result.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Task`

`Dim returnValue As ReadOnlyCollection(Of IFilter)`

`returnValue = instance.GetAppliedFilters`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetAppliedFilters As ReadOnlyCollection(Of IFilter)`

**C#**

`public abstract ReadOnlyCollection<IFilter> GetAppliedFilters ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a read-only collection of filters applied to a test task.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


If the task does not have a TaskResult or the TaskResult status is Not Complete, this method returns an empty collection.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






