---
title: PackageManager.GetFilters Method
description: PackageManager.GetFilters Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5fb0255a-2ab2-4c88-bc51-cc6f691a65d4
---

# PackageManager.GetFilters Method


This method retrieves the filters present in the submission package. Getting filters from a package is not supported.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageManager`

`Dim returnValue As ReadOnlyCollection(Of IFilter)`

`returnValue = instance.GetFilters`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function GetFilters As ReadOnlyCollection(Of IFilter)`

**C#**

`public override ReadOnlyCollection<IFilter> GetFilters ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






