---
title: FilterStatus Enumeration
description: FilterStatus Enumeration
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ab72a275-6acd-496a-b67c-c2b3fe85a5e8
---

# FilterStatus Enumeration


This class contains enumeration value that denotes the status of a HCK filter.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As FilterStatus`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Enumeration FilterStatus`

**C#**

`public enum FilterStatus`

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
<td><p>Active</p></td>
<td><p>This enum identifies a filter as being active. When in the active state, a filter will be applied during filter processing against matching test results.</p></td>
</tr>
<tr class="even">
<td><p>Inactive</p></td>
<td><p>This enum identifies a filter as being active. When a filter is inactive the filter will not be applied during filter processing for matching test results.</p></td>
</tr>
<tr class="odd">
<td><p>Test</p></td>
<td><p>This enum identifies a filter as a test filter.</p></td>
</tr>
</tbody>
</table>

 

 

 






