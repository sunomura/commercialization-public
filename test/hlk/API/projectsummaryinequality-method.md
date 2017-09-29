---
title: ProjectSummary.Inequality Method
description: ProjectSummary.Inequality Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fbd0191b-30eb-4b42-a093-1f3880355d63
---

# ProjectSummary.Inequality Method


This method provides an Inequality operator between two **ProjectSummary** objects.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim first As ProjectSummary`

`Dim second As ProjectSummary`

`Dim returnValue As Boolean`

`returnValue = (first <> second)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Shared Operator <> ( _`

          `first As ProjectSummary, _`

          `second As ProjectSummary _`

`) As Boolean`

**C#**

`public static bool operator != (`

          `ProjectSummary first,`

          `ProjectSummary second`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*first*

          The first **ProjectSummary** object to compare against.

*second*

          The second **ProjectSummary** object to compare against.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the objects are not equal, or **false** if the objects are the same or if either object is **null**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






