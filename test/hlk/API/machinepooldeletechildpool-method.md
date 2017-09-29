---
title: MachinePool.DeleteChildPool Method
description: MachinePool.DeleteChildPool Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dc7a0403-f7fc-4421-a406-c749cc1010ca
---

# MachinePool.DeleteChildPool Method


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


Any machines that are in this pool are moved to the default pool. This will not remove any results. However, any tests that are still outstanding will be canceled.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






