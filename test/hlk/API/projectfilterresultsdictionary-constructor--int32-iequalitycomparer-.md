---
title: ProjectFilterResultsDictionary Constructor (Int32, IEqualityComparer)
description: ProjectFilterResultsDictionary Constructor (Int32, IEqualityComparer)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2b67cc7f-d762-4ff3-8bb3-765534699e10
---

# ProjectFilterResultsDictionary Constructor (Int32, IEqualityComparer)


This constructor initializes a new instance of the **ProjectFilterResultsDictionary** class.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim capacity As Integer`

`Dim comparer As IEqualityComparer(Of TestResult)`

`Dim instance As New ProjectFilterResultsDictionary(capacity, comparer)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New ( _`

          `capacity As Integer, _`

          `comparer As IEqualityComparer(Of TestResult) _`

`)`

**C#**

`public ProjectFilterResultsDictionary (`

          `int capacity,`

          `IEqualityComparer<TestResult> comparer`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*capacity*

     The initial number of elements that the dictionary can contain.

*comparer*

     The **System.Collections.Generic.IEqualityComparer** implementation to use when comparing keys, or **null** to use the default EqualityComparer for the type of the key.

 

 






