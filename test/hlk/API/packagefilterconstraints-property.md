---
title: PackageFilter.Constraints Property
description: PackageFilter.Constraints Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1459774c-498a-4409-8157-75bd4b5e8dce
---

# PackageFilter.Constraints Property


This property represents the filter constraints for the filter.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageFilter`

`Dim value As ReadOnlyCollection(Of IFilterConstraint)`

`returnValue = instance.Constraints`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataMemberAttribute> _`

`Public Property Constraints As ReadOnlyCollection(Of IFilterConstraint)`

**C#**

`[DataMemberAttribute]`

`public ReadOnlyCollection<IFilterConstraint> Constraints { get; }`

`)`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






