---
title: Microsoft-Windows-TwinUI
description: Microsoft-Windows-TwinUI
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 62B05D59-7F90-4917-A4E4-90AA21A7A2D8
ms.author: alhopper
ms.date: 09/27/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---
# Microsoft-Windows-TwinUI

The `Microsoft-Windows-TwinUI` component specifies advanced pen settings.

## Ink Workspace

All of Windows Ink Workspace is available above lock. This functionality is off by default for privacy reasons; it is under the control of Windows customers. Once turned on via Settings, the user can utilize pen click functionality to launch Ink Workspace or any of its experiences directly depending on how they have configured their pen clicks. By default on a new system, it is:

* **Single click** – Ink Workspace Home
* **Double click** – Screen Sketch
* **Press and Hold** (only supported on some pens) – Sticky Notes

## In this section

| Topic                                                        | Description                                                                                                |
|:-------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------|
| [CustomProtocol](microsoft-windows-twinui-customprotocol.md) | Specifies that you are using your own advanced Pen settings application.                                   |
| [Hide](microsoft-windows-twinui-hide.md)                     | Specifies whether to hide the Pen shortcut UI in the Pen and Windows Ink Settings page.                    |

## Applies to

To determine whether a component applies to the image you’re building, load your image into Windows SIM and search for the component or setting name. For information on how to view components and settings, see [Configure Components and Settings in an Answer File](https://msdn.microsoft.com/library/windows/hardware/dn915078).

## Set advanced Pen settings using DISM

1. Open a command prompt with administrator privileges.
1. Mount the image. You will need to customize the following example to point to your install.wim directory.

    `dism /mount-wim /wimfile:c:\bootmedia\sources\install.wim /index:1 /MountDir:c:\wim`

1. Enable the feature.

    `Dism /online /Enable-Feature /FeatureName:Microsoft-Windows-Twinui`

1. Commit the change.

    `dism /unmount-wim /MountDir:c:\wim /Commit`

## Set advanced Pen settings app using Windows System Image Manager (WSIM)

1. Open Windows SIM.
1. On the **File** menu, click **Select Windows Image**.
1. In the **Select a Windows Image** dialog box, select the file type in the **Files of type** drop-down list, and then browse to a Windows image( \*.wim) file.
1. If there is more than one type of Windows image in the file, select a specific Windows image in the **Select an Image** box.

    The Windows image file or catalog file appears in the **Windows Image** pane.

1. Click **Open**. If you have not previously opened that Windows image file or have not refreshed the catalog file recently, Windows SIM prompts you to create or re-create the catalog file.
1. In the **Answer File** pane, find the offline services pass that contains the component for the setting that you want to change, in this case Microsoft-Windows-TwinUI.
1. Select the Microsoft-Windows-TwinUI component.
1. In the **Settings** section of the **Properties** pane, provide a value for “oem-app” for [CustomProtocol](microsoft-windows-twinui-customprotocol.md).

 

 






