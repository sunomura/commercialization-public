---
title: TargetFamily Methods
description: TargetFamily Methods
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c781c7aa-cc60-4a48-ba7a-f9e8d424d2fa
---

# TargetFamily Methods


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
<td><p>[AddTests](targetfamily-addtests-method.md)</p></td>
<td>Adds the given Tests to this [TargetFamily](targetfamily-class.md).
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[CreateTarget](targetfamilycreatetarget-method.md)</p></td>
<td>Creates a target from a <strong>TargetData</strong> object, and adds it to a target family.
<div class="alert">
<strong>Warning</strong>  Some overloads of this method are being deprecated. Please use [CreateTarget(IEnumerable&lt;TargetData&gt;)](targetfamilycreatetarget-method--ienumerable-.md).
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>[DeleteTarget](targetfamilydeletetarget-method.md)</p></td>
<td><p>This method deletes a test target from a target family.</p></td>
</tr>
<tr class="even">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[GetFeatures](targetfamilygetfeatures-method.md)</p></td>
<td><p>This method retrieves a list of features for this <strong>TargetFamily</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[GetTargets](targetfamilygettargets-method.md)</p></td>
<td><p>This method retrieves a list of test targets that have been assigned to this Device Family.</p></td>
</tr>
<tr class="even">
<td><p>[GetTestResults](targetfamilygettestresults-method.md)</p></td>
<td><p>This method retrieves a list of results for this <strong>TargetFamily</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>[GetTests](targetfamilygettests-method.md)</p></td>
<td><p>This method retrieves a list of all of the tests needed for this <strong>TargetFamily</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[IsValidTarget](targetfamilyisvalidtarget-method.md)</p></td>
<td><p>Checks to see if the TargetData can be a member of this target family.</p></td>
</tr>
<tr class="even">
<td><p>[QueueTest](targetfamilyqueuetest-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="odd">
<td><p>[RemoveTests](targetfamily-removetests-method.md)</p></td>
<td>Removes the given Tests from this [TargetFamily](targetfamily-class.md).
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[SetCommonParameters](targetfamilysetcommonparameters-method.md)</p></td>
<td><p>This method sets all of the parameters with a given name to the same value for all child jobs.</p></td>
</tr>
<tr class="odd">
<td><p>[TargetsAreValidInSameTargetFamily](targetfamliytargetsarevalidinsametargetfamily-method.md)</p></td>
<td><p>This method checks to see if the two [TargetData](targetdata-class.md) objects can be members of the same target family.</p></td>
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
<td><p><strong>Family</strong></p></td>
<td><p>This property represents the <strong>DeviceFamily</strong> object associated with this <strong>TargetFamily</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsValid</strong></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>ProductInstance</strong></p></td>
<td><p>This property represents the <strong>ProductInstance</strong> parent object of this <strong>TargetFamily</strong>.</p></td>
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
<td><p><strong>LockObject</strong></p></td>
<td><p>(Inherited from <strong>NotificationBase</strong>)</p></td>
</tr>
</tbody>
</table>

 

 

 






