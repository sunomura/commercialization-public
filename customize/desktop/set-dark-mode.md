---
title: Set dark mode
description: Windows 10, build 1607 exposes a new personalization setting for end users, allowing them to express preference whether to see applications which support the setting in a dark or light mode.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8D954E98-0090-4EB2-9FC7-7CE7B7483AEF
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Set dark mode


This personalization setting for end users allows them to express preference whether to see applications which support the setting in a dark or light mode.

![](images/darkmode1.png)

Many Microsoft first party applications apply the setting and it is easy for you to support the functionality in your UWP applications as well.

![](images/darkmode2.png)![](images/darkmode3.png)

OEMs can customize [themes](https://docs.microsoft.com/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-shell-setup-themes) via Unattend.xml as such:

```
<settings pass=”oobeSystem”> 
        <Themes> 
            <ThemeName>MyOLEDTheme</ThemeName> 
            <DefaultThemesOff>false</DefaultThemesOff> 
            <DesktopBackground>c:\windows\OLEDFriendlyImage.jpg</DesktopBackground> 
            <WindowColor>Lime</WindowColor> 
        </Themes> 
    </settings> 
```

In Windows 10, build 1607, a setting has been added for light/dark mode toggle.

```
<settings pass=”oobeSystem”> 
        <Themes> 
            <ThemeName>MyOLEDTheme</ThemeName> 
            <DefaultThemesOff>false</DefaultThemesOff> 
            <DesktopBackground>c:\windows\OLEDFriendlyImage.jpg</DesktopBackground> 
            <WindowColor>Lime</WindowColor> 
            <UWPAppsUseLightTheme>false</UWPAppsUseLightTheme> 
        </Themes> 
    </settings> 
```

To learn more about customizing Windows themes, see [Themes](https://docs.microsoft.com/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-shell-setup-themes) in the Unattended Windows Setup Reference.

 






