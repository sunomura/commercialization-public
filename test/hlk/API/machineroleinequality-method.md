---
title: MachineRole.Inequality Method
description: MachineRole.Inequality Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cf5caaac-f0df-489a-ac11-e44559d2fb4f
---

# MachineRole.Inequality Method


This method acts as an Inequality operator. The method always returns **false** if either operand is **null**; otherwise, returns **true** or **false**.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim first As MachineRole`

`Dim second As MachineRole`

`Dim returnValue As Boolean`

`returnValue = (first <> second)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Shared Operator <> ( _`

          `first As MachineRole, _`

          `second As MachineRole _`

`) As Boolean`

**C#**

`public static bool operator != (`

          `MachineRole first,`

          `MachineRole second`

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

 

 






