---
title: TestResult.GetAppliedFilters Method
description: TestResult.GetAppliedFilters Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a248db15-2ca5-4d25-a948-19aff96ae3e8
---

# TestResult.GetAppliedFilters Method


This method retrieves the filters applied for this test result.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TestResult`

`Dim returnValue As ReadOnlyCollection(Of IFilter)`

`returnValue = instance.GetAppliedFilters`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetAppliedFilters As ReadOnlyCollection(Of IFilter)`

**C#**

`public abstract ReadOnlyCollection<IFilter> GetAppliedFilters ()`

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






