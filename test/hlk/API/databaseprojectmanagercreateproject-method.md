---
title: DatabaseProjectManager.CreateProject Method
description: DatabaseProjectManager.CreateProject Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a22ca1bf-ec9e-4742-8326-2357626da9fd
---

# DatabaseProjectManager.CreateProject Method


This method creates a new **Project** object and adds it to the project collection.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DatabaseProjectManager`

`Dim projectName As String`

`Dim returnValue As Project`

`returnValue = instance.CreateProject(projectName)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function CreateProject ( _`

          `projectName As String, _`

`) As Project`

**C#**

`public override Project CreateProject (`

          `string projectName,`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*projectName*

     The name to be associated with the project. The name is case-insensitive.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns [Project Class](project-class.md).

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs when the *projectName* parameter is **null**, empty, or there is a failure while creating the **Project** object.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






