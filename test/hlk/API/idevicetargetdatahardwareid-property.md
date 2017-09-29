---
title: IDeviceTargetData.HardwareId Property
description: IDeviceTargetData.HardwareId Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e16b216c-5f27-48b0-a1ea-26919d86341b
---

# IDeviceTargetData.HardwareId Property


This property represents the hardware IDs for a deviceTarget object.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IDeviceTargetData`

`Dim value As ReadOnlyCollection(Of String)`

`value = instance.HardwareId`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property HardwareId As ReadOnlyCollection(Of String)`

**C#**

`ReadOnlyCollection<string> HardwareId { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **ReadOnlyCollection**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Hardware IDs are returned in a particular order. The order is determined by the OS on the machine where the target is found. The strong matched hardware ID is first in the collection and the last hardware ID is the weakest matching hardware ID.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






