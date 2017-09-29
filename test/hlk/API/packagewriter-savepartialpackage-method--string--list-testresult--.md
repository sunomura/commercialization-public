---
title: PackageWriter.SavePartialPackage Method (string, List TestResult )
description: PackageWriter.SavePartialPackage Method (string, List TestResult )
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 13701A4A-D131-4E85-9F5D-68F757834F71
---

# PackageWriter.SavePartialPackage Method (string, List{TestResult})


Creates a debug HCK package only containing data in the given result(s).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public void SavePartialPackage (`

          `string packageFile,`

          `List<TestResult> resultList`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*packageFile*

Name of file to where the package will be saved.

*resultList*

List of results to save.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This function cannot be used for Submission Packages and Update Packages.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






