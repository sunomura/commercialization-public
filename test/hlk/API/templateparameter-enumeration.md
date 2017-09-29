---
title: TemplateParameter Enumeration
description: TemplateParameter Enumeration
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9C6912BB-5B73-42E8-955F-33AC629D1BC3
---

# TemplateParameter Enumeration


Template parameter option for running tests on a Proxy Client.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public enum TemplateParameter`

## <span id="Members"></span><span id="members"></span><span id="MEMBERS"></span>Members


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Member name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ImagePath</p></td>
<td><p>Relative Image Path of the FFU or WIM file for flashing a new OS image on the Device Under Test.</p></td>
</tr>
<tr class="even">
<td><p>TestPackages</p></td>
<td><p>Test packages to deploy on the Device Under Test.</p></td>
</tr>
<tr class="odd">
<td><p>ForceReflash</p></td>
<td><p>Flag to flash a new OS image on the Device Under Test.</p></td>
</tr>
<tr class="even">
<td><p>MobileDebuggerPort</p></td>
<td><p>Port number to which the Device Under Test will route KD traffic.</p></td>
</tr>
<tr class="odd">
<td><p>ReflashOnFailure</p></td>
<td><p>Reflash the Device Under Test after a failure.</p></td>
</tr>
</tbody>
</table>

 

 

 






