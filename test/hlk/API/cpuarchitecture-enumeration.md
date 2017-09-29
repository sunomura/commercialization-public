---
title: CpuArchitecture Enumeration
description: CpuArchitecture Enumeration
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0dab3246-507f-4c03-9a34-6f1146702788
---

# CpuArchitecture Enumeration


This class contains enumeration values that define the architecture that a test or submission package is applicable to.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As CpuArchitecture`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Enumeration CpuArchitecture`

**C#**

`public enum CpuArchitecture`

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
<td><p>Arm</p></td>
<td><p>This enum value identifies the architecture as ARM.</p></td>
</tr>
<tr class="even">
<td><p>IA64</p></td>
<td><p>This enum value identifies the architecture as Intel ia64 (Itanium 64-bit).</p></td>
</tr>
<tr class="odd">
<td><p>X64</p></td>
<td><p>This enum value identifies the architecture as 64-bit.</p></td>
</tr>
<tr class="even">
<td><p>X86</p></td>
<td><p>This enum value identifies the architecture as 32-bit.</p></td>
</tr>
<tr class="odd">
<td><p>Arm64</p></td>
<td><p>This enum value identifies the architecture as ARM64.</p></td>
</tr>
</tbody>
</table>

 

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


See the Win32 documentation for SYSTEM\_INFO.wProcessorArchitecture.

 

 






