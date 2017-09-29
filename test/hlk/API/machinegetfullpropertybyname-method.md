---
title: Machine.GetFullPropertyByName Method
description: Machine.GetFullPropertyByName Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 90fe1b84-3df2-4f16-8f3c-c5d3fde70c85
---

# Machine.GetFullPropertyByName Method


This method retrieves the value of a particular dimension value.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Machine`

`Dim propertyName As String`

`Dim returnValue As MachineProperty`

`returnValue = instance.GetFullPropertyByName(propertyName)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetFullPropertyByName ( _`

          `propertyName As String _`

`) As MachineProperty`

**C#**

`public abstract MachineProperty GetFullPropertyByName (`

          `string propertyName`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*propertyName*

     The name of the property to get.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **MachineProperty**, which is the particular Machine property (dimensions).

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown when:

-   The *propertyName* parameter is null.

-   The *propertyName* parameter is empty.

-   The *propertyName* cannot be found.

    Machine Properties are also referred to as Dimensions.

    This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






