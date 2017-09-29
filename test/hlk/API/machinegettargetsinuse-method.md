---
title: Machine.GetTargetsInUse Method
description: Machine.GetTargetsInUse Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 18b7ed78-464f-4033-8bde-21b1cefd34c6
---

# Machine.GetTargetsInUse Method


This method retrieves a summary of all of the targets from all of the projects which are still in use by this machine.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overridable Function GetTargetsInUse() As ReadOnlyCollection(Of InUseTargetData)`

**C#**

`public virtual ReadOnlyCollection<InUseTargetData> GetTargetsInUse()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


This method returns a list of all targets that need to be deleted.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Before deleting this machine, all targets returned by this method must first be deleted.

This method returns a structure that indicates targets by name, but it does not open each project and load each target to get this information.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






