---
title: PackageFilter.LogNodes Property
description: PackageFilter.LogNodes Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5de6abcc-5054-4e6f-b8a7-c96fdf0d3683
---

# PackageFilter.LogNodes Property


This property represents the filter log nodes for the filter.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageFilter`

`Dim value As ReadOnlyCollection(Of IFilterLogNode)`

`value = instance.LogNodes`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataMemberAttribute> _`

`Public Property LogNodes As ReadOnlyCollection(Of IFilterLogNode)`

**C#**

`[DataMemberAttribute]`

`public ReadOnlyCollection<IFilterLogNode> LogNodes { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






