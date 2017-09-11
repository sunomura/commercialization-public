---
title: ThemeName
description: ThemeName
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fbdbc52b-6fe4-4e7a-a9af-17d9cf59cf27
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# ThemeName


`ThemeName` specifies the name of your custom theme.

> [!Note]
> In Windows 10, if you use this (DesktopBackground/ThemeName) setting, you’ll also need to set (ThemeName/DesktopBackground).
 

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>Theme_name</em></p></td>
<td><p>Specifies the name of the customized Windows theme. <em>Theme_name</em> is a string with a maximum length of 259 characters.</p></td>
</tr>
</tbody>
</table>

 

## Valid Configuration Passes


specialize

auditSystem

auditUser

oobeSystem

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [Themes](microsoft-windows-shell-setup-themes.md) | **ThemeName**

## Applies To


For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example


The following XML output shows how to name a customized theme, as well as set the desktop background.

```
<Themes>
   <ThemeName>Fabrikam Theme</ThemeName>
   <DesktopBackground>%WINDIR%\web\wallpaper\fabrikam.jpg</DesktopBackground>
</Themes>
```

## Related topics


[Themes](microsoft-windows-shell-setup-themes.md)

 

 







