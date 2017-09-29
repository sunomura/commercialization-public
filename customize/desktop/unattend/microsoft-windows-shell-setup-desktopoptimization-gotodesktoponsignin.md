---
title: GoToDesktopOnSignIn
description: GoToDesktopOnSignIn
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9b1c02c3-c013-4025-9c23-78801667a338
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# GoToDesktopOnSignIn


`GoToDesktopOnSignIn` specifies to go to the desktop instead of Start Screen when signing in or when all the apps on a screen are closed.

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>true</strong></p></td>
<td><p>Specifies to go to the desktop instead of Start Screen when signing in or when all the apps on a screen are closed.</p></td>
</tr>
<tr class="even">
<td><p><strong>false</strong></p></td>
<td><p>Specifies to go to the Start Screen instead of desktop when signing in or when all the apps on a screen are closed.</p></td>
</tr>
</tbody>
</table>

 

**Note**  
The default value of **GoToDesktopOnSignIn** depends on the selected power platform role.

 

**Important**  
It’s recommended that both settings, **GoToDesktopOnSignIn** and **ShowWindowsStoreAppsOnTaskbar**, be set to a consistent value, either both set to **true** or both set to **false**.

 

## Valid Passes


offlineServicing

oobeSystem

specialize

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [DesktopOptimization](microsoft-windows-shell-setup-desktopoptimization.md) | **GoToDesktopOnSignIn**

## Applies To


For a list of the supported Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example


The following XML output specifies to go to the desktop on sign in and to show Microsoft Store apps on the taskbar.

```
<DesktopOptimization>
     <GoToDesktopOnSignIn>true</GoToDesktopOnSignIn>
     <ShowWindowsStoreAppsOnTaskbar>true</ShowWindowsStoreAppsOnTaskbar>
</DesktopOptimization>
```

## Related topics


[DesktopOptimization](microsoft-windows-shell-setup-desktopoptimization.md)

[ShowWindowsStoreAppsOnTaskbar](microsoft-windows-shell-setup-desktopoptimization-showwindowsstoreappsontaskbar.md)

 

 







