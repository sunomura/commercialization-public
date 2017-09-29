---
title: WLAN Association Tests - OPEN\_WPA2\_AES
description: WLAN Association Tests - OPEN\_WPA2\_AES
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 51290eda-acbe-4b75-852e-e8bc64c5d5b0
---

# <span id="p_hlk_test.d6da2adf-19f4-4df0-8dc2-cb6acd31deda"></span>WLAN Association Tests - OPEN\_WPA2\_AES


This test suite validates WLAN associations.

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
<li>Device.Network.WLAN.SupportConnectionToWiFiAP.ConnectionToWiFiAP</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
<li>Windows 10 for desktop editions (Home, Pro, Enterprise, and Education) x64</li>
<li>Windows 10 for desktop editions x86</li>
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
<td>20</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Scenario</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>1200</td>
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

-   [Device.Network additional documentation](device-network-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Wireless LAN (802.11) Testing Prerequisites](wireless-lan--80211--testing-prerequisites.md).

This test suite performs the following actions:

-   Configure two routers, that are named Router 0 and Router 1, as follows:
    -   Router 0 – 2.4Ghz : OPEN/NONE \[Preferred PHY G/Channel 1\]
    -   Router 0 – 5Ghz : WPA2PSK/AES \[Preferred PHY A/Channel 36\]
    -   Router 1 – 2.4Ghz : WPA2PSK/AES \[Preferred PHY G/Channel 11\]
    -   Router 1 – 5Ghz : WPA2PSK/AES \[Preferred N/Channel 36\]
-   Execute the BasicAssociation() test steps as described in WLAN Association Tests – Custom Configuration
-   Execute the AssociationPowerManagementSleep() test steps as described in [WLAN Association Tests – Custom Configuration](41e3400d-08da-424b-becd-fe3e8952bbca.md)
-   Execute the AssociationPowerManagementHibernate() test steps as described in [WLAN Association Tests – Custom Configuration](41e3400d-08da-424b-becd-fe3e8952bbca.md)

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting Wireless LAN (802.11) Tests](troubleshooting-wireless-lan--80211--tests.md).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name              | Parameter description                                                                    |
|-----------------------------|------------------------------------------------------------------------------------------|
| **TestDeviceSupports5ghz**  | This should be set to TRUE if the device supports 5ghz networks and FALSE if it does not |
| **APControllerIPAddress**   | Internal Parameter                                                                       |
| **LocalDir**                | Internal Parameter                                                                       |
| **AP1IPAddress**            | IP Address of the first AP connected to the system                                       |
| **AP1Password**             | Root password for the first AP connected to the system                                   |
| **AP2IPAddress**            | IP Address of the second AP connected to the system                                      |
| **AP2Password**             | Root password for the second AP connected to the system                                  |
| **ServiceAPChannelAddress** | Internal Parameter                                                                       |
| **TestDll**                 | Internal Parameter                                                                       |
| **Priority**                | Internal Parameter                                                                       |
| **TestName**                | Internal Parameter                                                                       |
| **EnableTracing**           | Yes or No to enable tracing                                                              |

 

 

 






