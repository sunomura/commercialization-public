---
title: MachinePool.CreateChildPool Method
description: MachinePool.CreateChildPool Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 4797c7b4-ce82-40c1-8615-b1ce6a98a0d7
---

# MachinePool.CreateChildPool Method


This method creates a child machine pool.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachinePool`

`Dim name As String`

`Dim returnValue As MachinePool`

`returnValue = instance.CreateChildPool(name)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function CreateChildPool ( _`

          `name As String _`

`) As MachinePool`

**C#**

`public abstract MachinePool CreateChildPool (`

          `string name`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*name*

     The name of the pool to add to this machine pool.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **MachinePool**, which is the name of the machine pool that was added.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The child Machine Pool name must not match another existing Machine Pool name.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






