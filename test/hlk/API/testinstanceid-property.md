---
title: Test.InstanceId Property
description: Test.InstanceId Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 4eef86e9-d97e-48e3-9d3a-27a2a09ae8ef
---

# Test.InstanceId Property


Gets the instance Id.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public abstract string InstanceId { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns the InstanceId.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


A test may be needed for every target in a target family. This instance ID is unique across all instances of tests (applied to many targets).

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






