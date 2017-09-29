---
title: TargetFamily.CreateTarget Method (IEnumerable TargetData , bool)
description: TargetFamily.CreateTarget Method (IEnumerable TargetData , bool)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 610CA992-F8C6-43CC-850B-14BE56EA08C9
---

# TargetFamily.CreateTarget Method (IEnumerable{TargetData}, bool)

>[!WARNING]
>  This method is being deprecated. Please use [CreateTarget(IEnumerable&lt;TargetData&gt;)](targetfamilycreatetarget-method--ienumerable-.md) instead.

 

Creates multiple targets from a collection of [TargetData](targetdata-class.md), and adds it to the target family.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public virtual void CreateTarget (`

          `IEnumerable<TargetData> targets, `

          ` bool createWithoutAddingTests`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*targets*

Collection of [TargetData](targetdata-class.md) objects.

*createWithoutAddingTests*

A flag to create the Target without adding any Tests.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is not an atomic operation - if an exception is thrown while adding the targets, it is possible that only a subset of the targets was added. Typically the targets that were added before the exception. The targets are added in the order provided in the collection.

This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






