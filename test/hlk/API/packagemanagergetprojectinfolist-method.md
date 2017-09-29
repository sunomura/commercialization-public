---
title: PackageManager.GetProjectInfoList Method
description: PackageManager.GetProjectInfoList Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cb4edad0-218a-427c-9dbf-22bc3df771a9
---

# PackageManager.GetProjectInfoList Method


This method retrieves a list containing one [ProjectInfo Class](projectinfo-class.md) object per Project found in the submission package.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageManager`

`Dim returnValue As ReadOnlyCollection(Of ProjectInfo)`

`returnValue = instance.GetProjectInfoList`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function GetProjectInfoList As ReadOnlyCollection(Of ProjectInfo)`

**C#**

`public override ReadOnlyCollection<ProjectInfo> GetProjectInfoList ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






