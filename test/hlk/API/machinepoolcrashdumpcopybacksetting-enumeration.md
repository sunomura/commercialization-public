---
title: MachinePoolCrashDumpCopyBackSetting Enumeration
description: MachinePoolCrashDumpCopyBackSetting Enumeration
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9D6ED30E-4DAA-4870-BCB6-E4F597DAD375
---

# MachinePoolCrashDumpCopyBackSetting Enumeration


Represents the crash dump type setting for a [MachinePool](machinepool-class.md).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public enum MachinePoolCrashDumpCopyBackSetting`

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
<td><p><strong>Unknown</strong></p></td>
<td><p>The setting is non-uniform across the machine pool. This requires the user to explicitly choose a setting.</p></td>
</tr>
<tr class="even">
<td><p><strong>Disable</strong></p></td>
<td><p>Crash dump copy back is disabled.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Full</strong></p></td>
<td><p>Machines in the pool will write out and copy back a full crash dump.</p></td>
</tr>
<tr class="even">
<td><p><strong>Kernel</strong></p></td>
<td><p>Machines in the pool will write out and copy back only the kernel crash dump.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Mini</strong></p></td>
<td><p>Machines in the pool will write out and copy back only the mini dump.</p></td>
</tr>
</tbody>
</table>

 

 

 






