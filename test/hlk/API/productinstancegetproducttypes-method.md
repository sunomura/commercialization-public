---
title: ProductInstance.GetProductTypes Method
description: ProductInstance.GetProductTypes Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c4c6b17b-1d80-4e4d-b459-e0f565d8a37f
---

# ProductInstance.GetProductTypes Method


This method attempts to detect product types this product instance belongs to.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

`Dim returnValue As ReadOnlyCollection(Of ProductType)`

`returnValue = instance.GetProductTypes`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overridable Function GetProductTypes As ReadOnlyCollection(Of ProductType)`

**C#**

`public virtual ReadOnlyCollection<ProductType> GetProductTypes ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a list() of product types.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






