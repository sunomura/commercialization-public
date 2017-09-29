---
title: Machine.GetPropertyByName Method
description: Machine.GetPropertyByName Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 05b7914b-ac8f-4ae4-b81c-e5c23278890e
---

# Machine.GetPropertyByName Method


This method retrieves a particular dimension value.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Machine`

`Dim propertyName As String`

`Dim returnValue As String`

`returnValue = instance.GetPropertyByName(propertyName)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetPropertyByName ( _`

          `propertyName As String _`

`) As String`

**C#**

`public abstract string GetPropertyByName (`

          `string propertyName`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*propertyName*

     The name of the property to get.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **String**, which is the particular Machine property (dimension) for this machine.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Machine Properties are also referred to as Dimensions.

This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






