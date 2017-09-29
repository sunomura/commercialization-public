---
title: Machine.LastHeartbeat Property
description: Machine.LastHeartbeat Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a173d0fb-a084-4769-879b-c43300e6c47d
---

# Machine.LastHeartbeat Property


Represents the last heartbeat time.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Machine`

`Dim value As DateTime`

`value = instance.LastHeartbeat`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<IgnoreDataMemberAttribute> _`

`Public MustOverride ReadOnly Property LastHeartbeat As DateTime`

**C#**

`[IgnoreDataMemberAttribute]`

`public abstract DateTime LastHeartbeat { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **DateTime**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This will update the heartbeat and invoke a general refresh of the device.

This is not supported when the Project Manager is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






