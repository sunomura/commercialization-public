---
title: Wlan Test - Toggle airplane mode - (WoW64 for ARM64)
description: Wlan Test - Toggle airplane mode - (WoW64 for ARM64)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a93c542e-729c-400d-84e2-918b162bef91
---

# <span id="p_hlk_test.f248aee1-aada-44d2-8b8d-f03ffbeacef3"></span>Wlan Test - Toggle airplane mode - (WoW64 for ARM64)


This automated test toggles the radio states in the same way as the user interface airplane mode option.

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
<li>System.Client.WLAN.BasicConnectivity.WlanBasicConnectivity</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
<li>Windows 10 for desktop editions (Home, Pro, Enterprise, and Education) ARM64</li>
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
<td>1</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Scenario</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>5</td>
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

-   [System.Client additional documentation](system-client-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


This test is only valid on systems with a Wireless LAN adapter. The test completes the following:

1.  Disables each radio that is reported to the operating system.
2.  Each radio must change state and report its updated state in less than ten seconds.
3.  Enables each radio that is reported to the operating system.
4.  Each radio must change state and report its update state in under ten seconds

The test allows for and can accommodate devices that change the state of all radios when only one radio is requested. The test will only fail if an exception is thrown when attempting any of the above tasks, or if radios do not change state within the time required

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting the HCK Environment](http://msdn.microsoft.com/en-us/library/windows/hardware/hh998592.aspx).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name    | Parameter description |
|-------------------|-----------------------|
| **EnableTracing** | Enable Tracing        |

 

 

 






