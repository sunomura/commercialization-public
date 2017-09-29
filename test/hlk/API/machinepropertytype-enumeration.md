---
title: MachinePropertyType Enumeration
description: MachinePropertyType Enumeration
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 4aa46d4d-cc7a-4dfb-aba2-4869a1a28a70
---

# MachinePropertyType Enumeration


A flag value that indicates whether this machine property is a settable property, or a Non-settable query (for example, ProcessorSpeed).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachinePropertyType`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Enumeration MachinePropertyType`

**C#**

`public enum MachinePropertyType`

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
<td><p><strong>Query</strong></p></td>
<td><p>This Machine Property is a query against the machine itself, and is not settable or configurable.</p></td>
</tr>
<tr class="even">
<td><p><strong>Settable</strong></p></td>
<td><p>This flag indicates that a machine property is settable.</p></td>
</tr>
</tbody>
</table>

 

 

 






