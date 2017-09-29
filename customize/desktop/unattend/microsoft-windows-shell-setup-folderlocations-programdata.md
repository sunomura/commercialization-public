---
title: ProgramData
description: ProgramData
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 336500cb-0086-40ba-b8cd-409104c2f120
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# ProgramData


`ProgramData` specifies the path to the program-data folder (normally **C:\\ProgramData**). Unlike the **Program Files** folder, this folder can be used by applications to store data for standard users, because it does not require elevated permissions.

**Warning**  
We don’t recommend using this setting, except perhaps in a test environment. The following are known issues:

-   Microsoft Store apps are not supported.

-   If you change the default location of the program-data folders to a volume other than the system volume, you cannot service your image. Any updates, fixes, or service packs may not be applied to the installation.

The path can be on a volume other than the system drive, as long as it meets the following requirements:

-   It must be on an NTFS volume.

-   It can’t point to a drive that has a different copy of Windows on it.

-   It can’t contain any serviceable components.

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>Path_to_program_data_folder</em></p></td>
<td><p>Specifies the path to the program-data folder. <em>Path_to_program_data_folder</em> is a string with a maximum length of 259 characters.</p></td>
</tr>
</tbody>
</table>

 

This string type does not support empty elements. Do not create an empty value for this setting.

## Valid Configuration Passes


oobeSystem

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [FolderLocations](microsoft-windows-shell-setup-folderlocations.md) | **ProgramData**

## Applies To


For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example


The following XML example shows how to set the paths to folder locations.

```
<FolderLocations>
   <ProfilesDirectory>%SYSTEMDRIVE%\Profiles</ProfilesDirectory>
   <ProgramData>%SYSTEMDRIVE%\Programs</ProgramData>
</FolderLocations>
```

## Related topics


[FolderLocations](microsoft-windows-shell-setup-folderlocations.md)

 

 







