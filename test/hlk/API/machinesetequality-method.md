---
title: MachineSet.Equality Method
description: MachineSet.Equality Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c00a2b1a-ca67-4314-922e-6f17b5fc5f13
---

# MachineSet.Equality Method


This method provides an Equality operator between two **MachineSet** objects.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim first As MachineSet`

`Dim second As MachineSet`

`Dim returnValue As Boolean`

`returnValue = (first = second)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Shared Operator = ( _`

          `first As MachineSet, _`

          `second As MachineSet _`

`) As Boolean`

**C#**

`public static bool operator == (`

          `MachineSet first,`

          `MachineSet second`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*first*

     The first **MachineSet** object to compare against.

*second*

     The second **MachineSet** object to compare against.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the **MachineSet** objects are identical; otherwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






