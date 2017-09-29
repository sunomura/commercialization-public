---
title: Machine.GetTestTargets Method (TargetType)
description: Machine.GetTestTargets Method (TargetType)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dbd7feab-8e1f-490a-b24d-bea6dce34d02
---

# Machine.GetTestTargets Method (TargetType)


Retrieves a read-only list of test targets associated with a machine (test computer).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Machine`

`Dim type As TargetType`

`Dim returnValue As ReadOnlyCollection(Of TargetData)`

`returnValue = instance.GetTestTargets(type)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetTestTargets ( _`

          `type As TargetType _`

`) As ReadOnlyCollection(Of TargetData)`

**C#**

`public abstract ReadOnlyCollection<TargetData> GetTestTargets (`

          `TargetType type`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*type*

     The type of test target to search for.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a collection to test targets.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


All test targets associated with this machine and match the type provided are returned; the collection does not filter out targets based on any loaded projects.

In order to identify targets as a part of a loaded project, look at the ProductInstance.Targets property from the Project object.

This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






