---
title: Target.DriverStatus Property
description: Target.DriverStatus Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e1135be4-f466-4bef-aa6f-3d024ff9d603
---

# Target.DriverStatus Property


This property represents the driver status of the test target.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Target`

`Dim value As TargetDriversType`

`value = instance.DriverStatus`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataMemberAttribute> _`

`Public Property DriverStatus As TargetDriversType`

**C#**

`[DataMemberAttribute]`

`public TargetDriversType DriverStatus { get; }`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns [TargetDriversType Enumeration](targetdriverstype-enumeration.md).

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The status provides information on the driver that is associated with the target. The value is estimated.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






