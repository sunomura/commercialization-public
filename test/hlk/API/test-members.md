---
title: Test Members
description: Test Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c77e045d-9511-4432-8a38-1975f4a99032
---

# Test Members


The following table lists the members exposed by the [Test Class](test-class.md).

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
<td><p>[AreFiltersApplied](test-arefiltersapplied-property.md)</p></td>
<td><p>Gets a value indicating whether filters have been applied for this result.</p></td>
</tr>
<tr class="even">
<td><p>[ExecutionState](testexecutionstate-property.md)</p></td>
<td><p>Indicates whether there is an instance of this test that is queued, waiting to be run, or not running.</p></td>
</tr>
<tr class="odd">
<td><p>[InstanceId](testinstanceid-property.md)</p></td>
<td><p>Gets the instance Id.</p></td>
</tr>
<tr class="even">
<td><p>[ManuallyAdded](test-manuallyadded-property.md)</p></td>
<td><p>Gets whether the test was added separate from the feature detection process.</p></td>
</tr>
<tr class="odd">
<td><p>[Status](teststatus-property.md)</p></td>
<td><p>Gets the status of the test.</p></td>
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
<td><p>[AddTests](test-addtests-method.md)</p></td>
<td>This method should not be called.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[DeleteTestResult](testdeletetestresult-method.md)</p></td>
<td><p>This method deletes a specific result.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[FilterMultiDeviceTestGroups](testfiltermultidevicetestgroups-method.md)</p></td>
<td><p>This method removes tests from a list of tests that can be consolidated and returns the consolidated groupings of tests that are compatible.</p></td>
</tr>
<tr class="odd">
<td><p>[GetDefaultTemplateParameters](test-getdefaulttemplateparameters-method.md)</p></td>
<td><p>Gets the template parameters with default value.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[GetMachineRole](testgetmachinerole-method.md)</p></td>
<td><p>This method returns a logical Machine Set.</p></td>
</tr>
<tr class="even">
<td><p>[GetParameters](testgetparameters-method.md)</p></td>
<td><p>This method retrieves a dictionary collection of test parameters, sorted by parameter name.</p></td>
</tr>
<tr class="odd">
<td><p>[GetRequirements](testgetrequirements-method.md)</p></td>
<td><p>This method retrieves the enumerable list of certification requirements that this test verifies.</p></td>
</tr>
<tr class="even">
<td><p>[GetSupportedPlatforms](testgetsupportedplatforms-method.md)</p></td>
<td><p>This method returns a enumerable list of the architectures supported by this certification test.</p></td>
</tr>
<tr class="odd">
<td><p>[GetTestResults](testgettestresults-method.md)</p></td>
<td><p>This method retrieves the list of the test results generated during runs of this certification test.</p></td>
</tr>
<tr class="even">
<td><p>[GetTests](testgettests-method.md)</p></td>
<td><p>This method retrieves a test list.</p></td>
</tr>
<tr class="odd">
<td><p>[GetTestTargets](testgettesttargets-method.md)</p></td>
<td><p>This method retrieves a list of possible test targets for this test.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[QueueTest](testqueuetest-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="even">
<td><p>[RemoveTests](test-removetests-method.md)</p></td>
<td>This method should not be called.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>[SetParameter](testsetparameter-method.md)</p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="even">
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

 

 

 






