---
title: IRunTests.RemoveTests Method
description: IRunTests.RemoveTests Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: BF98BA4A-19D9-431D-A921-844663F42576
---

# IRunTests.RemoveTests Method

>[!WARNING]
>  This functionality is being deprecated. Please use playlists to create custom test pass lists.

 

For the [TestDefinition](testdefinition-class.md)s given, this method removes existing test instances.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`void RemoveTests (`

          `IEnumerable<TestDefinition> testList`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*testList*

     The list of tests to remove.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






