---
title: Customize the taskbar
description: Customize the taskbar
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 23839EDA-AB63-432A-AEC7-A9741AFB15E5
ms.author: alhopper
ms.date: 08/22/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Customize the taskbar


You can pin up to three additional apps to the taskbar. There are two methods to do this:

-   **Taskar Layout Modification XML** method (recommended)
    -   Supports multivariant images; you can specify different sets of taskbar layouts for different regions.
    -   Uses a single XML file.
    -   Is the only method that allows you to add UWP apps to the taskbar.
    -   In the examples below, the file name “TaskbarLayoutModification.xml” is used, however, you can choose any name you like.

-   **Classic Unattend method** (still supported in Windows 10, but marked as deprecated, and may not be available in future builds)
    -   Uses the Unattend setting: [TaskbarLinks](https://docs.microsoft.com/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-shell-setup-taskbarlinks)

## Taskbar links and ordering

The taskbar starts with the following links: **Start**, **Search**, and **Task View**, plus four additional Windows-provided links: Mail, Edge, File Explorer, and Store. These pins cannot be removed or replaced. 

OEMs can add up to three additional pinned apps to the taskbar.

For left-to-right languages, the taskbar icons are ordered from left to right (Start, Search, Task View, Windws-provided Pins, OEM-provided pins, Mail).
For right-to-left languages, the taskbar icons are in the opposite order, with the right-most element being **Start**.

## Add a default path

To use a Taskbar Layout Modification XML file in Windows, you’ll need to add a registry key (LayoutXMLPath) to the image, and then generalize and recapture the image. The registry key must be processed before the specialize configuration pass. This means you won’t be able to simply add the registry key by using Synchronous Commands/FirstLogonCommands unless you plan to generalize the image afterwards. 

You can use any name or file location by defining this in the registry key; the filename and path to TaskbarLayoutModification.xml is not required. The other shortcut files, apps, and the Taskbar Layout Modification file itself can be changed at any time through regular imaging techniques. You can add this registry key to all your images, even if you intend to add taskbar links using the Classic Unattend method. 

## Customize the taskbar

1.  Install the Windows image to a technician computer.
2.	After the image boots, go into audit mode by pressing CTRL+SHIFT+F3.
3.	Add the following registry key to define a default location for the Taskbar Layout Modification file: `cmd /c reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ /v LayoutXMLPath /d C:\Windows\Fabrikam\TaskbarLayoutModification.xml`
4.	Add a Taskbar Layout Modification file (TaskbarLayoutModification.xml) in the default location for example: `C:\Windows\Fabrikam\TaskbarLayoutModification.xml`
    ```
    <?xml version="1.0" encoding="utf-8"?>
    <LayoutModificationTemplate
    xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"
    xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout"
    xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout"
    xmlns:taskbar="http://schemas.microsoft.com/Start/2014/TaskbarLayout"
    Version="1">

    <CustomTaskbarLayoutCollection PinListPlacement="Replace">
        <defaultlayout:TaskbarLayout>
            <taskbar:TaskbarPinList>
                <taskbar:UWA AppUserModelID="Microsoft.Windows.Photos_8wekyb3d8bbwe!App" />
                <taskbar:DesktopApp DesktopApplicationLinkPath="%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Accessories\Paint.lnk"/>
            </taskbar:TaskbarPinList>
        </defaultlayout:TaskbarLayout>
        <defaultlayout:TaskbarLayout Region="US|GB">
            <taskbar:TaskbarPinList >
                <taskbar:DesktopApp DesktopApplicationLinkPath="%APPDATA%\Microsoft\Windows\Start Menu\Programs\Accessories\Notepad.lnk" />
                <taskbar:UWA AppUserModelID="Microsoft.WindowsCalculator_8wekyb3d8bbwe!App" />
            </taskbar:TaskbarPinList>
        </defaultlayout:TaskbarLayout>
        <defaultlayout:TaskbarLayout Region="CN|TW">
            <taskbar:TaskbarPinList>
                <taskbar:DesktopApp DesktopApplicationLinkPath="%APPDATA%\Microsoft\Windows\Start Menu\Programs\Accessories\Notepad.lnk" />
                <taskbar:UWA AppUserModelID="Microsoft.Windows.Photos_8wekyb3d8bbwe!App" />
                <taskbar:DesktopApp DesktopApplicationLinkPath="%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Accessories\Paint.lnk"/>
            </taskbar:TaskbarPinList>
        </defaultlayout:TaskbarLayout>
    </CustomTaskbarLayoutCollection>
    </LayoutModificationTemplate>
    ```

5.  Generalize the Windows image using [Sysprep](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/sysprep--system-preparation--overview):
    ```
    Sysprep /generalize /oobe /shutdown
    ```

6.	Boot to Windows PE.
7.	Recapture the image. For example:
    ```
    Dism /Capture-Image /CaptureDir:C:\ /ImageFile:c:\install-with-new-taskbar-layout.wim /Name:"Windows image with Taskbar layout"
    ```

8.	You can now apply this image to other PCs.

### To reference your apps

-   For **Classic Windows applications**, use shortcut (.lnk) files. We recommend using the same shortcut .lnk files in the All Users Start menu. Example:
    ```
    DesktopApp 
    DesktopApplicationLinkPath="%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Accessories\Paint.lnk"
    ```

-   For **Universal Windows apps**, use the Universal Windows app user model ID. Example:
    ```
    UWA AppUserModelID="Microsoft.Windows.Photos_8wekyb3d8bbwe!App"
    ```

> [!Note]  
> Links to .url files are not supported.

### To use different layouts for different regions

To use different layouts for different regions, include a region in the defaultlayout tag. These regions use the second half of the language/region tags listed in [Available Language Packs for Windows](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/available-language-packs-for-windows). You can use multiple region tags separated by a pipe (|) character. Here is an example of adding pins to the Chinese (PRC) and Chinese (Taiwan) regions: 

```
<defaultlayout:TaskbarLayout Region="CN|TW">
```

## How Windows parses the setting for Unattend and Taskbar Layout Modification XML

While you’re transitioning to the new method to customize the taskbar, you may end up using existing images that still include your old Unattend TaskbarLinks settings. When that happens: 

1.  If Windows finds a valid Taskbar Layout Modification XML file, it uses the XML file, and ignores any of the Unattend taskbar settings.
2.  If the Taskbar Layout Modification XML file isn't found, or is invalid, Windows looks for the old Unattend TaskbarLinks settings. If it finds them, it uses them.
3.  If Windows can't find either a valid Taskbar Layout Modification XML file, or Unattend TaskbarLink settings, then only the Windows-provided pins and **Start**, **Search**, and **Task View** are shown.

## Set transparency for the taskbar

The default transparency setting for the taskbar is 15%. To make Taskbar work with the Dark Mode on OLED displays, you need to set the taskbar transparency to 40%. 

To set the transparency for the Taskbar, create a registry key called “UseOLEDTaskbarTransparency” and place it in the following location:

```
HKLM\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced
```

> [!Important]  
> This registry key should only be used to change the taskbar transparency for OLED screens. We do not advise changing the default transparency on non-OLED displays.







