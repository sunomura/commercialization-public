---
title: ProductInstance.GetTargetFamilies Method
description: ProductInstance.GetTargetFamilies Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 87e49d70-6c08-4092-99ca-7a6884a77564
---

# ProductInstance.GetTargetFamilies Method


This method retrieves an enumerable list of TargetFamilies that expose the product to the system.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

`Dim returnValue As ReadOnlyCollection(Of TargetFamily)`

`returnValue = instance.GetTargetFamilies`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetTargetFamilies As ReadOnlyCollection(Of TargetFamily)`

**C#**

`public abstract ReadOnlyCollection<TargetFamily> GetTargetFamilies ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a collection of **DeviceFamily** objects.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






