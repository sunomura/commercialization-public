---
title: IRunTests.AddTests Method (IEnumerable TestDefinition , bool)
description: IRunTests.AddTests Method (IEnumerable TestDefinition , bool)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 559D9293-B1F9-4C65-B8DA-88684C1FCF77
---

# IRunTests.AddTests Method (IEnumerable{TestDefinition}, bool)

>[!WARNING]
>  This functionality is being deprecated. Please use playlists to create custom test pass lists.

 

For the [TestDefinition](testdefinition-class.md)s given, add new test instances.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`void AddTests (`

          `IEnumerable<TestDefinition> testList,`

          `bool featureDetectionEnabled`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*testList*

     The list of tests to add.

*featureDetectionEnabled*

     Sets whether there must be a feature mapping between the tests being created and the targets they are being added to.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






