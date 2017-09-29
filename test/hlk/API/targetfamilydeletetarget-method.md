---
title: TargetFamily.DeleteTarget Method
description: TargetFamily.DeleteTarget Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 25e3a90a-0c77-412f-96e4-b4fe89b2091f
---

# TargetFamily.DeleteTarget Method


This method deletes a test target from a target family.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TargetFamily`

`Dim targetToDelete As Target`

`instance.DeleteTarget(targetToDelete)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub DeleteTarget ( _`

          `targetToDelete As Target _`

`) `

**C#**

`public abstract void DeleteTarget (`

          `Target targetToDelete`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*targetToDelete*

     The test target to delete.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


All results associated with the target are also deleted.

This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






