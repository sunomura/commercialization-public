---
title: MachinePool.DeleteMachine Method
description: MachinePool.DeleteMachine Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6cfe9017-0b12-49a7-a4c3-0a892ef5f7d3
---

# MachinePool.DeleteMachine Method


This method delete the named machine for this machine pool. The machine to be deleted must be a child machine of this pool.

>[!WARNING]
>  
Using the **MachinePool.DeleteMachine** method is NOT recommended because it may leave the deleted machine in an unusable state.

 

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachinePool`

`Dim nameOfMachineToDelete As String`

`instance.DeleteMachine(nameOfMachineToDelete)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub DeleteMachine ( _`

          `nameOfMachineToDelete As String _`

`) `

**C#**

`public abstract void DeleteMachine (`

          `string nameOfMachineToDelete`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*nameOfMachineToDelete*

     The name of the machine to delete from this machine pool.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This will delete any test results that are associated with this machine.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






