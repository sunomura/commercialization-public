---
title: Manual Test - Verify basic UEFI shell functionality
description: Manual Test - Verify basic UEFI shell functionality
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fd40eb2a-e8e9-4c1e-b7dd-55e83df47f7e
---

# <span id="p_hlk_test.dbee905d-663f-423d-88ed-d31cab46bcdb"></span>Manual Test - Verify basic UEFI shell functionality


This is a manual test & it should be run outside HLK by following the manual instructions provided below. If this test is run as an automated test from HLK studio/controller, the test will pass by default without testing any functionality. --------------------------------------------------------------------------------------------------------- Manual instructions to run this test: 1. Install serial comm application (for example putty.exe from http://www.putty.org) 2. Hook the device up to a serial debug connection. 3. Hold down ‘+’ and Camera button to go to UEFI menu 4. Navigate to Select “Enter Shell” (9) using ‘-‘ button. 5. Connect to device using Putty.exe 6. From putty, run command “memmap” 7. Verify memory map output is shown in putty.exe as well as on phone screen. a. Memmap summary should be in following format though values will be different: Reserved : 27,622 Pages (113,139,712) LoaderCode: 213 Pages (872,448) LoaderData: 0 Pages (0) BS\_Code : 362 Pages (1,482,752) BS\_Data : 4,772 Pages (19,546,112) RT\_Code : 40 Pages (163,840) RT\_Data : 31 Pages (126,976) ACPI Recl : 10 Pages (40,960) ACPI NVS : 1 Pages (4,096) MMIO : 3 Pages (12,288) Available : 229,093 Pages (938,364,928) Total Memory: 1024 MB (1,073,754,112 Bytes) --------------------------------------------------------------------------------------------------------- Note: This test is associated with an optional feature: System.Client.MobileHardware. It will not appear in the list of tests in HLK studio for a system target by default. Optional: To enable it to show up in the list of tests for system target in HLK studio, run the following steps: 1\] In HLK Studio, select system target 2\] Right click on the selected system target 3\] Click on Add\\Modify Features 4\] A Device Feature List window will open up 5\] Scroll down to select the feature named: System.Client.MobileHardware 6\] Click on the check box to enable this optional feature 7\] This test will now appear in the list of applicable tests for the selected system target in HLK studio

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
<li>System.Client.MobileHardware.BasicFunctionality</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
<li>Windows 10 Mobile ARM</li>
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
<td>15</td>
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
<td>manual</td>
</tr>
</tbody>
</table>

 

## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [System.Client additional documentation](system-client-additional-documentation.md)

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

 

 






