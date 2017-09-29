---
title: USB Device Connection S3+S4+Connected Standby
description: USB Device Connection S3+S4+Connected Standby
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ce83822f-7664-438d-985a-e4d429d6872c
---

# <span id="p_hlk_test.4e35cd21-a1dd-4cfa-be2d-1a9c9d6a1fef"></span>USB Device Connection S3+S4+Connected Standby


This test verifies that a USB-based device becomes available within 500 milliseconds after the test system exits the S3 or S4 power state or connected standby. The test also confirms that there were not any errant device disconnects during system resume.

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
<li>Device.Connectivity.UsbDevices.DeviceAttachLessThan100ms</li>
<li>Device.Connectivity.UsbDevices.MustBeFunctionalAfterResume</li>
<li>Device.Connectivity.UsbDevices.MustResumeWithoutForcedReset</li>
<li>Device.Connectivity.UsbDevices.MustSignalAttachWithin500ms</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
<li>Windows 10 for desktop editions (Home, Pro, Enterprise, and Education) x86</li>
<li>Windows 10 for desktop editions x64</li>
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
<td>Compatibility</td>
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
<td>automatic</td>
</tr>
</tbody>
</table>

 

## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Connectivity additional documentation](device-connectivity-additional-documentation.md)

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name  | Parameter description                   |
|-----------------|-----------------------------------------|
| **WDKDeviceID** | Device ID of the device under test      |
| **queryIsUsb3** | QueryIsUsb3 of device under test        |
| **DFUDevice**   | Uses DFU to reflash firmware on connect |

 

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

 

 






