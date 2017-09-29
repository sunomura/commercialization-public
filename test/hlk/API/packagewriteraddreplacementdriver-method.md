---
title: PackageWriter.AddReplacementDriver Method
description: PackageWriter.AddReplacementDriver Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6f32eb48-a295-4022-a051-9d8ffbb2cb98
---

# PackageWriter.AddReplacementDriver Method


This method adds driver files to the submission package and checks the driver files for driver signability. This method can only be used for submission packages. It cannot be used for update packages. The signability tests are done when drivers are added to the package. If the signability tests fail the driver is not added to the package. Down level operating system signability tests are automatically run. Errors from these signability results will not prevent submission creation (will not cause a false return value). The error messages for down level operating system signability runs will be captured and returned as warnings.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageWriter`

`Dim pathToNewDriver As String`

`Dim replacesDriverId As String`

`Dim errorMessages As StringCollection`

`Dim warningMessages As StringCollection`

`Dim returnValue As Boolean`

`returnValue = instance.AddReplacementDriver(pathToNewDriver, replacesDriverId, errorMessages, warningMessages)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function AddReplacementDriver ( _`

          `pathToNewDriver As String, _`

          `replacesDriverId As String, _`

          `<OutAttribute> ByRef errorMessages As StringCollection, _`

          `<OutAttribute> ByRef warningMessages As StringCollection _`

`) As Boolean`

**C#**

`public bool AddReplacementDriver (`

          `string pathToNewDriver,`

          `string replacesDriverId,`

          `out StringCollection errorMessages,`

          `out StringCollection warningMessages`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*pathToNewDriver*

     The path to the driver files. All files in this directory and all subdirectories (and their files) will be packaged.

*replacesDriverId*

     The GUID of the driver that this replaces.

*errorMessages*

     Reference to a string collection that will contain all the error messages.

*warningMessages*

     Reference to a string collection that will contain all the warning messages.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the new driver files passed signability; otherwise, **false**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown when:

-   The *pathToDriver* paramteror *replacesDriverIdis* parameter is **null**.

-   The *pathToDriver* parameter or *replacesDriverId* parameter is invalid or if the GUID for *replacesDriverId* was not found.

-   The **PackageWriter** object has already been disposed.

-   The method calls an invalid connection type.

-   The directory does not exist for the *pathToDriver* parameter.

-   The method called for an invalid connection type.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






