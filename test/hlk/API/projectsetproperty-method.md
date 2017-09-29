---
title: Project.SetProperty Method
description: Project.SetProperty Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6d3f78cd-7054-4237-a855-804a4f1e35f0
---

# Project.SetProperty Method


This method updates or creates a new property value.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Project`

`Dim nameOfProperty As String`

`Dim propertyValue As String`

`Dim returnValue As String`

`returnValue = instance.SetProperty(nameOfProperty, propertyValue)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function SetProperty ( _`

          `nameOfProperty As String, _`

          `propertyValue As String _`

`) As String `

**C#**

`public abstract string SetProperty (`

          `string nameOfProperty,`

          `string propertyValue`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*nameOfProperty*

     The name of the property to update or create.

*propertyValue*

     The machine pool to use for this **ProductInstance**.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **String**, which is the string value of the new value of the property that was set.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An error occurs if *nameOfProperty* is **null** or empty, or if *propertyValue* is **null**.

This method is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






