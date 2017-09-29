---
title: IDeviceCollectionTargetData.Manufacturer Property
description: IDeviceCollectionTargetData.Manufacturer Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 283873e0-b914-4949-ad1d-919222a90af6
---

# IDeviceCollectionTargetData.Manufacturer Property


**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IDeviceCollectionTargetData`

`Dim value As String`

`value = instance.Manufacturer`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property Manufacturer As String`

**C#**

`string Manufacturer { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **String**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Returns null if a manufacturer cannot be found.

 

 






