---
title: PackageWriter.ValidateMerge Method
description: PackageWriter.ValidateMerge Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6b3d3e1e-3dff-49c0-9bf0-fb104a9818e3
---

# PackageWriter.ValidateMerge Method


Checks the provided project for errors that would occur while merging with the current package.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

` public IEnumerable<string> ValidateMerge (`

`Project project,`

`out StringCollection errorList,`

`out StringCollection warningList`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*project*

The specified project to merge.

*errorList*

A list that contains any error messages that were output during validation.

*warningList*

A list that contains any warning messages that were output during validation.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns a collection of error messages if the merge is not supported. If the merge is supported then an empty collection is returned.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This method does not merge the project. Use [Merge](packagewritermerge-method.md) to merge the project.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






