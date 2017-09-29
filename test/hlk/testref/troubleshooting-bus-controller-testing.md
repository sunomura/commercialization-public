---
title: Troubleshooting Bus Controller Testing
description: Troubleshooting Bus Controller Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8784dc59-3a52-48b1-9568-3b6b9962bbdf
---

# Troubleshooting Bus Controller Testing


To troubleshoot bus controller test issues, follow these steps:

1.  Review the following Windows Hardware Lab Kit (Windows HLK) topics:

    -   [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md)

    -   One of the following topics, depending on the type of bus controller that you are testing:

        -   [Bluetooth Controller Testing Prerequisites](bluetooth-controller-testing-prerequisites.md)

        -   [Proximity Controller Testing Prerequisites](proximity-controller-testing-prerequisites.md)

        -   [Secure Digital Host Controller Testing Prerequisites](secure-digital-host-controller-testing-prerequisites.md)

        -   [USB Bus Controller Testing Prerequisites](usb-bus-controller-testing-prerequisites.md)

        -   [WITT I2C Testing Prerequisites](witt-i2c-testing-prerequisites.md)

2.  Verify that you have installed the latest Windows HLK filters and kit updates. For more information, see [Windows Hardware Lab Kit Filters](..\user\windows-hardware-lab-kit-filters.md).

3.  For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

4.  If you cannot obtain a successful test result, contact [Windows HLK Support](..\user\windows-hlk-support.md).

### <span id="bluetooth"></span><span id="BLUETOOTH"></span>Bluetooth controller test troubleshooting

The following table describes common issues that can occur during Bluetooth controller testing:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Issue</th>
<th>Resolution</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Failures finding Bluetooth devices during an Bluetooth Inquiry command</p></td>
<td><p>This failure can happen when you run a test in a noisy environment. Rerunning the test usually fixes this error. You can also try to bring the radios closer together. Make sure that the radios have a clear line of sight. Turn off other radios that may be causing interference.</p></td>
</tr>
<tr class="even">
<td><p>Failures connecting Bluetooth devices during Bluetooth Inquiry commands</p></td>
<td><p>This failure occurs when the test times out before the devices could be reconnected. Rerunning the test usually fixes this error.</p></td>
</tr>
</tbody>
</table>

 

## <span id="witti2c"></span><span id="WITTI2C"></span>WITT I²C controller test troubleshooting


The following table describes common issues that can occur during Windows Inter-Integrated Circuit (I²C) Testing Tool (WITT) controller testing:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Issue</th>
<th>Resolution</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>All tests failed with error message <strong>WITT device test interface is not found</strong>.</p></td>
<td><p>Review [WITT I2C Testing Prerequisites](witt-i2c-testing-prerequisites.md). Make sure that the WITT test peripheral driver is installed, ACPI table modified with sample ASL and four instances of WITT Test Driver are found in Windows HLK Device Manager.</p></td>
</tr>
<tr class="even">
<td><p>WITT firmware needs to be updated. The WITT firmware binary (i2c9665a.iic) is released as part of. When you install a new Windows HLK package, you should update the WITT firmware.</p></td>
<td><p>See [WITT I2C Testing Prerequisites](witt-i2c-testing-prerequisites.md) for instructions on how to upgrade the WITT firmware.</p></td>
</tr>
<tr class="odd">
<td><p>WITT device is in a bad state. Typically, the green LED on a WITT device should be lit when there is no traffic, and should blink when there is traffic. Otherwise, the WITT or I²C controller might be in a bad state.</p></td>
<td><p>Unplug the WITTs USB cable to power-cycle the device. If the controller is still not working, reboot the testing system.</p></td>
</tr>
</tbody>
</table>

 

## <span id="related_topics"></span>Related topics


[Device.BusController Tests](device-buscontroller-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







