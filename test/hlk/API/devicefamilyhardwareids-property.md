---
title: DeviceFamily.HardwareIds Property
description: DeviceFamily.HardwareIds Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e66e43a4-704f-4212-80f3-1d5d8e58da48
---

# DeviceFamily.HardwareIds Property


This property represents a collection of hardware IDs used to identify the test targets in this device family.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DeviceFamily`

`Dim value As ReadOnlyCollection(Of String)`

`value = instance.HardwareIds`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride ReadOnly Property HardwareIds As ReadOnlyCollection(Of String)`

**C#**

`public abstract ReadOnlyCollection<string> HardwareIds { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






