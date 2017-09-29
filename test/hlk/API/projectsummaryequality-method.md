---
title: ProjectSummary.Equality Method
description: ProjectSummary.Equality Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ab16f658-d641-48a9-85f5-60d450d21c56
---

# ProjectSummary.Equality Method


This method provides an Equality operator between two **ProjectSummary** objects.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim first As ProjectSummary`

`Dim second As ProjectSummary`

`Dim returnValue As Boolean`

`returnValue = (first = second)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Shared Operator = ( _`

          `first As ProjectSummary, _`

          `second As ProjectSummary _`

`) As Boolean`

**C#**

`public static bool operator == (`

          `ProjectSummary first,`

          `ProjectSummary second`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*first*

     The first **ProjectSummary** object to compare against.

*second*

     The second **ProjectSummary** object to compare against.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the **ProjectSummary** objects are identical; otherwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






