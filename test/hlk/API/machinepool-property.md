---
title: Machine.Pool Property
description: Machine.Pool Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 33a84f15-2ac5-4bb3-86bc-054b0bee52fa
---

# Machine.Pool Property


Represents the reference of the parent pool for a machine.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Machine`

`Dim value As MachinePool`

`value = instance.Pool`

`instance.Pool = value`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<IgnoreDataMemberAttribute> _`

`Public MustOverride Property Pool As MachinePool`

**C#**

`[IgnoreDataMemberAttribute]`

`public abstract MachinePool Pool { get; set; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **MachinePool**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






