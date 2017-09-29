---
title: IDeviceTargetData.Drivers Property
description: IDeviceTargetData.Drivers Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7e30a2d9-fb11-4032-8907-bd2dbba2aa5c
---

# IDeviceTargetData.Drivers Property


This property represents all of the drivers for this device that can be identified for this deviceTarget object.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IDeviceTargetData`

`Dim value As ReadOnlyCollection(Of String)`

`value = instance.Drivers`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property Drivers As ReadOnlyCollection(Of String)`

**C#**

`ReadOnlyCollection<string> Drivers { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **ReadOnlyCollection**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Upper and lower filter drivers may also be included.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






