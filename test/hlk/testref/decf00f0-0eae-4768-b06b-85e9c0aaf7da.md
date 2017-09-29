---
title: DF - PNP Surprise Remove Device Test (Reliability)
description: DF - PNP Surprise Remove Device Test (Reliability)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d2c60ab3-f7d2-4a86-be65-8b597eea5af7
---

# <span id="p_hlk_test.decf00f0-0eae-4768-b06b-85e9c0aaf7da"></span>DF - PNP Surprise Remove Device Test (Reliability)


The Surprise Removal test encompasses IRP\_MN\_SURPRISE\_REMOVAL followed by IRP\_MN\_REMOVE\_DEVICE.

As with the previous tests, the test application will attempt to add an upper filter to the target device stack and then restart the stack. If this attempt is not successful, the test restarts the computer.

When triggered by the test application, the filter driver will cause the system to send an IRP\_MN\_SURPRISE\_REMOVAL to the device stack, followed by an IRP\_MN\_REMOVE\_DEVICE. The filter driver will assert that both of these IRPs are completed successfully by lower drivers.

After the surprise removal test is complete, the device will be uninstalled and reenumerated, also removing the filter driver from the stack.

-   **Test binary:** Devfund\_PnPDTest.dll
-   **Test method:** PNPSurpriseRemoveAndRestartDevice

The Disable Enhanced Device Testing (EDT) Support test uninstalls the test filter driver (msdmfilt.sys) as an upper filter on devices specified using the DQ parameter. This test filter gets installed as part of running tests in this test category

-   **Test binary:** Devfund\_PnPDTest.dll
-   **Test method:** DisableEnhancedDeviceTestingSupport

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
<li>Device.DevFund.Reliability.BasicReliabilityAndPerformance</li>
<li>Device.DevFund.Reliability.PnPIRPs</li>
<li>Device.DevFund.DriverFramework.KMDF.Reliability</li>
<li>Device.DevFund.DriverFramework.UMDF.Reliability</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
<li>Windows 10 for desktop editions (Home, Pro, Enterprise, and Education) x86</li>
<li>Windows 10 for desktop editions x64</li>
<li>Windows Server 2016 x64</li>
<li>Windows 10 Mobile ARM</li>
<li>Windows 10 for desktop editions ARM64</li>
<li>Windows 10 Mobile ARM64</li>
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
<td>8</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Scenario</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>210</td>
</tr>
<tr class="odd">
<td><strong>Requires reboot</strong></td>
<td>false</td>
</tr>
<tr class="even">
<td><strong>Requires special configuration</strong></td>
<td>true</td>
</tr>
<tr class="odd">
<td><strong>Type</strong></td>
<td>automatic</td>
</tr>
</tbody>
</table>

 

## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.DevFund additional documentation](device-devfund-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Device.Fundamentals Reliability Testing Prerequisites](devicefundamentals-reliability-testing-prerequisites.md).

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information specific to the Device Fundamentals tests in the HLK and WDK, see [Device.DevFund additional documentation](device-devfund-additional-documentation.md).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name                               | Parameter description                                                                                                                                                                                                                                |
|----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **DQ**                                       | A WDTF SDEL query that is used to identify the target device(s) - http://go.microsoft.com/fwlink/?LinkId=232678                                                                                                                                      |
| **Wpa2PskAesSsid**                           | Required ONLY if DUT or one of its child devices is a WiFi adapter. Please provide SSID of a WPA2 AES WiFi network that the test can use to test the WiFi adapter. The default is 'kitstestssid'.                                                    |
| **Wpa2PskPassword**                          | Required ONLY if DUT or one of its child devices is a WiFi adapter. Please provide password of the WPA2 AES WiFi network specified using the Wpa2PskAesSsid parameter. The default is 'password'.                                                    |
| **WDTFREMOTESYSTEM**                         | Required ONLY if DUT or one of its child devices is a wired NIC that doesn't have an IPv6 gateway address. If determined to be required, please provide an IPv6 address that the test NIC can ping to test network I/O. Eg: fe80::78b6:810:9c12:46cd |
| **DriverVerifierAdditionalDrivers**          | Additional drivers that should have Driver Verifier enabled                                                                                                                                                                                          |
| **DriverVerifierExcludedFlags**              | Placeholder for Driver Verifier flags that may be manually excluded for the test run                                                                                                                                                                 |
| **MultiDeviceHardwareIdSdelQueryHardwareID** | Multi Device SDEL                                                                                                                                                                                                                                    |
| **MultiDeviceInstanceIdSdelWDKDeviceID**     | Device id of DUT                                                                                                                                                                                                                                     |
| **DriverVerifierCustomizeConfiguration**     | Specifies that this test may want to automatically update Driver Verifier settings                                                                                                                                                                   |
| **TestCycles**                               | Number of cycles to run the test for.                                                                                                                                                                                                                |
| **DoSimpleIO**                               | True or False. Runs SimpleIO (if found) on test devices before and after performing PNP operations.                                                                                                                                                  |
| **IOPeriod**                                 | Time period in minutes to run SimpleIO (if found).                                                                                                                                                                                                   |
| **DoConcurrentIO**                           | True or False. Uses WDTF concurrent IO interface to send I/O requests to target device stacks while performing PNP operations.                                                                                                                       |

 

 

 






