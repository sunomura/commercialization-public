---
title: DatabaseProjectManager.DeleteProject Method
description: DatabaseProjectManager.DeleteProject Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 09491599-adae-4b28-8915-06ad818321f7
---

# DatabaseProjectManager.DeleteProject Method


This method deletes a named project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DatabaseProjectManager`

`Dim projectNameToDelete As String`

`instance.DeleteProject(projectNameToDelete)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Sub DeleteProject ( _`

          `projectNameToDelete As String _`

`) `

**C#**

`public override void DeleteProject (`

          `string projectNameToDelete`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*projectNameToDelete*

     The name of the project to delete.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs when the *projectNameToDelete* parameter is **null** or empty.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






