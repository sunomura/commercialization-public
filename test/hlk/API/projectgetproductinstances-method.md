---
title: Project.GetProductInstances Method
description: Project.GetProductInstances Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cebb0294-3635-40e7-afce-a8d5ba67aa0c
---

# Project.GetProductInstances Method


This method retrieves a list of **ProductInstance** objects.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Project`

`Dim returnValue As ReadOnlyCollection(Of ProductInstance)`

`returnValue = instance.GetProductInstances`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetProductInstances As ReadOnlyCollection(Of ProductInstance)`

**C#**

`public abstract ReadOnlyCollection<ProductInstance> GetProductInstances ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a collection of **ProductInstance** objects.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






