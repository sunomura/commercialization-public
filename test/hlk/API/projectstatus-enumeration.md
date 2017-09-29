---
title: ProjectStatus Enumeration
description: ProjectStatus Enumeration
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: aa44b9c6-74f8-46bc-a730-6dfc5940863b
---

# ProjectStatus Enumeration


The values that define the status of a project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Public Enumeration ProjectStatus`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Enumeration ParameterSetAsDefault`

**C#**

`public enum ProjectStatus`

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
<td><p>NotRunning</p></td>
<td><p>This value represents the project status. If there are no tests running for this project, the status is NotRunning.</p></td>
</tr>
<tr class="even">
<td><p>Passing</p></td>
<td><p>This value represents the project status A project is passing, if all of the tests needed have passed, and there are no tests that are still running.</p></td>
</tr>
<tr class="odd">
<td><p>Running</p></td>
<td><p>This value represents the project status. A project is running if there is at least one related test that is in a running state.</p></td>
</tr>
</tbody>
</table>

 

 

 






