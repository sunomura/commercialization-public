---
title: ProjectManager.GetProjectSummary Method
description: ProjectManager.GetProjectSummary Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: bed22024-e227-44e6-b846-cf6418c0fa27
---

# ProjectManager.GetProjectSummary Method


This method retrieves a list of project summaries.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProjectManager`

`Dim returnValue As ReadOnlyCollection(Of ProjectSummary)`

`returnValue = instance.GetProjectSummary`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetProjectSummary() As ReadOnlyCollection(Of ProjectSummary)`

**C#**

`public abstract ReadOnlyCollection<ProjectSummary> GetProjectSummary();`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






