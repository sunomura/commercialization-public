---
title: ProjectFilterResultsDictionary Class
description: ProjectFilterResultsDictionary Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d7a57c10-807a-406c-980e-e6151c82376f
---

# ProjectFilterResultsDictionary Class


This class represents a collection of filter results for the test results in a project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProjectFilterResultsDictionary`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<SerializableAttribute> _`

`Public Class ProjectFilterResultsDictionaryPublic Class ProjectFilterResultsDictionary`

          `Inherits Dictionary(Of TestResult, ReadOnlyCollection(Of IFilterResult))`

**C#**

`[SerializableAttribute]`

`public class ProjectFilterResultsDictionary : Dictionary<TestResult,ReadOnlyCollection<IFilterResult>>`

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

     **System.Collections.Generic.Dictionary**

          **Microsoft.Windows.Kits.Hardware.ObjectModel.ProjectFilterResultsDictionary**

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






