---
title: MachinePool Methods
description: MachinePool Methods
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2de694b5-e68c-4e0c-bedd-71c89a257475
---

# MachinePool Methods


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
<td><p><strong>CreateChildPool</strong></p></td>
<td><p>This method creates a child machine pool.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeleteChildPool</strong></p></td>
<td><p>This method deletes a child machine pool that doesn't contain any machines in it.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeleteMachine</strong></p></td>
<td><p>This method deletes the named machine for this machine pool. The machine to be deleted must be a child machine of this pool. Using the <strong>DeleteMachine</strong> method is NOT recommended because it may leave the deleted machine in an unusable state.</p></td>
</tr>
<tr class="even">
<td><p><strong>Equals</strong></p></td>
<td><p>Overloaded. Overridden.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetChildPools</strong></p></td>
<td><p>This method retrieves the enumerable list of child machine pools for this machine pool.</p></td>
</tr>
<tr class="even">
<td><p>[GetConfiguration](machinepoolgetconfiguration-method.md)</p></td>
<td><p>Retrieves the crash dump configuration for all machines in the machine pool.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>Overridden. This method retrieves (creates) the hash code for a <strong>MachinePool</strong> object.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetMachines</strong></p></td>
<td><p>This method retrieves the enumerable list of machines contained by this machine pool.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from Object)</p></td>
</tr>
<tr class="even">
<td><p><strong>MoveMachineTo</strong></p></td>
<td><p>This method moves a machine from one machine pool to another. Moving resource to the root pool will cause an exception.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Equality</strong></p></td>
<td><p>This method acts as an Equality operator. The method always returns <strong>false</strong> if either operand is <strong>null</strong>; otherwise, returns <strong>true</strong> or <strong>false</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Inequality</strong></p></td>
<td><p>This method acts as an Inequality operator. The method always returns <strong>false</strong> if either operand is <strong>null</strong>; otherwise, returns <strong>true</strong> or <strong>false</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToString</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p><strong>SetConfiguration Method</strong></p></td>
<td><p>Sets the crash dump configuration for all machines in the machine pool.</p></td>
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

 

 

 






