---
title: TestResult Members
description: TestResult Members
MS-HAID:
- 'bd07c4c0-73e3-4401-92df-1f1d6cf2dac4'
- 'p\_hlk\_om.testresult\_members'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d78399bc-9ed7-4f13-9717-1eb37831794c
---

# TestResult Members


The following table lists the members exposed by the [TestResult Class](testresult-class.md).

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
<td><p>[AreFiltersApplied](testresult-arefiltersapplied-property.md)</p></td>
<td><p>Indicates whether filters have been applied for this result.</p></td>
</tr>
<tr class="even">
<td><p>[CompletionTime](testresultcompletiontime-property.md)</p></td>
<td><p>This property represents the time when the corresponding certification test completed.</p></td>
</tr>
<tr class="odd">
<td><p>[HasBugchecked](testresult-hasbugchecked-property.md)</p></td>
<td><p>Indicates whether a bugcheck occurred on the client machine during the test run.</p></td>
</tr>
<tr class="even">
<td><p>[InstanceId](testresultinstanceid-property.md)</p></td>
<td><p>This property represents the instance ID value of the test result.</p></td>
</tr>
<tr class="odd">
<td><p>[IsMultiDevice](testresult-ismultidevice-property.md)</p></td>
<td><p>Indicates whether the test ran as a MultiDevice test.</p></td>
</tr>
<tr class="even">
<td><p>[Machine](testresultmachine-property.md)</p></td>
<td><p>This property represents the machine (test computer) on which this test ran.</p></td>
</tr>
<tr class="odd">
<td><p>[ScheduleTime](testresultscheduletime-property.md)</p></td>
<td><p>This property represents the time when the corresponding logo test was first scheduled.</p></td>
</tr>
<tr class="even">
<td><p>[StartTime](testresultstarttime-property.md)</p></td>
<td><p>This property represents the time when the corresponding certification test was started and this result was generated.</p></td>
</tr>
<tr class="odd">
<td><p>[Status](testresultstatus-property.md)</p></td>
<td><p>This property represents the status of this certification test result.</p></td>
</tr>
<tr class="even">
<td><p>[Target](testresulttarget-property.md)</p></td>
<td><p>This property represents the test target that this test result was obtained from.</p></td>
</tr>
<tr class="odd">
<td><p>[Test](testresulttest-property.md)</p></td>
<td><p>This property represents the certification test object this result is generated for.</p></td>
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
<td><p>[Cancel](testresultcancel-method.md)</p></td>
<td><p>This method cancels a job that is scheduled.</p></td>
</tr>
<tr class="even">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[GetAllTests](testresult-getalltests-method.md)</p></td>
<td><p>Returns all tests consolidated for multi-device tests.</p></td>
</tr>
<tr class="even">
<td><p>[GetAppliedFilters](testresultgetappliedfilters-method.md)</p></td>
<td><p>This method retrieves the filters applied for this test result.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[GetLogs](testresultgetlogs-method.md)</p></td>
<td><p>This method retrieves all of the logs associated with this test result.</p></td>
</tr>
<tr class="odd">
<td><p>[GetParameters](testresultgetparameters-method.md)</p></td>
<td><p>This method retrieves the parameters that were applied to a test when it was run.</p></td>
</tr>
<tr class="even">
<td><p>[GetTasks](testresultgettasks-method.md)</p></td>
<td><p>This method retrieves the tasks associated with this test.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[Refresh](testresultrefresh-method.md)</p></td>
<td><p>Refresh the current status of the result.</p></td>
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

 

 

 






