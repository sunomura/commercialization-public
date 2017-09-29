---
title: MachinePool.MoveMachineTo Method
description: MachinePool.MoveMachineTo Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7a75dc68-b4c0-4503-8284-f1e66184c8c3
---

# MachinePool.MoveMachineTo Method


**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachinePool`

`Dim machine As Machine`

`Dim otherPool As MachinePool`

`instance.MoveMachineTo(machine, otherPool)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub MoveMachineTo ( _`

          `machine As Machine, _`

          `otherPool As MachinePool _`

`)`

**C#**

`public abstract void MoveMachineTo (`

          `Machine machine,`

          `MachinePool otherPool`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*machine*

          A machine to move from this pool.

*otherPool*

          The destination pool to move the machine to.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






