---
title: ProjectManager.CreateProject Method
description: ProjectManager.CreateProject Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cfdd06cc-439c-45ac-98c1-33a1df6f5652
---

# ProjectManager.CreateProject Method


This method creates a new project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProjectManager`

`Dim projectName As String`

`returnValue As Project`

`returnValue = instance.CreateProject(projectName)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function CreateProject ( _`

          `projectName As String, _`

`) As Project`

**C#**

`public abstract Project CreateProject (`

          `string projectName`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*projectName*

     The name of the project to create.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns [Project Class](project-class.md).

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


*projectName* is not case sensitive.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






