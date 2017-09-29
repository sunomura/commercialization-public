---
title: Project.GetAllPossibleTests Method
description: Project.GetAllPossibleTests Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 05B4D47F-BDB5-4DA0-97F5-7B0F6B092865
---

# Project.GetAllPossibleTests Method

>[!WARNING]
>  This functionality is being deprecated. Please use playlists to create custom test pass lists.

 

Gets all of the tests that could potentially be added to this Project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public abstract List<TestDefinition> GetAllPossibleTests()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


A list of [TestDefinition](testdefinition-class.md) objects that are applicable to this [Project](project-class.md).

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






