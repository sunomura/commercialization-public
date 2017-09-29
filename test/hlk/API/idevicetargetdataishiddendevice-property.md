---
title: IDeviceTargetData.IsHiddenDevice Property
description: IDeviceTargetData.IsHiddenDevice Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 807f39e2-9947-4cbb-b6ad-a7b4a376551a
---

# IDeviceTargetData.IsHiddenDevice Property


This property represents a value indicating whether this should be hidden from the user by default for a deviceTarget object.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IDeviceTargetData`

`Dim value As Boolean`

`value = instance.IsHiddenDevice`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property IsHiddenDevice As Boolean`

**C#**

`bool IsHiddenDevice { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


**true** if the test target should be hidden from testers; otherwise, **false**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The devices that are marked hidden are typically devices that are not commonly certified.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






