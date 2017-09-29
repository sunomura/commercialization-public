---
title: PackageWriter Members
description: PackageWriter Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a98f4773-89a7-4cdc-8f0e-d9b33dbe9045
---

# PackageWriter Members


The following table lists the members exposed by the [PackageWriter Class](packagewriter-class.md).

## <span id="Public_Constructors"></span><span id="public_constructors"></span><span id="PUBLIC_CONSTRUCTORS"></span>Public Constructors


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>PackageWriter</p></td>
<td><p>Overloaded.</p></td>
</tr>
</tbody>
</table>

 

## <span id="Public_Properties"></span><span id="public_properties"></span><span id="PUBLIC_PROPERTIES"></span>Public Properties


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageVersion</strong></p></td>
<td><p>This property represents the version of the package that this instance of <strong>PackageWriter</strong> will create.</p></td>
</tr>
</tbody>
</table>

 

## <span id="Public_Methods"></span><span id="public_methods"></span><span id="PUBLIC_METHODS"></span>Public Methods


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[AddDriver](packagewriteradddriver-method.md)</p></td>
<td><p>This method adds driver files to the submission package and checks the driver files for driver signability. This method can only be used for submission packages. It cannot be used for update packages. The signability tests are done when drivers are added to the package. If the signability tests fail the driver is not added to the package. Down level operating system signability tests are automatically run. Errors from these signability results will not prevent submission creation (will not cause a false return value).The error messages for down level operating system signability runs will be captured and returned as warnings.</p></td>
</tr>
<tr class="even">
<td><p>[AddReplacementDriver](packagewriteraddreplacementdriver-method.md)</p></td>
<td><p>This method replaces a driver in the submission package. This method can only be used for update packages.</p></td>
</tr>
<tr class="odd">
<td><p>[AddSupplementalFiles](packagewriteraddsupplementalfiles-method.md)</p></td>
<td><p>This method adds all of the files in a specified directory to a submission package. This method can be used for both submission packages and update packages.</p></td>
</tr>
<tr class="even">
<td><p>[Dispose](packagewriterdispose-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[Merge](packagewritermerge-method.md)</p></td>
<td><p>This method merges a project into an existing package. This method can only be used for existing submission packages.</p></td>
</tr>
<tr class="odd">
<td><p>[Save](packagewritersave-method.md)</p></td>
<td><p>Overloaded. This class contains methods used to save a submission package.</p></td>
</tr>
<tr class="even">
<td><p>[SavePartialPackage](packagewriter-savepartialpackage-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="odd">
<td><p>[SetProgressActionHandler](packagewritersetprogressactionhandler-method.md)</p></td>
<td><p>This method sets an action handler that is used to send out submission progress updates. This method can be used for both submission packages and update packages.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToString</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[TargetFamiliesAreDeepMergeCompatible](packagewriter-targetfamiliesaredeepmergecompatible-method.md)</p></td>
<td><p>Checks if two target families are similar enough for deep merging.</p></td>
</tr>
<tr class="even">
<td><p>[ValidateMerge](packagewritervalidatemerge-method.md)</p></td>
<td><p>Checks the provided project for errors that would occur while merging with the current package.</p></td>
</tr>
</tbody>
</table>

 

## <span id="Protected_Methods"></span><span id="protected_methods"></span><span id="PROTECTED_METHODS"></span>Protected Methods


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Dispose](packagewriterdispose-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="even">
<td><p><strong>Finalize</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p><strong>MemberwiseClone</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
</tbody>
</table>

 

 

 






