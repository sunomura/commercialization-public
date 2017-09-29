---
title: MachineSet.Equals Method (MachineSet)
description: MachineSet.Equals Method (MachineSet)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 529edcdf-c8a7-4c51-9ba1-fa3d94a6ab78
---

# MachineSet.Equals Method (MachineSet)


This method compares two **MachineSet** instances.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachineSet`

`Dim otherMachineSet As MachineSet`

`Dim returnValue As Boolean`

`returnValue = instance.Equals(otherMachineSet)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function Equals ( _`

          `otherMachineSet As MachineSet _`

`) As Boolean`

**C#**

`public bool Equals (`

          `MachineSet otherMachineSet`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*otherMachineSet*

     The **MachineSet** object to compare against.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the two objects are equal; otherwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






