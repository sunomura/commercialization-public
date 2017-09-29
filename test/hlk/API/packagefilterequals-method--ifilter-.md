---
title: PackageFilter.Equals Method (IFilter)
description: PackageFilter.Equals Method (IFilter)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 98b988a4-6126-4d4d-ab01-706bd8ddac38
---

# PackageFilter.Equals Method (IFilter)


This method compares two **PackageFilter** instances.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageFilter`

`Dim other As IFilter`

`Dim returnValue As Boolean`

`returnValue = instance.Equals(other)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function Equals ( _`

          `other As IFilter _`

`) As Boolean`

**C#**

`public bool Equals (`

          `IFilter other`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*other*

     The **PackageFilter** to compare.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the two objects are equal; otherwise, **false**.

## <span id="Thread_Saftey"></span><span id="thread_saftey"></span><span id="THREAD_SAFTEY"></span>Thread Saftey


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






