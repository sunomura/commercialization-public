---
title: Target.IsTargetReady Property
description: Target.IsTargetReady Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 87f81227-5132-4b27-a793-af56c649a1f7
---

# Target.IsTargetReady Property


This property represents the value indicating whether the test target is currently ready to run tests (specifically, the test computer is in the “ready” state).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Target`

`Dim value As Boolean`

`value = instance.IsTargetReady`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<IgnoreDataMemberAttribute> _`

`Public MustOverride ReadOnly Property IsTargetReady As Boolean`

**C#**

`[IgnoreDataMemberAttribute]`

`public abstract bool IsTargetReady { get; }`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **Boolean**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Readiness is determined by the following checks.

-   The machine associated with the target is in ready state.

-   The machine associated with the target has a recent heartbeat (registered with the controller).

-   The machine associated with the target is in the correct machine pool (pool specified with the product instance).

If the returned value is false, Tests for this target cannot be scheduled.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






