---
title: CustomDefaultThemeFile
description: CustomDefaultThemeFile
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: bdab4b5b-d51b-41ce-9e68-826b26e58cbd
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# CustomDefaultThemeFile

> [!Important]
> This setting is deprecated. Theme files can no longer be set as the default Windows theme. Instead, customize the following elements of the Windows default theme using Unattend.xml: [DesktopBackground](microsoft-windows-shell-setup-themes-desktopbackground.md), [ThemeName](microsoft-windows-shell-setup-themes-themename.md), [BrandIcon](microsoft-windows-shell-setup-themes-brandicon.md), [ScreenSaver](microsoft-windows-shell-setup-themes-screensaver.md), [UWPAppsUseLightTheme](microsoft-windows-shell-setup-themes-uwpappsuselighttheme.md), and [WindowColor](microsoft-windows-shell-setup-themes-windowcolor.md).

`CustomDefaultThemeFile` specifies the path to a customized theme file. These files may include a .bmp file for customized background.

While you can create additional custom themes by adding .theme files to a Windows installation (using [these instructions](https://msdn.microsoft.com/en-us/library/bb773190(VS.85).aspx(d=robot)#boot)), .theme files can no longer be used as the default theme.

 

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>Path_to_theme_file</em></p></td>
<td><p>Specifies the path to the customized default theme file. <em>Path_to_theme_file</em> is a string with a maximum length of 259 characters.</p>
<p>Theme files have a file name extension of .theme and are text files containing, among other things, pointers to visual resources such as background.</p></td>
</tr>
</tbody>
</table>

 

This string type supports empty elements.

> [!Note] 
> The background color or design must not, in any way, obscure the Windows desktop icons, taskbar, **Start** button, or **Start** menu, or otherwise impair the functionality of the user interface. Users must be able to view and to use the Windows desktop for its intended purpose, which is to provide easy access to icons and to folders.

 

## Valid Configuration Passes


specialize

auditSystem

auditUser

oobeSystem

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [Themes](microsoft-windows-shell-setup-themes.md) | **CustomDefaultThemeFile**

## Applies To


For a list of the supported Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example


The following XML output shows how to set a customized theme.

```
<Themes>
   <CustomDefaultThemeFile>c:\themefiles\theme1.theme</CustomDefaultThemeFile>
   <DefaultThemesOff>false</DefaultThemesOff>
</Themes>
```

## Related topics


[Themes](microsoft-windows-shell-setup-themes.md)

 

 







