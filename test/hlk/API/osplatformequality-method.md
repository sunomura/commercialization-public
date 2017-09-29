---
title: OSPlatform.Equality Method
description: OSPlatform.Equality Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d6faff5d-6e8a-41ec-8343-dae7fb7879e2
---

# OSPlatform.Equality Method


This method provides an Equality operator between two **OSPlatform** objects.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim first As OSPlatform`

`Dim second As OSPlatform`

`Dim returnValue As Boolean`

`returnValue = (first = second)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Shared Operator = ( _`

          `first As OSPlatform, _`

          `second As OSPlatform _`

`) As Boolean`

**C#**

`public static bool operator == (`

          `OSPlatform first,`

          `OSPlatform second`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*first*

     The first **OSPlatform** object to compare against.

*second*

     The second **OSPlatform** object to compare against.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the **OSPlatform** objects are identical; otherwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






