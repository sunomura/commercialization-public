---
title: Machine.SetProperty Method
description: Machine.SetProperty Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 67e42a9f-f167-46ee-8db0-e9c9e7dcc183
---

# Machine.SetProperty Method


This method creates a new, or updates an existing property value for a machine.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Machine`

`Dim nameOfPropertyToSet As String`

`Dim valueOfPropertyToSet As String`

`Dim returnValue As String`

`returnValue = instance.SetProperty(nameOfPropertyToSet, valueOfPropertyToSet)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function SetProperty ( _`

          `nameOfPropertyToSet As String, _`

          `valueOfPropertyToSet As String _`

`) As String`

**C#**

`public abstract string SetProperty (`

          `string nameOfPropertyToSet,`

          `string valueOfPropertyToSet`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*nameOfPropertyToSet*

     The name of the property to create or set.

*valueOfPropertyToSet*

     The value to set the property to.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **String**, which is the value of the property that has been set.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs if:

-   The source utility “UI” is not found.*status* is not valid.

-   The *nameOfPropertyToSet* parameter or the *valueOfPropertyToSet* parameter is **null**.

-   The *nameOfPropertyToSet* parameter or the *valueOfPropertyToSet* parameter is empty.

    This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






