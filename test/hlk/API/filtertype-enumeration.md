---
title: FilterType Enumeration
description: FilterType Enumeration
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ddb28d7c-414b-492a-9664-8a0d1673d52e
---

# FilterType Enumeration


This class contains an enumeration that defines the HCK filter type.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As FilterType`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Enumeration FilterType`

**C#**

`public enum FilterType`

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
<td><p>AutoTriage</p></td>
<td><p>This enum identifies a filer as being of type Auto Triage. In this case, the filter provides additional troubleshooting information that can be viewed by the tester. This type of filer does not change the status of the test result. For a failed test result, the test must be rerun until it returns a pass.</p></td>
</tr>
<tr class="even">
<td><p>Contingency</p></td>
<td><p>This enum identifies a filer as being of type Contingency. A contingency is granted to Microsoft partners due to partial hardware or driver implementation issues and once applied it enables failed results to be submitted as if the tests passed.</p></td>
</tr>
<tr class="odd">
<td><p>Errata</p></td>
<td><p>This enum identifies a filer as being of type Errata. This type of filter is applied to tests that fail due to known test issues, and enables failed results to be submitted as if the tests passed.</p></td>
</tr>
</tbody>
</table>

 

 

 






