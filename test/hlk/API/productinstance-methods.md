---
title: ProductInstance Methods
description: ProductInstance Methods
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c428d97e-5b2f-4799-9445-f8e2e086bca9
---

# ProductInstance Methods


The following table lists the methods exposed by the [ProductInstance Class](productinstance-class.md).

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
<td><p>[AddTests](productinstance-addtests-method.md)</p></td>
<td>Adds the given Tests to this Product Instance.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[CanCreateTarget](productinstancecancreatetarget-method.md)</p></td>
<td><p>This method determines if a target can be created from <strong>TargetData</strong> object provided. The target is not added to the product instance.</p></td>
</tr>
<tr class="odd">
<td><p>[CreateTarget](productinstancecreatetarget-method.md)</p></td>
<td>This method creates a target from <strong>TargetData</strong>, and adds it to this product instance.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[CreateTargetFamily](productinstancecreatetargetfamily-method.md)</p></td>
<td><p>This method creates and adds a target family to the existing product instance, using the supplied <strong>DeviceFamily</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>[DeleteTarget](productinstancedeletetarget-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="even">
<td><p>[DeleteTargetFamily](productinstancedeletetargetfamily-method.md)</p></td>
<td><p>This method deletes a target family.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[FindTargetFromContainer](productinstancefindtargetfromcontainer-method.md)</p></td>
<td><p>This method creates a list of targets containing the specific container ID. There are two special container Ids to consider. The first is the system containerId (00000000-0000-0000-ffff-ffffffffffff). If this is passed in, then the method will return a list with just a single &quot;system&quot; target. The second is a zero-decorated GUID (00000000-0000-0000-0000-000000000000). This is an invalid GUID.</p></td>
</tr>
<tr class="odd">
<td><p>[FindTargetFromDeviceFamily](productinstancefindtargetfromdevicefamily-method.md)</p></td>
<td><p>This method finds a list of target data that matches the family specified.</p></td>
</tr>
<tr class="even">
<td><p>[FindTargetFromId](productinstancefindtargetfromid-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="odd">
<td><p>[FindTargetFromSystem](productinstancefindtargetfromsystem-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="even">
<td><p>[GetFeatures](productinstancegetfeatures-method.md)</p></td>
<td><p>This method retrieves a collection of features detected for this product instance.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[GetMachines](productinstancegetmachines-method.md)</p></td>
<td><p>This method retrieves all of the machines in a Product Instance. Machines are associated with Product Instances via their test targets. To add or remove a machine, you must add or remove the associated test target.</p></td>
</tr>
<tr class="odd">
<td><p>[GetPlaylists](productinstance-getplaylists-method.md)</p></td>
<td><p>Gets the applied playlists for this [ProductInstance](productinstance-class.md).</p></td>
</tr>
<tr class="even">
<td><p>[GetProductTypes](productinstancegetproducttypes-method.md)</p></td>
<td><p>This method attempts to detect product types this product instance belongs to.</p></td>
</tr>
<tr class="odd">
<td><p>[GetTargetFamilies](productinstancegettargetfamilies-method.md)</p></td>
<td><p>This method retrieves an enumerable list of TargetFamilies that expose the product to the system.</p></td>
</tr>
<tr class="even">
<td><p>[GetTargets](productinstancegettargets-method.md)</p></td>
<td><p>This method retrieves an enumerable list of targets that expose the product to the system.</p></td>
</tr>
<tr class="odd">
<td><p>[GetTests](productinstancegettests-method---.md)</p></td>
<td><p>This method retrieves all tests needed for this node.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from Object)</p></td>
</tr>
<tr class="odd">
<td><p>[QueueTest](productinstancequeuetest-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="even">
<td><p>[RemoveTests](productinstance-removetests-method.md)</p></td>
<td>Removes the given Tests from the [ProductInstance](productinstance-class.md).
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>[SetCommonParameters](productinstancesetcommonparameters-method.md)</p></td>
<td><p>This method sets all of the parameters with a given name to the same value for all child jobs.</p></td>
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
<td><p>Finalize</p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>MemberwiseClone</p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
</tbody>
</table>

 

 

 






