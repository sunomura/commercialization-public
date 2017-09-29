---
title: ProjectManager.GetProjectInfo Method
description: ProjectManager.GetProjectInfo Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d19d2af3-020e-4446-8805-8ab407e77e75
---

# ProjectManager.GetProjectInfo Method


This method retrieves information for a specific project. This does not open the project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetProjectInfo(ByVal projectName As String) As ProjectInfo`

**C#**

`public abstract ProjectInfo GetProjectInfo(string projectName);`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ProjectInfo**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






