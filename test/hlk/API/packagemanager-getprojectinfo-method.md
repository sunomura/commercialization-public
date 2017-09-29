---
title: PackageManager.GetProjectInfo Method
description: PackageManager.GetProjectInfo Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 02A241F6-BC92-4C5D-BC30-843B7BE58868
---

# PackageManager.GetProjectInfo Method


Gets the [ProjectInfo Class](projectinfo-class.md) for a specific project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public override ProjectInfo GetProjectInfo (`

          `string projectName`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*projectName*

Case-insensitive name of project to load.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns a [ProjectInfo Class](projectinfo-class.md) for the requested project.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






