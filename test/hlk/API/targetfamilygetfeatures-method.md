---
title: TargetFamily.GetFeatures Method
description: TargetFamily.GetFeatures Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1cdf9415-336b-49f4-b709-afc29cbd8fcc
---

# TargetFamily.GetFeatures Method


This method retrieves a list of features for this **TargetFamily**.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TargetFamily`

`Dim returnValue As ReadOnlyCollection(Of Feature)`

`returnValue = instance.GetFeatures`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetFeatures As ReadOnlyCollection(Of Feature)`

**C#**

`public abstract ReadOnlyCollection<Feature> GetFeatures ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is the collection of features.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






