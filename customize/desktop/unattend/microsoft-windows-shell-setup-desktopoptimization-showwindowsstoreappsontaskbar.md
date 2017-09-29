---
title: ShowWindowsStoreAppsOnTaskbar
description: ShowWindowsStoreAppsOnTaskbar
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a787937a-433f-4ae5-88a9-0f465cac3e5b
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# ShowWindowsStoreAppsOnTaskbar


`ShowWindowsStoreAppsOnTaskbar` shows Window Store apps on taskbar.

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>true</strong></p></td>
<td><p>Specifies to show Microsoft Store apps on the taskbar.</p></td>
</tr>
<tr class="even">
<td><p><strong>false</strong></p></td>
<td><p>Specifies to not show Microsoft Store apps on the taskbar.</p></td>
</tr>
</tbody>
</table>

 

**Note**  
The default value of **ShowWindowsStoreAppsOnTaskbar** depends on the selected power platform role.

 

**Important**  
It’s recommended that both settings, **GoToDesktopOnSignIn** and **ShowWindowsStoreAppsOnTaskbar**, be set to a consistent value, either both set to **true** or both set to **false**.

 

## Valid Passes


offlineServicing

oobeSystem

specialize

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [DesktopOptimization](microsoft-windows-shell-setup-desktopoptimization.md) | **ShowWindowsStoreAppsOnTaskbar**

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

[GoToDesktopOnSignIn](microsoft-windows-shell-setup-desktopoptimization-gotodesktoponsignin.md)

 

 







