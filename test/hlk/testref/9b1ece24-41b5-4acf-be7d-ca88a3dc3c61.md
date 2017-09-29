---
title: Windows Touch Test
description: Windows Touch Test
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9bb7a4cd-287b-4243-bfee-3fc690fba76e
---

# <span id="p_hlk_test.9b1ece24-41b5-4acf-be7d-ca88a3dc3c61"></span>Windows Touch Test


This test verifies that a Windows® Touch device meets requirements.

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
<li>Device.Input.Digitizer.Touch.CustomGestures</li>
<li>Device.Input.Digitizer.Touch.HIDCompliant</li>
<li>Device.Input.Digitizer.Touch.ThirdPartyDrivers</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
<li>Windows 10 for desktop editions (Home, Pro, Enterprise, and Education) x86</li>
<li>Windows 10 for desktop editions x64</li>
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
<td>2</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Compatibility</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>120</td>
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

-   [Device.Input additional documentation](device-input-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Windows Touch Testing Prerequisites](windows-touch-testing-prerequisites.md).

The Windows Touch Test combines a set of simple manual tests. Measured requirements include: having a bezel that is flush with the display, specifying physical dimensions that match the device's true physical dimensions, and passing the HID Validator tool's static test. (The HID Validator tool installed together with the Windows HLK).

### <span id="Flush_Bezel"></span><span id="flush_bezel"></span><span id="FLUSH_BEZEL"></span>Flush Bezel

The bezel requirement (System.Client.Digitizer.Touch.Bezel) helps ensure easy access to the edge of the screen, which is used to display the **Charms Bar** and to switch applications. It also provides an optimal set of conditions to use the thumb keyboard. USB and I2C buses are required because they support the HID standard upon which the Windows touch infrastructure is based. FFU is required.

For a Tablet device, ensure that the bezel is flush with the display (the bezel must not be taller than the display).

### <span id="Physical_Dimensions"></span><span id="physical_dimensions"></span><span id="PHYSICAL_DIMENSIONS"></span>Physical Dimensions

The physical dimensions of the device must support system gestures and general touch interactions (Device.Digitizer.Touch.PhysicalDimension). For example, the momentum of a touch gesture depends on the physical distance moved and the length of that movement.

This test verifies that the physical dimensions that are reported by the HID descriptor match the true physical dimensions of the visible screen area. Discrepancies affect system gestures and UI elements, which rely on physical size information. We strongly recommend that you use the dimensions that are specified by the display manufacturer. The test itself relies on this information to size elements appropriately. The test will be affected by errors; for example, targets that are intended to be 20mm apart might resolve to being 22mm apart. The WTTL does not make allowances for devices that report physical size values that differ from the true measurement by more than 2mm.

### <span id="High_Quality_Touch_Digitizer_Input"></span><span id="high_quality_touch_digitizer_input"></span><span id="HIGH_QUALITY_TOUCH_DIGITIZER_INPUT"></span>High Quality Touch Digitizer Input

To run this test, the HID descriptor must be stored in the device firmware. The Windows Hardware Lab Kit (Windows HLK) includes the HID Validator tool. Before you run this test, we recommend that you review **Windows Hardware Certification Requirements** and the HID Validator documentation that is installed together with the HID Validator tool.

To run the test, double-click **HidValidator.exe** on the touch device. The tool ensures that the descriptor conforms to the HID specification.

### <span id="Power_States"></span><span id="power_states"></span><span id="POWER_STATES"></span>Power States

For a discussion of power-state requirements (Device.Digitizer.Touch.PowerStates), see [Power Handling for Windows 8 Touch Controllers](http://go.microsoft.com/fwlink/?LinkID=287026).

You can use the WTTL to check the ability of a device to traverse power states by using the following procedure:

**To run the power states test**

1.  If applicable, put the device into the **Connected Standby** state. Otherwise, power the device off.

2.  Place any type of contact on any number on the screen and hold for 10 to 15 seconds.

3.  If the device is in the **Connected Standby** state, wake the device while maintaining contact. If the device is powered off, power on the device while maintaining contact.

4.  After the machine has booted, ensure that no ghost touches exist. Attempt to use touch input.

5.  If applicable to the device, repeat these steps for **Sleep (S3)** state.

If no ghost touches exist, and if touch input can be used as expected to control the machine, then the device passes this test. Otherwise, it fails the test.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [How to run the Windows HLK Tests for Touch and Pen Devices](how-to-run-the-windows-hck-tests-for-touch-and-pen-devices.md#hiderrors).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


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
<td><p><strong>Logo3.exe -config Other.json</strong></p></td>
<td><p>Runs the test.</p></td>
</tr>
</tbody>
</table>

 

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
<td><p>Logo3.exe</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\digitizer\Win8Touch</p></td>
</tr>
<tr class="even">
<td><p>Other.json</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\digitizer\Win8Touch</p></td>
</tr>
</tbody>
</table>

 

 

 






