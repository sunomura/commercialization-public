---
title: ProjectFilterResultsDictionary Constructor (IEqualityComparer)
description: ProjectFilterResultsDictionary Constructor (IEqualityComparer)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e98cc703-49a6-4fc6-827b-a0181a7f84a5
---

# ProjectFilterResultsDictionary Constructor (IEqualityComparer)


This constructor initializes a new instance of the **ProjectFilterResultsDictionary** class.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim comparer As IEqualityComparer(Of TestResult)`

`Dim instance As New ProjectFilterResultsDictionary(comparer)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New ( _`

          `comparer As IEqualityComparer(Of TestResult) _`

`)`

**C#**

`public ProjectFilterResultsDictionary (`

          `IEqualityComparer<TestResult> comparer`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*comparer*

     The **System.Collections.Generic.IEqualityComparer** implementation to use when comparing keys, or **null** to use the default EqualityComparer for the type of the key.

 

 






