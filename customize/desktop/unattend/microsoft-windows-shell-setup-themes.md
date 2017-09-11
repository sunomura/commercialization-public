---
title: Themes
description: Themes
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2e12464c-73c5-4b99-9506-d5edb166e839
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 09/01/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Themes


The `Themes` setting includes settings to customize elements of the Windows visual style, including the window glass color, desktop background, and brand icon.

To customize the Windows default theme, you must include the settings: [DesktopBackground](microsoft-windows-shell-setup-themes-desktopbackground.md) and [ThemeName](microsoft-windows-shell-setup-themes-themename.md). You may also optionally include the settings: [BrandIcon](microsoft-windows-shell-setup-themes-brandicon.md), [ScreenSaver](microsoft-windows-shell-setup-themes-screensaver.md), [UWPAppsUseLightTheme](microsoft-windows-shell-setup-themes-uwpappsuselighttheme.md), and [WindowColor](microsoft-windows-shell-setup-themes-windowcolor.md).

In addition to customizing the Windows default theme, you can also create additional custom themes using .theme files. See instructions in the MSDN topic: [Creating and Installing Theme Files](http://go.microsoft.com/fwlink/?LinkId=141343). Theme files can't be used as the Windows default, however, users can choose to apply one of your custom themes from their **Personalization** settings if desired.

## Child Elements


<table>
<colgroup>
<col width="30%" />
<col width="80%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[BrandIcon](microsoft-windows-shell-setup-themes-brandicon.md)</p></td>
<td><p>Specifies the path to a graphic file that is incorporated in the theme preview in the user's <strong>Personalization</strong> settings.</p></td>
</tr>
<tr class="even">
<td><p>[CustomDefaultThemeFile](microsoft-windows-shell-setup-themes-customdefaultthemefile.md)</p></td>
<td><p>This setting is deprecated. To customize the Windows default theme, simply define the [DesktopBackground](microsoft-windows-shell-setup-themes-desktopbackground.md) and [ThemeName](microsoft-windows-shell-setup-themes-themename.md) settings. You may also optionally include the settings: [BrandIcon](microsoft-windows-shell-setup-themes-brandicon.md), [ScreenSaver](microsoft-windows-shell-setup-themes-screensaver.md), [UWPAppsUseLightTheme](microsoft-windows-shell-setup-themes-uwpappsuselighttheme.md), and [WindowColor](microsoft-windows-shell-setup-themes-windowcolor.md).</p>
<div class="alert">
<strong>Note</strong>  
<p>While you can add additional custom themes to a Windows installation using a [.theme file](https://msdn.microsoft.com/en-us/library/bb773190(VS.85).aspx(d=robot)#boot), .theme files can no longer be used as the default theme. Only the elements listed here can be customized in the Windows default theme.</p>
<p></p>
</div>
<div>
 
</div></td>
</tr>

<tr class="odd">
<td><p>[DesktopBackground](microsoft-windows-shell-setup-themes-desktopbackground.md)</p></td>
<td><p>Specifies the path to a graphic file that is used for the desktop background.</p></td>
</tr>
<tr class="even">
<td><p>[ScreenSaver](microsoft-windows-shell-setup-themes-screensaver.md)</p></td>
<td><p>Specifies the path to a screen-saver file.</p>
<div class="alert">
<strong>Note</strong>  
<p>We do not recommend setting this deprecated value. Instead, we recommend using automatic power plans to dim the screen. This can help reduce system power consumption. </p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[ThemeName](microsoft-windows-shell-setup-themes-themename.md)</p></td>
<td><p>Specifies the name of the customized Windows default theme.</p></td>
</tr>
<tr class="odd">
<td><p>[UWPAppsUseLightTheme](microsoft-windows-shell-setup-themes-uwpappsuselighttheme.md)</p></td>
<td><p>Specifies whether dark mode is applied to UWP apps. By default, the classic Windows color mode (light theme) is used. </p></td>
</tr>
<tr class="even">
<td><p>[WindowColor](microsoft-windows-shell-setup-themes-windowcolor.md)</p></td>
<td><p>Specifies the color of the window borders and the color of various other elements in the system, most notably colors in the Start menu, common controls, active-underline for open apps in the taskbar, and Quick Action tiles in the notification area.</p></td>
</tr>
</tbody>
</table>

 

## Valid Configuration Passes


auditSystem

auditUser

oobeSystem

specialize

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | **Themes**

## Applies To


For a list of the supported Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example


The following XML output shows how to set a customized theme.

```
<Themes>
   <ThemeName>Fabrikam Theme</ThemeName>
   <DefaultThemesOff>false</DefaultThemesOff>
   <DesktopBackground>%WINDIR%\web\wallpaper\fabrikam.jpg</DesktopBackground>
   <BrandIcon>%programfiles%\Fabrikam\fabrikam-logo.png</BrandIcon>
   <ScreenSaver>Bubbles.scr</ScreenSaver>
   <UWPAppsUseLightTheme>false</UWPAppsUseLightTheme>
   <WindowColor>Automatic</WindowColor>
</Themes>
```

## Related topics


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md)

 

 







