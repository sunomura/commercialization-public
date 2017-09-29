---
title: IRunTests.AddTests Method (IEnumerable TestDefinition )
description: IRunTests.AddTests Method (IEnumerable TestDefinition )
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: A661C62C-049D-4C9C-95D1-7D73A933FA7A
---

# IRunTests.AddTests Method (IEnumerable{TestDefinition})

>[!WARNING]
>  This functionality is being deprecated. Please use playlists to create custom test pass lists.

 

For the [TestDefinition](testdefinition-class.md)s given, add new test instances.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`void AddTests (`

          `IEnumerable<TestDefinition> testList`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*testList*

     The list of tests to add.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






