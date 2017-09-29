---
title: DatabaseProjectManager Members
description: DatabaseProjectManager Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: aa2c967e-3fd1-4e22-8e84-d2d259b0210f
---

# DatabaseProjectManager Members


The following tables list the members exposed by the [DatabaseProjectManager Class](databaseprojectmanager-class.md).

## <span id="Protected_Constructors"></span><span id="protected_constructors"></span><span id="PROTECTED_CONSTRUCTORS"></span>Protected Constructors


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
<td><p><strong>DatabaseProjectManager</strong></p></td>
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
<td><p>ConnectionType</p></td>
<td><p>Overridden. This property represents the underlying database connection type.</p></td>
</tr>
<tr class="even">
<td><p>[ControllerName](databaseprojectmanager-controllername-property.md)</p></td>
<td><p>The name of the controller.</p></td>
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
<td><p>[CreateDeviceFamily](databaseprojectmanagercreatedevicefamily-method.md)</p></td>
<td><p>Overridden. This method creates a new device family with the given name.</p></td>
</tr>
<tr class="even">
<td><p>[CreateProject](databaseprojectmanagercreateproject-method.md)</p></td>
<td><p>Overridden. This method creates a new Project and adds it to the project collection.</p></td>
</tr>
<tr class="odd">
<td><p>[DeleteDeviceFamily](databaseprojectmanagerdeletedevicefamily-method.md)</p></td>
<td><p>Overridden. This method deletes a named Device Family.</p></td>
</tr>
<tr class="even">
<td><p>[.DeleteProject](databaseprojectmanagerdeleteproject-method.md)</p></td>
<td><p>Overridden. This method deletes a named project.</p></td>
</tr>
<tr class="odd">
<td><p>[Dispose](databaseprojectmanagerdispose-method.md)</p></td>
<td><p>This method implements the IDisposable interface. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
</tr>
<tr class="even">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[GetDeviceFamilies](databaseprojectmanagergetdevicefamilies-method.md)</p></td>
<td><p>Overridden. This method retrieves a list of available DeviceFamilies.</p></td>
</tr>
<tr class="even">
<td><p>[GetFeatures](databaseprojectmanagergetfeatures-method.md)</p></td>
<td><p>Overridden. This method features all of the features stored in the Windows HCK.</p></td>
</tr>
<tr class="odd">
<td><p>[GetFilters](databaseprojectmanagergetfilters-method.md)</p></td>
<td><p>Overridden. This method returns all the filters installed in the system.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[GetNetBiosName](databaseprojectmanager-getnetbiosname-method.md)</p></td>
<td><p>Converts a FQDN name to a NetBIOS name.</p></td>
</tr>
<tr class="even">
<td><p>[GetPlatforms](databaseprojectmanagergetplatforms-method.md)</p></td>
<td><p>Overridden.</p></td>
</tr>
<tr class="odd">
<td><p>[GetProductTypes](databaseprojectmanagergetproducttypes-method.md)</p></td>
<td><p>Overridden.</p></td>
</tr>
<tr class="even">
<td><p>[GetProject](databaseprojectmanagergetproject-method.md)</p></td>
<td><p>Overridden. This method loads an existing project into the collection.</p></td>
</tr>
<tr class="odd">
<td><p>[GetProjectInfo](databaseprojectmanager-getprojectinfo-method.md)</p></td>
<td><p>Gets the [ProjectInfo Class](projectinfo-class.md) for a specific project.</p></td>
</tr>
<tr class="even">
<td><p>[GetProjectInfoList](databaseprojectmanagergetprojectinfolist-method.md)</p></td>
<td><p>Overridden. This method retrieves a list of project information.</p></td>
</tr>
<tr class="odd">
<td><p>[GetProjectNames](databaseprojectmanagergetprojectnames-method.md)</p></td>
<td><p>Overridden. This method retrieves a list of project names.</p></td>
</tr>
<tr class="even">
<td><p>[GetProjectSummary](databaseprojectmanagergetprojectsummary-method.md)</p></td>
<td><p>Overridden.</p></td>
</tr>
<tr class="odd">
<td><p>[GetRequirements](databaseprojectmanagergetrequirements-method.md)</p></td>
<td><p>Overridden. This method retrieves the list of requirements in the Windows HCK.</p></td>
</tr>
<tr class="even">
<td><p>[GetRootMachinePool](databaseprojectmanagergetrootmachinepool-method.md)</p></td>
<td><p>Overridden. This method retrieves the root machine pool.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from Object)</p></td>
</tr>
<tr class="even">
<td><p><strong>ToString</strong></p></td>
<td><p>(Inherited from Object)</p></td>
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
<td><p>Dispose</p></td>
<td><p>Overridden. This method implements the <strong>IDisposable</strong> interface.</p></td>
</tr>
<tr class="even">
<td><p><strong>Finalize</strong></p></td>
<td><p>This method finalizes an instance of the <strong>ProjectManager</strong> class. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
</tr>
<tr class="odd">
<td><p><strong>MemberwiseClone</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
</tbody>
</table>

 

 

 






