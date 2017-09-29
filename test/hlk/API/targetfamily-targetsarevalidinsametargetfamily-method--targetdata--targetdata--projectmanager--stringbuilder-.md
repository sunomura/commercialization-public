---
title: TargetFamily.TargetsAreValidInSameTargetFamily Method (TargetData, TargetData, ProjectManager, StringBuilder)
description: TargetFamily.TargetsAreValidInSameTargetFamily Method (TargetData, TargetData, ProjectManager, StringBuilder)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: BFAE14F7-0ABC-474C-804A-6AF479B7AAB4
---

# TargetFamily.TargetsAreValidInSameTargetFamily Method (TargetData, TargetData, ProjectManager, StringBuilder)


Checks to see if the two [TargetData](targetdata-class.md) objects can be members of the same target family.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`   public static bool TargetsAreValidInSameTargetFamily (`

          `TargetData firstTarget,`

          `TargetData secondTarget,`

          `ProjectManager manager,`

          `StringBuilder builder`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*firstTarget*

First instance of [TargetData](targetdata-class.md) to compare.

*secondTarget*

Second instance of [TargetData](targetdata-class.md) to compare.

*manager*

Instance of [ProjectManager](projectmanager-class.md).

*builder*

String builder that will contain information on any checks that fail.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns true if these two targets are similar enough to be in the same target family; otherwise it returns false.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


There are a number of checks done:

-   The Machine of the targets are in the same machine pool.

-   The Machine of the targets have the same OS Platform.

-   Both targets are the same target type.

-   Both targets have common manufacturer/VID/Ven.

-   Both targets have common driver hash (of all drivers associated with this device, including any upper and lower filters).

-   Both targets have a common INF hash.

-   Both targets have the same bus/enumerator type.

-   Both targets have the same class/subclass.

-   If DX capable, same DX major version.

-   All targets are on unique machines.

If any of the checks fail, the method returns false.

>[!NOTE]
>  
This specifically allows different Device ID, PID (Product Id) or "Dev" and different sub vendor or implementer Ids.

>[!NOTE]
>  
This function populates the event log with additional data if the comparison has failed.

 

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






