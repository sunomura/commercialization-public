---
title: ProductInstance.CanCreateTarget Method
description: ProductInstance.CanCreateTarget Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 240a5683-7261-481a-9b64-b351ca789dd7
---

# ProductInstance.CanCreateTarget Method


This method determines if a target can be created from **TargetData** object provided. The target is not added to the product instance.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

`Dim data As TargetData`

`Dim returnValue As Boolean`

`returnValue = instance.CanCreateTarget(data)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function CanCreateTarget ( _`

          `data As TargetData _`

`) As Boolean`

**C#**

`public bool CanCreateTarget (`

          `TargetData data`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*data*

     The **TargetData** to use to create the target

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the target can be created; otherwise, **false**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This method only validates that a target can be created. To add a target use the **CreateTarget** method.

If *data* is **null** an exception is thrown.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






