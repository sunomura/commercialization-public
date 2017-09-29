---
title: Target Members
description: Target Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d8338c02-35fb-41c2-b08b-19e8a4ca7d12
---

# Target Members


This class represents an abstract pool of machines that are grouped together based on a user intention. It exposes functionality that enables machines to be regrouped among different machine pools and manage the resource pool hierarchy.

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
<td><p><strong>DriverStatus</strong></p></td>
<td><p>This property represents the driver status of the test target.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsTargetReady</strong></p></td>
<td><p>This property represents the value indicating whether the test target is currently ready to run tests (specifically, the test computer is in the “ready” state).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Key</strong></p></td>
<td><p>This property represents the string that uniquely identifies this test target. In case of a device, for example, this would be the hardware ID.</p></td>
</tr>
<tr class="even">
<td><p><strong>Machine</strong></p></td>
<td><p>This property represents the machine (test computer) that this test target was detected on.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p>This property represents the name of the test target to display to the users.</p></td>
</tr>
<tr class="even">
<td><p><strong>TargetFamily</strong></p></td>
<td><p>This property represents the product instance that this test target is associated with.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TargetType</strong></p></td>
<td><p>This property represents the type of this test target.</p></td>
</tr>
<tr class="even">
<td><p><strong>XmlData</strong></p></td>
<td><p>This property represents the sysparse data associated with this test target.</p></td>
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
<td><p>LockObject</p></td>
<td><p>(Inherited from [NotificationBase Class](notificationbase-class.md))</p></td>
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
<td><p>[AddFeature](targetaddfeature-method.md)</p></td>
<td><p>This method adds a [Feature](feature-class.md).</p></td>
</tr>
<tr class="even">
<td><p><strong>Equals</strong></p></td>
<td><p>Overloaded. Overridden.</p></td>
</tr>
<tr class="odd">
<td><p>[GetDrivers](targetgetdrivers-method.md)</p></td>
<td><p>Gets a list of drivers.</p></td>
</tr>
<tr class="even">
<td><p>[GetFeatures](targetgetfeatures-method.md)</p></td>
<td><p>This method retrieves the list of features that is associated with the [Target](target-class.md).</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[GetTestResults](targetgettestresults-method.md)</p></td>
<td><p>Gets a read-only collection of test results for tests for this [Target](target-class.md).</p></td>
</tr>
<tr class="odd">
<td><p>[GetTests](targetgettests-method.md)</p></td>
<td><p>Gets all tests for this [Target](target-class.md).</p></td>
</tr>
<tr class="even">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[RedistributeScheduledTests](target-redistributescheduledtests-method.md)</p></td>
<td><p>Method to redistribute tests across targets which have been added to a project.</p></td>
</tr>
<tr class="even">
<td><p><strong>RemoveFeature</strong></p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToString</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
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
<td><p><strong>Finalize</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p><strong>MemberwiseClone</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
</tbody>
</table>

 

 

 






