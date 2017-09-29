---
title: PackageWriter.Save Method (string, List TargetFamily )
description: PackageWriter.Save Method (string, List TargetFamily )
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5305AACE-D76D-4845-B931-529EF90DC205
---

# PackageWriter.Save Method (string, List{TargetFamily})


Creates an HCK package only containing data in the given target families.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public void Save (`

          `string packageFile,`

          `List<TargetFamily> targetFamilyList`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*packageFile*

Name of file to where the package will be saved.

*targetFamilyList*

List of target families to save.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This function can be used for Submission Packages and Update Packages.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






