---
title: Preinstalled apps
description: OEMs and Mobile operators can create Partner applications that can be packaged and configured to install during the initial device setup process.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 268d5950-04e6-4450-94a0-a3d902edc7e7
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Preinstalled apps


## Purpose


The primary channel for distributing apps is the Microsoft Store. However, because Microsoft Store apps are only available on the device after a user-initiated download and some partner apps need to be available at first boot, there is an alternate option available for OEMs and mobile operators. OEMs and Mobile operators can create Partner applications that can be packaged and configured to install during the initial device setup process. While the user is going through the initial setup process, the preinstalled applications are installed in the background.

The process for creating a preinstalled app is similar to that of a standard app. An unsigned app package (.appx), generated with the Windows SDK, is submitted to the Windows Dev Center for certification and signing. During the submission process, you can specify that you are submitting a preinstalled app. If the app meets certification requirements, it is processed to create a package that can be downloaded from the Dev Center. The app can then be published to the Microsoft Store as well, so that users who have uninstalled the app can re-download it and updates can later be offered to devices that have the app installed.

## In this section


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Topic</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Preinstallable apps for desktop devices](preinstallable-apps-for-windows-10-desktop.md)</p></td>
<td><p>Learn how to add an app to a Windows 10 for desktop editions (Home, Pro, Enterprise, and Education) image that will be available to customers at first boot.</p></td>
</tr>
<tr class="even">
<td><p>[Preinstallable apps for mobile devices](preinstallable-apps-for-window-10-for-phones.md)</p></td>
<td><p>Learn how to add an app to a mobile image that will be available to customers at first boot.</p></td>
</tr>
<tr class="odd">
<td><p>[Preinstall tasks](preinstall-tasks.md)</p></td>
<td><p>OEMs and MOs are permitted to ship preinstalled apps in the device image. Some of those preinstalled apps require tasks to run without user interaction and often before the end-user opens the app for the first time; such as a product survey app or a SMS server registration. Similarly, some apps will need servicing tasks to run without user interaction after an app has been updated. Preinstall and update tasks provide the mechanism for allowing tasks to run in the background without before the app is installed or when it is updated.</p></td>
</tr>
</tbody>
</table>

 

## <a href="" id="developer-audience-heading"></a>Developer audience


Preinstall is designed for use by OEM and MO developers writing apps to be preinstalled on Windows 10 OS images.

 

 






