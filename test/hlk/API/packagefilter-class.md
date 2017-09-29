---
title: PackageFilter Class
description: PackageFilter Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 28ae0b9b-1ca0-49ff-9627-ea7881cdc51a
---

# PackageFilter Class


This class represents a submission package filter that's applied for a TaskResult.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageFilter`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<KnownTypeAttribute(GetType(PackageFilterLogNode))> _`

`<KnownTypeAttribute(GetType(PackageFilterConstraint))> _`

`<DataContractAttribute> _`

`Public Class PackageFilter`

               `Implements IFilter`

**C#**

`[KnownTypeAttribute(typeof(PackageFilterLogNode))]`

`[KnownTypeAttribute(typeof(PackageFilterConstraint))]`

`[DataContractAttribute]`

`public class PackageFilter : IFilter`

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

    **Microsoft.Windows.Kits.Hardware.ObjectModel.Submission.PackageFilter**

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






