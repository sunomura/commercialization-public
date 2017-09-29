---
title: PackageWriter.Save Method (String)
description: PackageWriter.Save Method (String)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 317273eb-f5af-47d4-9ad2-64c7011af39b
---

# PackageWriter.Save Method (String)


This method saves a submission package to disk.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageWriter`

`Dim packageFile As String`

`instance.Save(packageFile)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub Save ( _`

          `packageFile As String _`

`) `

**C#**

`public void Save (`

          `string packageFile`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*packageFile*

     The file name (including the path) specifying where to write the package.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This method throws an exception when:

-   The *packageFile* parameter is **null**.

-   The *packageFile* parameter is invalid.

-   The **PackageWriter** object has already been disposed.

-   There is an IO exception when the package is being closed.

-   The targets that are mapped to a driver are not found in the projects.

-   The package does not have at least one product instance.

-   There is a problem creating a directory and copying the package to that directory.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






