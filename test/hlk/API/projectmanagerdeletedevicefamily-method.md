---
title: ProjectManager.DeleteDeviceFamily Method
description: ProjectManager.DeleteDeviceFamily Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a345468e-fb2e-4bb6-9c87-e7c1bb62b402
---

# ProjectManager.DeleteDeviceFamily Method


This method deletes a device family by name.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProjectManager`

`Dim name As String`

`instance.DeleteDeviceFamily(name)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub DeleteDeviceFamily ( _`

          `name As String _`

`) `

**C#**

`public abstract void DeleteDeviceFamily (`

          `string name`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*name*

     The name of the device family to delete..

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An error occurs if the device family cannot be located or is in use.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






