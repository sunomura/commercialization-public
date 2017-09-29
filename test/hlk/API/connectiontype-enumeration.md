---
title: ConnectionType Enumeration
description: ConnectionType Enumeration
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 964fbdc9-449b-4d7e-8f24-6d6e19a807a4
---

# ConnectionType Enumeration


This class contains the enumeration values that describe the connection type or the Logo manager type.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ConnectionType`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Enumeration ConnectionType`

**C#**

`public enum ConnectionType`

## <span id="Members"></span><span id="members"></span><span id="MEMBERS"></span>Members


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Member Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Database</p></td>
<td><p>This enum represents the connection type use to connect to the controller’s database.</p></td>
</tr>
<tr class="even">
<td><p>SubmissionPackage</p></td>
<td><p>This enum identifies the connection type as being use to connect to a new submission package.</p></td>
</tr>
<tr class="odd">
<td><p>UpdatePackage</p></td>
<td><p>This enum identifies the connection type as being used to update an existing package.</p></td>
</tr>
<tr class="even">
<td><p>PartialPackage</p></td>
<td><p>This is a partial package.</p>
<p>Once a package is marked as a partial package, it will always be a partial package; even if merged with a non-partial package. Such packages are not acceptable for submissions.</p></td>
</tr>
</tbody>
</table>

 

 

 






