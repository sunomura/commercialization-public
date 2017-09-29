---
title: MachinePool Members
description: MachinePool Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fd327c17-ad6e-4830-967a-cc0932eeb9f9
---

# MachinePool Members


This class represents an abstract pool of machines that are grouped together based on a user intention. It exposes functionality that enables machines to be regrouped among different machine pools and manage the resource pool hierarchy.

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
<td><p><strong>MachinePool</strong></p></td>
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
<td><p><strong>DefaultPool</strong></p></td>
<td><p>This property represents the default pool.</p></td>
</tr>
<tr class="even">
<td><p><strong>Executable</strong></p></td>
<td><p>This property represents a value indicating whether this pool can be used to run tests.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p>This property represents the name of this machine pool.</p></td>
</tr>
<tr class="even">
<td><p><strong>Path</strong></p></td>
<td><p>This property represents the machine pool path.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RootPool</strong></p></td>
<td><p>This property represents a value indicating whether this pool can be used to run tests.</p></td>
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
<td><p><strong>CreateChildPool</strong></p></td>
<td><p>This method creates a child machine pool.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeleteChildPool</strong></p></td>
<td><p>This method deletes a child machine pool that doesn't contain any machines in it.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeleteMachine</strong></p></td>
<td><p>This method deletes the named machine for this machine pool. The machine to be deleted must be a child machine of this pool. Using the <strong>MachinePool.DeleteMachine</strong> method is NOT recommended because it may leave the deleted machine in an unusable state.</p></td>
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
<td><p><strong>GetHashCode</strong></p></td>
<td><p>Overridden. This method retrieves (creates) the hash code for a <strong>MachinePool</strong> object.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetMachines</strong></p></td>
<td><p>This method retrieves the enumerable list of machines contained by this machine pool.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p><strong>MoveMachineTo</strong></p></td>
<td><p>This method moves a machine from one machine pool to another. Moving resource to the root pool will cause an exception.</p></td>
</tr>
<tr class="even">
<td><p><strong>Equality</strong></p></td>
<td><p>This method acts as an Equality operator. The method always returns <strong>false</strong> if either operand is <strong>null</strong>; otherwise, returns <strong>true</strong> or <strong>false</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Inequality</strong></p></td>
<td><p>This method acts as an Inequality operator. The method always returns <strong>false</strong> if either operand is <strong>null</strong>; otherwise, returns <strong>true</strong> or <strong>false</strong>.</p></td>
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

 

## <span id="Enumeration"></span><span id="enumeration"></span><span id="ENUMERATION"></span>Enumeration


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
<td><p><strong>CrashDumpConfigurationSettingName</strong></p></td>
<td><p>Dimension name for crash dump setting</p></td>
</tr>
</tbody>
</table>

 

 

 






