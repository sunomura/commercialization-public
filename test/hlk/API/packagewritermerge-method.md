---
title: PackageWriter.Merge Method
description: PackageWriter.Merge Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c1abca6a-0621-4acd-92ca-1bd8fa377206
---

# PackageWriter.Merge Method


This method merges a project into an existing package. This method can only be used for existing submission packages.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageWriter`

`project As Project`

`Dim errors As StringCollection`

`Dim returnValue As Boolean`

`returnValue = instance.Merge(project, errors)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function Merge ( _`

          `project As Project, _`

          `<OutAttribute> ByRef errors As StringCollection _`

`) As Boolean`

**C#**

`public bool Merge (`

          `Project project,`

          `out StringCollection errors`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*project*

     The project to merge into the submission package being created.

*errors*

     Reference to a string collection that returns error messages for merging a project.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the project was successfully merged into the package; otherwise, **false**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown when:

-   The **PackageWriter** object has already been disposed.

-   The *project* parameter is **null**.

-   The connection type of the project is not a submission package.

-   There are problems with merging the project or if the **PackageWriter** object is for a DUA package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






