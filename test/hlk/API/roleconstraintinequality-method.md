---
title: RoleConstraint.Inequality Method
description: RoleConstraint.Inequality Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 57f496bf-c7b8-4ccd-a033-fcb7c48fb9f2
---

# RoleConstraint.Inequality Method


This method acts as an InEquality operator. It returns false if either operand is **null**.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim first As RoleConstraint`

`Dim second As RoleConstraint`

`Dim returnValue As Boolean`

`returnValue = (first <> second)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Shared Operator <> ( _`

     `first As RoleConstraint, _`

     `second As RoleConstraint _`

`) As Boolean`

**C#**

`public static bool operator != (`

          `RoleConstraint first,`

          `RoleConstraint second`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*first*

          The first value to compare against.

*second*

          The second value to compare against.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the objects are not equal, or **false** if the objects are the same or if either object is **null**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






