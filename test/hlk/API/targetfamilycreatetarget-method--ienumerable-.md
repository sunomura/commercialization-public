---
title: TargetFamily.CreateTarget Method (IEnumerable)
description: TargetFamily.CreateTarget Method (IEnumerable)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8cd69709-0d3d-4cee-a58a-0d3f32211c1a
---

# TargetFamily.CreateTarget Method (IEnumerable)


This method creates a target from a **TargetData** object, and adds it to a target family.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TargetFamily`

`Dim targets As IEnumerable(Of TargetData)`

`instance.CreateTarget(targets)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub CreateTarget ( _`

          `targets As IEnumerable(Of TargetData) _`

`) `

**C#**

`public void CreateTarget (`

          `IEnumerable<TargetData> targets`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*targets*

     The list of test targets to which to add the contents of the [TargetData Class](targetdata-class.md) object.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is not an atomic operation. If an exception is thrown while adding the targets, it is possible that only a subset of the targets was added.

Targets are added in the order provided in the collection.

This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






