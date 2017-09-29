---
title: MachinePool.Executable Property
description: MachinePool.Executable Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 66ed70d7-4469-4af1-b2b7-64dc56e43290
---

# MachinePool.Executable Property


This property represents a value indicating whether this pool can be used to run tests.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachinePool`

`Dim value As Boolean`

`value = instance.Executable`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride ReadOnly Property Executable As Boolean`

**C#**

`public abstract bool Executable { get; }`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **Boolean**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Tests cannot be scheduled on a machine that resides in certain reserved Machine Pools. This value indicates if tests can be run on any machines in this machine pool.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






