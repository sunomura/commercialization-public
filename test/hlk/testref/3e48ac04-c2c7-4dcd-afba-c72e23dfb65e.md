---
title: Manual Test - Verify eMMC is enumerated in mass storage mode
description: Manual Test - Verify eMMC is enumerated in mass storage mode
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 63b65c06-1fba-47a7-9577-93eb650dd829
---

# <span id="p_hlk_test.3e48ac04-c2c7-4dcd-afba-c72e23dfb65e"></span>Manual Test - Verify eMMC is enumerated in mass storage mode


This is a manual test & it should be run outside HLK by following the manual instructions provided below. If this test is run as an automated test from HLK studio/controller, the test will pass by default without testing any functionality. --------------------------------------------------------------------------------------------------------- Manual instructions to run this test: 1. Make sure the device is powered off and all the DIP switches on the debug board are in the OFF position. Note that you do not need a debug board to put the device in MSM. 2. If you're using KDSERIAL, disconnect the serial cable or close WinDbg as it interferes with mass storage hotkeys. 3. Position the phone on the debug board and plug in power but do not press the power key on the device or the debug board. 4. Plug in the micro-USB cable into the USB2 portion of the USB3 port. This acts as a wake event for the device. 5. Press and hold the Vol+ and the Camera buttons down during UEFI boot. This should bring up UEFI BDS menu. 6. The device should reboot into mass storage mode and a new physical disk would appear in the disk manager (diskmgmt.msc). NOTE: Common mistake: Device would neither auto power on nor enter mass storage mode if the micro-USB cable is inserted into USB2 port. --------------------------------------------------------------------------------------------------------- Note: This test is associated with an optional feature: System.Client.MobileHardware. It will not appear in the list of tests in HLK studio for a system target by default. Optional: To enable it to show up in the list of tests for system target in HLK studio, run the following steps: 1\] In HLK Studio, select system target 2\] Right click on the selected system target 3\] Click on Add\\Modify Features 4\] A Device Feature List window will open up 5\] Scroll down to select the feature named: System.Client.MobileHardware 6\] Click on the check box to enable this optional feature 7\] This test will now appear in the list of applicable tests for the selected system target in HLK studio

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

 

 






