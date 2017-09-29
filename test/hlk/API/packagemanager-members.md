---
title: PackageManager Members
description: PackageManager Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3cf902ca-e04a-444b-ae5b-18028ab98893
---

# PackageManager Members


The following table lists the members exposed by the [PackageManager Class](packagemanager-class.md).

## <span id="Public_Constructors"></span><span id="public_constructors"></span><span id="PUBLIC_CONSTRUCTORS"></span>Public Constructors


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
<td><p>PackageManager(String)</p></td>
<td><p>Overloaded.</p></td>
</tr>
</tbody>
</table>

 

## <span id="Public_Fields"></span><span id="public_fields"></span><span id="PUBLIC_FIELDS"></span>Public Fields


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
<td><p>[PackageVersionString](packagemanagerpackageversionstring-field.md)</p></td>
<td><p>The version (string) for the package version that this <strong>PackageManager</strong> can open.</p></td>
</tr>
<tr class="even">
<td><p>[WinBlueVersion](packagemanager-winblueversion-field.md)</p></td>
<td><p>Specifies the version for packages created for WinBlue.</p></td>
</tr>
<tr class="odd">
<td><p>[Win8Version](packagemanager-win8version-field.md)</p></td>
<td><p>Specifies the version for packages created for Win8 (HCK 2.0).</p></td>
</tr>
<tr class="even">
<td><p>[WinThresholdAndRedstoneVersion](winthresholdandredstoneversion-field.md)</p></td>
<td><p>Specifies the version for packages created for Windows 10.</p></td>
</tr>
<tr class="odd">
<td><p>[PackageDownlevelVersions](packagedownlevelversions-field.md)</p></td>
<td><p>A list of downlevel versions that packages can target.</p></td>
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
<td><p><strong>Certificate</strong></p></td>
<td><p>This property represents the certificate used to sign a submission package. This property will be <strong>null</strong> if the package is not signed.</p></td>
</tr>
<tr class="even">
<td><p>ConnectionType</p></td>
<td><p>Overridden. This property represents the connection type for this submission package.</p></td>
</tr>
<tr class="odd">
<td><p>FileName</p></td>
<td><p>This property represents the filename of the submission package that was opened.</p></td>
</tr>
<tr class="even">
<td><p>PackageVersion</p></td>
<td><p>This property represents the package version that this instance of <strong>PackageManager</strong> is able to read.</p></td>
</tr>
<tr class="odd">
<td><p>Version</p></td>
<td><p>This property represents the major version of the Windows HCK Controller. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
</tr>
<tr class="even">
<td><p>VersionString</p></td>
<td><p>This property represents the version of the Windows HCK Controller and its content. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
</tr>
</tbody>
</table>

 

## <span id="Protected_Properties"></span><span id="protected_properties"></span><span id="PROTECTED_PROPERTIES"></span>Protected Properties


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
<td><p>IsDisposed</p></td>
<td><p>This property represents a value indicating whether this object has already freed its resources. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
</tr>
</tbody>
</table>

 

## <span id="Public_Methods"></span><span id="public_methods"></span><span id="PUBLIC_METHODS"></span>Public Methods


### <span id="Public_Methods"></span><span id="public_methods"></span><span id="PUBLIC_METHODS"></span>Public Methods

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
<td><p>[CreateDeviceFamily](packagemanagercreatedevicefamily-method.md)</p></td>
<td><p>Overridden. This method creates a new device family to use.</p></td>
</tr>
<tr class="even">
<td><p>[CreateProject](packagemanagercreateproject-method.md)</p></td>
<td><p>Overridden. This method creates a new project within the submission package.</p></td>
</tr>
<tr class="odd">
<td><p>[DeleteDeviceFamily](packagemanagerdeletedevicefamily-method.md)</p></td>
<td><p>Overridden. This method deletes a device family.</p></td>
</tr>
<tr class="even">
<td><p>[DeleteProject](packagemanagerdeleteproject-method.md)</p></td>
<td><p>Overridden. This method deletes a project from the submission package.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[ExtractDriverPackages](packagemanagerextractdriverpackages-method.md)</p></td>
<td><p>This method extracts all the driver packages linked with a submission package.</p></td>
</tr>
<tr class="odd">
<td><p>[ExtractSupplementalFiles](packagemanagerextractsupplementalfiles-method.md)</p></td>
<td><p>This method extracts all the &quot;supplemental files&quot; linked with a submission package.</p></td>
</tr>
<tr class="even">
<td><p>[GetDeviceFamilies](packagemanagergetdevicefamilies-method.md)</p></td>
<td><p>Overridden. This method retrieves a list of all of the device families used in this submission package.</p></td>
</tr>
<tr class="odd">
<td><p>[GetFeatures](packagemanagergetfeatures-method.md)</p></td>
<td><p>Overridden. This method retrieves the features found within the submission package.</p></td>
</tr>
<tr class="even">
<td><p>[GetFilters](packagemanagergetfilters-method.md)</p></td>
<td><p>Overridden. This method retrieves the filters present in the submission package. Getting filters from a package is not supported.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[GetPlatforms](packagemanagergetplatforms-method.md)</p></td>
<td><p>Gets a collection of all platforms.</p></td>
</tr>
<tr class="odd">
<td><p>[GetProductTypes](packagemanagergetproducttypes-method.md)</p></td>
<td><p>Overridden. This method retrieves the product types found within the package.</p></td>
</tr>
<tr class="even">
<td><p>[GetProject](packagemanagergetproject-method.md)</p></td>
<td><p>Overridden. This method retrieves a Submission from the package that matches projectName.</p></td>
</tr>
<tr class="odd">
<td><p>[GetProjectInfo](packagemanager-getprojectinfo-method.md)</p></td>
<td><p>Gets the [ProjectInfo Class](projectinfo-class.md) for a specific project.</p></td>
</tr>
<tr class="even">
<td><p>[GetProjectInfoList](packagemanagergetprojectinfolist-method.md)</p></td>
<td><p>Overridden. This method retrieves a list containing one ProjectInfo object per Project found in the submission package.</p></td>
</tr>
<tr class="odd">
<td><p>[GetProjectNames](packagemanagergetprojectnames-method.md)</p></td>
<td><p>Overridden. This method retrieves a list of names for projects stored in this package.</p></td>
</tr>
<tr class="even">
<td><p>[GetProjectSummary](packagemanagergetprojectsummary-method.md)</p></td>
<td><p>Gets a collection of ProjectSummary objects for all the projects.</p></td>
</tr>
<tr class="odd">
<td><p>[GetRequirements](packagemanagergetrequirements-method.md)</p></td>
<td><p>Overridden. This method retrieves the requirements found within the submission package.</p></td>
</tr>
<tr class="even">
<td><p>[GetRootMachinePool](packagemanagergetrootmachinepool-method.md)</p></td>
<td><p>Overridden. This method retrieves the root machine pool for this package.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[Sign](packagemanagersign-method.md)</p></td>
<td><p>Sign an existing package.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToString</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[VerifySignature](packagemanagerverifysignature-method.md)</p></td>
<td><p>This method is no longer valid. Use <strong>IOpcFactory</strong> and <strong>CreateDigitalSignatureManager</strong> to detect signatures.</p></td>
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
<td><p>[Dispose](packagemanagerdispose-method.md)</p></td>
<td><p>This method implements the IDisposable interface. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
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

 

 

 






