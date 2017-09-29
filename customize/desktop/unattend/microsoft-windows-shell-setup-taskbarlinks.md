---
title: TaskbarLinks
description: TaskbarLinks
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 17a5ff39-bed8-4ffa-9f61-0e9a78671b55
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# TaskbarLinks


`TaskbarLinks` specifies shortcuts to display on the taskbar. Up to six shortcuts to programs, Microsoft Store apps or website links can be specified.

**Note**  
Any item that is pinned to the taskbar will not appear in the **Start** menu list of most frequently used programs.

 

Each of the settings under `TaskbarLinks` specifies:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Taskbar Link Type</th>
<th>Format</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Shortcut to programs</p></td>
<td><p>The complete path and the file name of a shortcut file with a .lnk file name extension. The path to the shortcut file must refer to a location on the destination computer.</p></td>
</tr>
<tr class="even">
<td><p>Shortcut to website link</p></td>
<td><p>The complete path and website name of the shortcut file with a .website file name extension. The path to the shortcut file must refer to a location on the destination computer. </p></td>
</tr>
<tr class="odd">
<td><p>Shortcut to a Microsoft Store app</p></td>
<td><p>Use the Application User Model ID (AUMID).</p></td>
</tr>
</tbody>
</table>

 

For shortcuts to programs, each shortcut file must include the complete path and file name of a corresponding program file with an .exe file name extension. The path to the program file must refer to a location on the destination computer.

We recommend that you add shortcut files to the All Users **Start** menu, for example: `%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Fabrikam\Application.lnk`.

We do not recommend adding the shortcut by using the environment variable: `%USERPROFILE%`. Shortcuts added by using `%USERPROFILE%` are applied only to the profile of the next user to log on to the computer. Also, if the setting is applied during the **auditUser** configuration pass, the shortcut is applied only to the temporary administrator account, which is removed after exiting audit mode.

This setting has no effect on Server Core installations.

## Child Elements


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[Link0](microsoft-windows-shell-setup-taskbarlinks-link0.md)</p></td>
<td><p>Specifies the path to the first shortcut.</p></td>
</tr>
<tr class="even">
<td><p>[Link1](microsoft-windows-shell-setup-taskbarlinks-link1.md)</p></td>
<td><p>Specifies the path to the second shortcut.</p></td>
</tr>
<tr class="odd">
<td><p>[Link2](microsoft-windows-shell-setup-taskbarlinks-link2.md)</p></td>
<td><p>Specifies the path to the third shortcut.</p></td>
</tr>
<tr class="even">
<td><p>[Link3](microsoft-windows-shell-setup-taskbarlinks-link3.md)</p></td>
<td><p>Specifies the path to the fourth shortcut.</p></td>
</tr>
<tr class="odd">
<td><p>[Link4](microsoft-windows-shell-setup-taskbarlinks-link4.md)</p></td>
<td><p>Specifies the path to the fifth shortcut.</p></td>
</tr>
<tr class="even">
<td><p>[Link5](microsoft-windows-shell-setup-taskbarlinks-link5.md)</p></td>
<td><p>Specifies the path to the sixth shortcut.</p></td>
</tr>
</tbody>
</table>

 

## Valid Configuration Passes


auditUser

oobeSystem

specialize

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | **TaskbarLinks**

## Applies To


For a list of the supported Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example


The following XML output shows how to set a shortcut for Wordpad, a shortcut to Sound Recorder, a shortcut to a Microsoft Store app with an AUMID of AppID1 and a shortcut to the Bing website.

```
<TaskbarLinks>
   <Link0>%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Accessories\Wordpad.lnk</Link0>
   <Link1>%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Accessories\Sound Recorder.lnk</Link1>
   <Link2>AppID1</Link2>
   <Link3>%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Websites\Bing.website</Link3>
</TaskbarLinks>
```

## Related topics


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md)

 

 







