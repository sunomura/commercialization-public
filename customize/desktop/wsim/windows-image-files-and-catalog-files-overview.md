---
title: Windows Image Files and Catalog Files Overview
description: Windows Image Files and Catalog Files Overview
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9cbc49e7-e962-4d9c-a04e-59b7ed67c278
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Windows Image Files and Catalog Files Overview


Windows System Image Manager (Windows SIM) uses Windows image **(.wim)** files and catalog **(.clg)** files to display the available components and packages that can be added to an answer file (**Unattend.xml**). Windows images and catalog files contain configurable settings that you can modify after the component or package is added to an answer file.

## <a href="" id="supported_architectures"></a> Supported architectures

Windows SIM can create catalog files for Windows images of the following architecture types

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Your version of Windows</th>
<th>Windows images you can create catalog files from</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>x86 version of Windows</p></td>
<td><p>x86-based systems, x64-based systems, and ARM-based systems</p></td>
</tr>
<tr class="even">
<td><p>x64 version of Windows</p></td>
<td><p>x64-based systems only</p></td>
</tr>
</tbody>
</table>

Don't have an x86 PC handy?

* You can install the 32-bit version of Windows on a 64-bit PC. 
* You can install Windows on a 32-bit virtual machine from a 64-bit PC.

## Windows Image Files


A Windows image file contains one or more compressed Windows images. Each Windows image in a Windows image file contains a list of all of the components, settings, and packages that are available with that Windows image.

### Limitations of Windows Image Files

The following list describes some of the limitations of using Windows image files:

-   Only an account that has administrator permissions can open Windows image files.

-   Only one user at a time can open Windows image files.

-   Because Windows image files can contain one or more Windows images, they are frequently large. Some Windows image files can be several gigabytes in size.

-   Because Windows images can be modified through different settings, using a Windows image file to create your answer file might cause you to apply altered default settings and configurations to a recaptured Windows image.

Because of these limitations, Windows SIM uses catalog files to create an answer file.

## Catalog Files


A catalog file is a binary file that only includes the settings and packages in a Windows image. Catalog files (.**clg**) are only used by Windows SIM and is not used by other deployment tools, nor is it required to install Windows. When Windows SIM creates a catalog file, it queries the Windows image for a list of all the settings and state of each setting in that image. Because the contents of a Windows image can change over time, you must re-create the catalog file whenever you update a Windows image.

Because only administrators can open Windows images, you must have administrator permissions on the system to create a catalog file.

When Windows SIM opens a Windows image file or catalog file, all of the configurable components and packages inside that image are displayed in the **Windows Image** pane. You can then add components and settings to an answer file.

### Contents of a Catalog File

A catalog file contains the following information:

-   A list of component settings and current values

-   Windows features and package states

### Benefits of Catalog Files

Catalog files have several advantages over Windows image files:

-   The size of a catalog file can be less than 1 megabyte (MB), whereas the size of Windows image files can be several gigabytes. Also, catalog files are easier to copy to removable media or a network share.

-   Multiple users can create answer files for a single catalog file at the same time, whereas only one person can open and access a Windows image file at any particular time.

-   Non-administrators can create answer files for a catalog file. However, only administrators can open Windows image files.

### Troubleshooting 

-   **"The catalog file for Windows Image (image name) cannot be opened for the following reason:**

    **Cannot find the catalog file associated with the Windows image (image name)**

    **You must have a valid catalog file to continue. Do you want to create a catalog file?"** 

    _Fix:_ Click **Yes** to create a catalog file. After you've created the catalog file, this message will no longer appear.

    _What's going on_: This message usually shows up the first time you open a .wim file. 

    
-   **"Access denied"** 

    _Fix:_ Copy the .wim file to a simple writable file location, like C:\Images, then try again.
    
    _What's going on_: This message appears when you're creating a catalog file from a .wim file that's in a location that the system can't write to, like a DVD or secured network share.

-   **"Catalog creation failed to complete. This 64-bit version of Windows SIM can only create catalogs for 64-bit Windows images. For a list of supported architecture types, see link below."** 

    _Fix:_  Use an x86 version installation of Windows to create catalog files for x86 or ARM-based .wim files. 

    _What's going on_: Windows SIM can't create x86 or ARM catalog files from a 64-bit Windows installation. See [architectures](#supported_architectures).
    

## Related topics


[Open a Windows Image or Catalog File](open-a-windows-image-or-catalog-file.md)

[Windows System Image Manager Overview Topics](windows-system-image-manager-overview-topics.md)

 

 







