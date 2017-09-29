---
title: Project Members
description: Project Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 45986fe4-075c-4627-901f-0131e877f4d1
---

# Project Members


The following table lists the members exposed by the **Machine** type.

## <span id="Public_Fields"></span><span id="public_fields"></span><span id="PUBLIC_FIELDS"></span>Public Fields


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>OpenedByTag</p></td>
<td><p>This is the value of the string used to indicate the current opener.</p></td>
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
<td><p>CreationTime</p></td>
<td><p>This property represents the creation <strong>DateTime</strong> for this <strong>Project</strong> object. You cannot change this value.</p></td>
</tr>
<tr class="even">
<td><p>Info</p></td>
<td><p>This property represents the project information.</p></td>
</tr>
<tr class="odd">
<td><p>ModifiedTime</p></td>
<td><p>This property represents the <strong>DateTime</strong> that this project was last modified (for example, when targets are created/removed or tests are scheduled). <strong>ModifiedTime</strong> is not updated when tests are completed.</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>This property represents the name of this <strong>Project</strong> object.</p></td>
</tr>
<tr class="odd">
<td><p>ProjectManager</p></td>
<td><p>This property represents the parent Windows HCK Studio object.</p></td>
</tr>
<tr class="even">
<td><p>ServiceLog</p></td>
<td><p>This property represents the service log associated with this project.</p></td>
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
<td><p>(Inherited from <strong>NotificationBase</strong>)</p></td>
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
<td><p>[AddTests](project-addtests-method.md)</p></td>
<td>Adds the given Tests to this Project.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[CanCreateProductInstance](projectcancreateproductinstance-method.md)</p></td>
<td><p>This method validates that a child product instance object can be created but does not add the product instance. This method does not create a <strong>ProductInstance</strong>. A call to <strong>CreateProductInstance</strong> needs to be called to actually create the <strong>ProductInstance</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>[CreateProductInstance](projectcreateproductinstance-method.md)</p></td>
<td><p>This method creates a child <strong>ProductInstance</strong> object.</p></td>
</tr>
<tr class="even">
<td><p>[DeleteProductInstance](projectdeleteproductinstance-method.md)</p></td>
<td><p>This method deletes a <strong>ProductInstance</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>[DeleteProperty](projectdeleteproperty-method.md)</p></td>
<td><p>This method deletes an instance of a names property.</p></td>
</tr>
<tr class="even">
<td><p>Equals</p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[GetAllPossibleTests](project-getallpossibletests-method.md)</p></td>
<td>Gets all of the tests that could potentially be added to this Project.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[GetAppliedFilters](projectgetappliedfilters-method.md)</p></td>
<td><p>This method retrieves a list of filters applied for this submission project.</p></td>
</tr>
<tr class="odd">
<td><p>GetHashCode</p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[GetProductInstances](projectgetproductinstances-method.md)</p></td>
<td><p>This method retrieves a list of product instances.</p></td>
</tr>
<tr class="odd">
<td><p>[GetProperties](projectgetproperties-method.md)</p></td>
<td><p>This method retrieves, a <strong>Dictionary</strong> object with all of the project properties.</p></td>
</tr>
<tr class="even">
<td><p>[GetTests](projectgettests----method.md)</p></td>
<td><p>This method retrieves all tests needed for this node.</p></td>
</tr>
<tr class="odd">
<td><p>GetType</p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[QueueTest](projectqueuetest-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="odd">
<td><p>[RemoveTests](project-removetests-method.md)</p></td>
<td>Removes the given Tests from the Project.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[SetProperty](projectsetproperty-method.md)</p></td>
<td><p>This method updates or creates a new property value.</p></td>
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

 

 

 






