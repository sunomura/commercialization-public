---
title: Machine.EstimatedRuntime Property
description: Machine.EstimatedRuntime Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 46a26bff-ed42-4cfa-b013-6198add40b33
---

# Machine.EstimatedRuntime Property


This property represents the estimated runtime remaining for all tests which will be run against this machine (test computer).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Machine`

`Dim value As TimeSpan`

`value = instance.EstimatedRuntime`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<IgnoreDataMemberAttribute> _`

`Public MustOverride ReadOnly Property EstimatedRuntime As TimeSpan`

**C#**

`[IgnoreDataMemberAttribute]`

`public abstract TimeSpan EstimatedRuntime { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **TimeSpan**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is not supported when the Project Manager is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






