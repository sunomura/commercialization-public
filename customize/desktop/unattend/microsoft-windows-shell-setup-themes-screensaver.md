---
title: ScreenSaver
description: ScreenSaver
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 49a2e156-f277-4f3b-9d92-d630bb510143
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# ScreenSaver


> [!Important]
> In Windows 10 version 1607, ScreenSaver is deprecated. We do not recommend setting this deprecated value. Instead, we recommend using automatic power plans to dim the screen. This can help reduce system power consumption. 

`ScreenSaver` specifies the path to a Windows screen saver file in a theme.

 

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>Screen_saver_file</em></p></td>
<td><p>Specifies the name of the screen saver file. <em>Screen_saver_file</em> is a string with a maximum length of 256 characters.</p></td>
</tr>
</tbody>
</table>

 

## Valid Configuration Passes


specialize

auditSystem

auditUser

oobeSystem

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [Themes](microsoft-windows-shell-setup-themes.md) | **ScreenSaver**

## Applies To


For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## Related topics


[Themes](microsoft-windows-shell-setup-themes.md)

 

 







