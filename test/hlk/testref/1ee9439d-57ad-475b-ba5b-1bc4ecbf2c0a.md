---
title: iSCSI Boot Firmware Table Test (LOGO)
description: iSCSI Boot Firmware Table Test (LOGO)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: bf46d5cf-8d5e-4678-a9ce-7c8be3b42574
---

# <span id="p_hlk_test.1ee9439d-57ad-475b-ba5b-1bc4ecbf2c0a"></span>iSCSI Boot Firmware Table Test (LOGO)


This test verifies that the iSCSI Boot Firmware table is available and is valid.

The iSCSI Boot Firmware Table (iBFT) is a block of information residing in memory that contains different entries that are required by the iSCSI boot process.

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
<li>Device.Storage.Controller.Iscsi.iSCSIBootComponent.FwTable</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
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
<td>10</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Development</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>600</td>
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

-   [Device.Storage additional documentation](device-storage-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [iSCSI Boot Component Testing Prerequisites](iscsi-boot-component-testing-prerequisites.md).

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see: [Troubleshooting Device.Storage Testing](troubleshooting-devicestorage-testing.md).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


iSCSI Boot Firmware Table test (iBFTest) consists of two binaries. A user-mode binary (ibftestwrap.exe) and a kernel-mode binary (ibftest.sys). Both binaries are required for the test to run successfully.

1.  ibftestwrap.exe loads ibftest.sys into kernel mode.

2.  ibftest.sys checks if iBFT exists in memory.

3.  If iBFT exists in memory, ibftest.sys will get a copy of the table.

4.  ibftest.sys validates the table and returns results to ibftestwrap.exe.

5.  ibftestwrap.exe in turn provides a friendly log.

6.  The log contains either the table if it is available and valid or a detailed error information if the table is unavailable or invalid.

iBFTest ensures that the iBFT is present and available to the operating system for a consistent flow of the boot process. It also validates the various entries within the table and ensures that the table is intact. It ensures that all the information is compliant with the specification

To run the test, do the following:

1.  Copy iBFTest binaries: (Or make sure iBFTest is available within HLK Studio)

    1.  Copy ibftestwrap.exe to test working directory.

    2.  Copy ibftest.sys to test working directory.

2.  Run ibftestwrap.exe

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
<td><p><strong>ibftest.exe</strong></p></td>
<td></td>
</tr>
</tbody>
</table>

>[!NOTE]
>  
For command-line help for this test binary, type `/h`

 

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
<td><p>Ibftest.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\DriversTest\storage\wdk\ibftest\</p></td>
</tr>
<tr class="even">
<td><p>Ibftest.sys</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\DriversTest\storage\wdk\ibftest\</p></td>
</tr>
<tr class="odd">
<td><p>Ibftestwrap.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\DriversTest\storage\wdk\ibftest\</p></td>
</tr>
</tbody>
</table>

 

### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name         | Parameter description                      |
|------------------------|--------------------------------------------|
| **LLU\_NetAccessOnly** | User account for accessing test fileshare. |
| **LLU\_LclAdminUsr**   | User account for running the test.         |

 

 

 






