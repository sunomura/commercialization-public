---
title: PackageManager.ExtractSupplementalFiles Method
description: PackageManager.ExtractSupplementalFiles Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 4636fb5f-912f-4e56-9d0f-ef9ba3757c24
---

# PackageManager.ExtractSupplementalFiles Method


This method extracts all the "supplemental files" linked with a submission package.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageManager`

`Dim path As String`

`instance.ExtractSupplementalFiles(path)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub ExtractSupplementalFiles ( _`

          `path As String _`

`) `

**C#**

`public void ExtractSupplementalFiles (`

          `string path`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*path*

     The path under which the supplemental files are to be extracted.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown if *path* is **null** or empty.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






