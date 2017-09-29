---
title: DesktopOptimization
description: DesktopOptimization
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cba4a9f6-23eb-413e-a29b-451bb47dfdb7
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# DesktopOptimization


`DesktopOptimization` specifies display settings that affect the desktop.

## Child Elements


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[GoToDesktopOnSignIn](microsoft-windows-shell-setup-desktopoptimization-gotodesktoponsignin.md)</p></td>
<td><p>Specifies to go to the desktop instead of Start Screen when signing in or when all the apps on a screen are closed.</p></td>
</tr>
<tr class="even">
<td><p>[ShowWindowsStoreAppsOnTaskbar](microsoft-windows-shell-setup-desktopoptimization-showwindowsstoreappsontaskbar.md)</p></td>
<td><p>Specifies to show Microsoft Store apps on the taskbar.</p></td>
</tr>
</tbody>
</table>

 

**Important**  
It’s recommended that both settings, **GoToDesktopOnSignIn** and **ShowWindowsStoreAppsOnTaskbar**, be set to a consistent value, either both set to **true** or both set to **false**.

 

## Valid Passes


offlineServicing

oobeSystem

specialize

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | **DesktopOptimization**

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


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md)

 

 







