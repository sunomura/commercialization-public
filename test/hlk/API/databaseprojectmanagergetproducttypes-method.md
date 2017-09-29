---
title: DatabaseProjectManager.GetProductTypes Method
description: DatabaseProjectManager.GetProductTypes Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: bee1b34f-79d9-4714-a877-a3dfb388d43d
---

# DatabaseProjectManager.GetProductTypes Method


This method returns all of the product types stored in the Windows HCK.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DatabaseProjectManager`

`Dim returnValue As ReadOnlyCollection(Of ProductType)`

`returnValue = instance.GetProductTypes`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function GetProductTypes As ReadOnlyCollection(Of ProductType)`

**C#**

`public override ReadOnlyCollection<ProductType> GetProductTypes ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a list of product types.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






