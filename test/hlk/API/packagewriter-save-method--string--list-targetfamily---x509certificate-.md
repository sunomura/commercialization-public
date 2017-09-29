---
title: PackageWriter.Save Method (string, List TargetFamily , X509Certificate)
description: PackageWriter.Save Method (string, List TargetFamily , X509Certificate)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: DD25FD9F-0FE6-4327-8C72-A89D4C0D3294
---

# PackageWriter.Save Method (string, List{TargetFamily}, X509Certificate)


Creates and signs an HCK package only containing data in the given target familes.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public void Save (`

          `string packageFile,`

          `List<TargetFamily> targetFamilyList,`

          `X509Certificate certificate`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*packageFile*

Name of file to where the package will be saved.

*targetFamilyList*

List of target families to save.

*certificate*

The certificate to use for signing.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This function can be used for Submission Packages and Update Packages.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






