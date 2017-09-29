---
title: MachineSet.IsValid Method
description: MachineSet.IsValid Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3fd22376-f29c-4982-9259-e3df0fdcc1ae
---

# MachineSet.IsValid Method


This method checks to see if the specified **MachineSet** is sufficient to enable this machine set.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachineSet`

`Dim otherMachineSet As MachineSet`

`Dim returnValue As Boolean`

`returnValue = instance.IsValid(otherMachineSet)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function IsValid ( _`

          `otherMachineSet As MachineSet _`

`) As Boolean`

**C#**

`public bool IsValid (`

          `MachineSet otherMachineSet`

`) `

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*otherMachineSet*

          The **MachineSet** object to compare against this **MachineSet** object.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the two objects being compared are the same; otherwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






