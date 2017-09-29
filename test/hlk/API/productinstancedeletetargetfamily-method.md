---
title: ProductInstance.DeleteTargetFamily Method
description: ProductInstance.DeleteTargetFamily Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2b487183-3bfc-450f-8e87-eb40d3fc6470
---

# ProductInstance.DeleteTargetFamily Method


This method deletes a target family.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

`Dim familyToDelete As TargetFamily`

`instance.DeleteTargetFamily(familyToDelete)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub DeleteTargetFamily ( _`

          `familyToDelete As TargetFamily _`

`) `

**C#**

`public abstract void DeleteTargetFamily (`

          `TargetFamily familyToDelete`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*familyToDelete*

     The **TargetFamily** to delete.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs if *familyToDelete* is **null** or not valid, or if an internal storage problem exists (for example, the controller cannot be reached).

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






