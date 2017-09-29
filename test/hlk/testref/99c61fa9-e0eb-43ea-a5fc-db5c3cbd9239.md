---
title: DF - Reboot restart with IO before and after (Reliability)
description: DF - Reboot restart with IO before and after (Reliability)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1041ca7f-313c-42a5-9cc7-7c0769397299
---

# <span id="p_hlk_test.99c61fa9-e0eb-43ea-a5fc-db5c3cbd9239"></span>DF - Reboot restart with IO before and after (Reliability)


This test runs I/O on devices before and after a system reboot.

-   **Test binary:** Devfund\_RebootRestart\_With\_IO\_BeforeAndAfter.dll
-   **Test method:** Reboot\_Restart\_With\_IO\_Before\_And\_After

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
<li>Device.DevFund.Reliability.Discretional</li>
<li>Device.DevFund.Reliability.PnPIDs</li>
<li>Device.DevFund.ReliabilityDisk.IOCompletionCancellation</li>
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
<td>4</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Scenario</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>30</td>
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

| Parameter name                               | Parameter description                                                                                                                                                                                                                            |
|----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **DQ**                                       | A WDTF SDEL query that is used to identify the target device(s) - http://go.microsoft.com/fwlink/?LinkId=232678                                                                                                                                  |
| **Wpa2PskAesSsid**                           | Required ONLY if DUT or one of its child devices is a WiFi adapter. Please provide SSID of a WPA2 AES WiFi network that the test can use to test the WiFi adapter. The default is 'kitstestssid'.                                                |
| **Wpa2PskPassword**                          | Required ONLY if DUT or one of its child devices is a WiFi adapter. Please provide password of the WPA2 AES WiFi network specified using the Wpa2PskAesSsid parameter. The default is 'password'.                                                |
| **MultiDeviceHardwareIdSdelQueryHardwareID** | Multi Device SDEL                                                                                                                                                                                                                                |
| **MultiDeviceInstanceIdSdelWDKDeviceID**     | Device id of DUT                                                                                                                                                                                                                                 |
| **WDTFREMOTESYSTEM**                         | Required ONLY if DUT or any of its child devices is a wired NIC that does not have an IPv6 gateway address. If determined to be required, please provide an IPv6 address that the NIC can ping to test network I/O. Eg: fe80::78b6:810:9c12:46cd |
| **TestCycles**                               | Number of test cycles                                                                                                                                                                                                                            |
| **IOPeriod**                                 | IO period in minutes                                                                                                                                                                                                                             |
| **DriverVerifierAdditionalDrivers**          | Additional drivers that should have Driver Verifier enabled                                                                                                                                                                                      |
| **DriverVerifierExcludedFlags**              | Placeholder for Driver Verifier flags that may be manually excluded for the test run                                                                                                                                                             |
| **DriverVerifierCustomizeConfiguration**     | Specifies that this test may want to automatically update Driver Verifier settings                                                                                                                                                               |

 

 

 






