---
title: Present Validation 2 (FullScreen) (WoW64)
description: Present Validation 2 (FullScreen) (WoW64)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c1b1b28a-32fe-4145-b2c6-59708fc44996
---

# <span id="p_hlk_test.a2e0db44-2ac8-49fb-bf5a-fe321bbfc1a2"></span>Present Validation 2 (FullScreen) (WoW64)


This automated test verifies that all modes that the **EnumAdapterModes** method reports for the device are available to applications.

The test uses the following parameters: back buffer format, screen resolution, present intervals, swap effects, and multisample types.

The DoNotWait test calls the swap chain's **Present** method in a loop, passes the **D3DPRESENT\_DONOTWAIT** option (in full-screen mode), and uses the **D3DPRESENT\_INTERVAL\_ONE** value. As a result, the driver's queue of frames will exceed the allowed maximum of three. The DoNotWait test expects the driver to return control to the application by using the **D3DERR\_WASSTILLDRAWING** error code. If the error code is not returned, the test fails.

The LockDoNotWait test is similar to the DoNotWait test but occurs on a surface (the back buffer). The same behavior is expected of the driver. If the error code is not returned, the test fails.

This topic applies to the following test jobs:

-   Present Validation 2 (FullScreen)

-   Present Validation 2 (FullScreen) (WoW64)

## <span id="Test_details"></span><span id="test_details"></span><span id="TEST_DETAILS"></span>Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Specifications</strong></td>
<td><ul>
<li>Device.Graphics.AdapterRender.MinimumDirectXLevel</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
<li>Windows 10 for desktop editions (Home, Pro, Enterprise, and Education) x64</li>
<li>Windows Server 2016 x64</li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>Supported Releases</strong></td>
<td><ul>
<li>Windows 10</li>
<li>Windows 10, version 1511</li>
<li>Windows 10, version 1607</li>
<li>Windows 10, version 1703</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Expected run time (in minutes)</strong></td>
<td>9</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Compatibility</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>540</td>
</tr>
<tr class="odd">
<td><strong>Requires reboot</strong></td>
<td>false</td>
</tr>
<tr class="even">
<td><strong>Requires special configuration</strong></td>
<td>false</td>
</tr>
<tr class="odd">
<td><strong>Type</strong></td>
<td>automatic</td>
</tr>
</tbody>
</table>

 

## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Graphics additional documentation](device-graphics-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Graphic Adapter or Chipset Testing Prerequisites](graphic-adapter-or-chipset-testing-prerequisites.md).

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting Device.Graphics Testing](troubleshooting-devicegraphics-testing.md).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


The test displays on-screen pass-or-fail compliance and writes the results to a log file that is named Present2.xml. Present2.xml is written to the %windir%\\dxlogs directory.

If the call to the **Reset** method fails, you can check the values that the test used for the back buffer format and size in the log file. If the image comparison fails, the test prints the image-comparison statistics, just like the other Present Validation tests in the group.

The following table lists the image surfaces that the test uses. If you specify the **-Save** command option, the test saves these files.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Texture.dds</p></td>
<td><p>The texture that is used to fill the quad that is used in <strong>Present</strong> operations.</p></td>
</tr>
<tr class="even">
<td><p>SourceSurface.bmp</p></td>
<td><p>The source surface in the back buffer. For full-screen <strong>Present</strong> operations, this surface is the whole buffer.</p></td>
</tr>
<tr class="odd">
<td><p>DestSurface.bmp</p></td>
<td><p>The destination surface in the front buffer. For full-screen <strong>Present</strong> operations, this surface is the whole buffer.</p></td>
</tr>
<tr class="even">
<td><p>RefSurface.bmp</p></td>
<td><p>The reference surface, as computed by the Microsoft® Direct3D® API.</p></td>
</tr>
<tr class="odd">
<td><p>DiffSurface.bmp</p></td>
<td><p>The difference between the front buffer and the reference image.</p></td>
</tr>
<tr class="even">
<td><p>FrontBuffer.bmp</p></td>
<td><p>The contents of the front buffer.</p></td>
</tr>
</tbody>
</table>

 

### <span id="Command_syntax"></span><span id="command_syntax"></span><span id="COMMAND_SYNTAX"></span>Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Command option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Present2_fullscreen.exe -M:1 -dx9 -whql -logclean</strong></p></td>
<td><p>Runs the Present Validation 2 (FullScreen) test job.</p></td>
</tr>
<tr class="even">
<td><p><strong>Present2_fullscreen.exe -M:1 -whql -logclean</strong></p></td>
<td><p>Runs the Present Validation 2 (FullScreen) (WoW64) test job.</p></td>
</tr>
</tbody>
</table>

>[!NOTE]
>  
For command-line help for this test binary, type **/?**.

 

### <span id="File_list"></span><span id="file_list"></span><span id="FILE_LIST"></span>File list

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configdisplay.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\tools</p></td>
</tr>
<tr class="even">
<td><p>D3d10ref.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support\</p></td>
</tr>
<tr class="odd">
<td><p>D3d11ref.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support\</p></td>
</tr>
<tr class="even">
<td><p>D3dcompiler_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support\</p></td>
</tr>
<tr class="odd">
<td><p>D3dref9.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support\</p></td>
</tr>
<tr class="even">
<td><p>D3dx10_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support\</p></td>
</tr>
<tr class="odd">
<td><p>D3dx11_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support\</p></td>
</tr>
<tr class="even">
<td><p>D3dx9_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support\</p></td>
</tr>
<tr class="odd">
<td><p>Fpstate.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\utility\</p></td>
</tr>
<tr class="even">
<td><p>Modechange.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\utility\</p></td>
</tr>
<tr class="odd">
<td><p>Present2_fullscreen.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\</p></td>
</tr>
<tr class="even">
<td><p>TDRWatch.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\</p></td>
</tr>
<tr class="odd">
<td><p>Vbswap.x</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\conf\</p></td>
</tr>
</tbody>
</table>

 

### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name               | Parameter description                                 |
|------------------------------|-------------------------------------------------------|
| **MODIFIEDCMDLINE**          | Additional command line arguments for test executable |
| **LLU\_NetAccessOnly**       | LLU Name of net user                                  |
| **MONITOR**                  | Display device to test                                |
| **ConfigDisplayCommandLine** | Custom Command Line for ConfigDisplay. Default: logo  |
| **TDRArgs**                  | /get or /set                                          |

 

 

 






