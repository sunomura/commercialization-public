---
title: BrandIcon
description: BrandIcon
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a214fabd-f51f-4411-a6dc-53f20a6257af
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# BrandIcon


`BrandIcon` specifies the path to a graphic file that appears in the **Personalization** settings to represent a theme.

Themes enable users to customize elements of the Windows visual style, including the window glass color, desktop background, and brand icon.

The icon graphic must be a .png file that is no larger than 240x80 pixels in size.

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>Path_to_icon_file</em></p></td>
<td><p>Specifies the path to the graphic file. <em>Path_to_icon_file</em> is a string that has a maximum length of 1024 characters.</p></td>
</tr>
</tbody>
</table>

 

This string type supports empty elements.

## Valid Configuration Passes


specialize

auditSystem

auditUser

oobeSystem

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [Themes](microsoft-windows-shell-setup-themes.md) | **BrandIcon**

## Applies To


For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example


The following example shows how to set a customized logo to represent a theme.

```
<Themes>
   <ThemeName>Fabrikam Theme</ThemeName>
   <DesktopBackground>%WINDIR%\web\wallpaper\fabrikam.jpg</DesktopBackground>
   <BrandIcon>%programfiles%\Fabrikam\fabrikam-logo.png</BrandIcon>
</Themes>
```

## Related topics


[Themes](microsoft-windows-shell-setup-themes.md)

 

 







