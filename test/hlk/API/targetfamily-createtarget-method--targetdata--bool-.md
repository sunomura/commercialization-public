---
title: TargetFamily.CreateTarget Method (TargetData, bool)
description: TargetFamily.CreateTarget Method (TargetData, bool)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2622AA0E-0598-4533-92F8-E809ED126C3F
---

# TargetFamily.CreateTarget Method (TargetData, bool)

>[!WARNING]
>  This method is being deprecated. Please use [CreateTarget(IEnumerable&lt;TargetData&gt;)](targetfamilycreatetarget-method--ienumerable-.md) instead.

 

Creates a target from a Target data, and adds it to the target family.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

` public abstract Target CreateTarget (`

          `TargetData target,`

          ` bool createWithoutAddingTests`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*target*

Target data to create a target.

*createWithoutAddingTests*

A flag to create the Target without adding any Tests.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns the [Target](target-class.md) object that was created.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






