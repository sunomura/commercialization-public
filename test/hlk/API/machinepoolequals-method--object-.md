---
title: MachinePool.Equals Method (Object)
description: MachinePool.Equals Method (Object)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e5cd0b55-ee08-4d4b-b2a0-22622798c82f
---

# MachinePool.Equals Method (Object)


**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachinePool`

`Dim obj As Object`

`Dim returnValue As Boolean`

`returnValue = instance.Equals(obj)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function Equals ( _`

          `obj As Object _`

`) As Boolean`

**C#**

`public override bool Equals (`

          `Object obj`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*obj*

     An object to compare against this **MachinePool** object.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **Boolean**, which has a value of **true** if the two OSPlatforms are equal, or a value of **false** if they are different.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






