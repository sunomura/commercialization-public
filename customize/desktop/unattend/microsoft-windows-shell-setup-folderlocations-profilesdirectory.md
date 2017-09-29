---
title: ProfilesDirectory
description: ProfilesDirectory specifies the path to the user profile folder (normally C \\Users).
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c43e6bf4-74cb-4a17-9da7-2a44b12a052c
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# ProfilesDirectory


`ProfilesDirectory` specifies the path to the user profile folder (normally **C:\\Users**).

When you use a folder name other than "Users", like `C:\Documents and Settings`, then Windows creates the Users folder on that drive (C:\\Users), and also creates an redirect folder (C:\\Documents and Settings) that points to the Users folder.

## Important usage notes


-   We don’t recommend using this setting, except perhaps in a test environment.

-   When this setting is changed, Microsoft Store apps are not supported.

-   **Using drives other than the system drive:**

    Use this setting to move the user-profile folder (typically %SYSTEMDRIVE%\\Users) to another location during deployment. The destination path can be on a volume other than the system drive, as long as it meets the following requirements:

    -   It must be on an NTFS volume.

    -   It can’t point to a drive that has a different copy of Windows on it.

-   Beginning with Windows 10, OS upgrades are supported even if user profiles have been redirected to another drive. For example, if you are using Windows 7 or Windows 8.1 with `ProfilesDirectory` set to D:\\, you can upgrade to Windows 10.

    However, this is not supported when using push-button reset.

-   This setting can be used to keep system data separate from user data. If Windows is re-installed on the system volume, a user with administrative rights can manually recover data from this location.

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>Path_to_profiles_directory</em></p></td>
<td><p>Specifies the path to the user profile folder. <em>Path_to_profiles_directory</em> is a string with a maximum length of 256 characters.</p></td>
</tr>
</tbody>
</table>

 

This string type does not support empty elements. Do not create an empty value for this setting.

## Valid Configuration Passes


oobeSystem

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [FolderLocations](microsoft-windows-shell-setup-folderlocations.md) | **ProfilesDirectory**

## Applies To


For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example


The following XML example shows how to set the paths to folder locations.

```
<FolderLocations>
   <ProfilesDirectory>%SYSTEMDRIVE%\Profiles</ProfilesDirectory>
   <ProgramData>%SYSTEMDRIVE%\ProgramData</ProgramData>
</FolderLocations>
```

## Related topics


[FolderLocations](microsoft-windows-shell-setup-folderlocations.md)

 

 







