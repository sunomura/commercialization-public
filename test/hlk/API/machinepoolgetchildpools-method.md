---
title: MachinePool.GetChildPools Method
description: MachinePool.GetChildPools Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6edce656-1368-4dce-9ec9-80cd8f700f40
---

# MachinePool.GetChildPools Method


**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachinePool`

`Dim returnValue As ReadOnlyCollection(Of MachinePool)`

`returnValue = instance.GetChildPools`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetChildPools As ReadOnlyCollection(Of MachinePool)`

**C#**

`public abstract ReadOnlyCollection<MachinePool> GetChildPools ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is the collection of child pools.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






