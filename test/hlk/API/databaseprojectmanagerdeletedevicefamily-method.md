---
title: DatabaseProjectManager.DeleteDeviceFamily Method
description: DatabaseProjectManager.DeleteDeviceFamily Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7df1f655-15a5-4277-9e7b-2e8e5637364c
---

# DatabaseProjectManager.DeleteDeviceFamily Method


This method deletes a named Device Family.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DatabaseProjectManager`

`Dim name As String`

`instance.DeleteDeviceFamily(name)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Sub DeleteDeviceFamily ( _`

          `name As String, _`

`) `

**C#**

`public override  void DeleteDeviceFamily (`

          `string name`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*name*

     The name of the device family to delete.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs when the *name* parameter is **null**, empty, or the device family cannot be removed.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






