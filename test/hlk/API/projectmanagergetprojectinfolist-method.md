---
title: ProjectManager.GetProjectInfoList Method
description: ProjectManager.GetProjectInfoList Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: aa02f2b3-8902-4333-bec7-c6fe7ec27204
---

# ProjectManager.GetProjectInfoList Method


This method retrieves a list of Project Info classes. This does not open each of the Projects.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProjectManager`

`Dim returnValue As ReadOnlyCollection(Of ProjectInfo)`

`returnValue = instance.GetProjectInfoList`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetProjectInfoList As ReadOnlyCollection(Of ProjectInfo)`

**C#**

`public abstract ReadOnlyCollection<ProjectInfo> GetProjectInfoList ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






