---
title: LoadGen Server Stress - Run Last - Reset Machine Policies
description: LoadGen Server Stress - Run Last - Reset Machine Policies
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 44b82c4a-5467-40a8-9a6f-f3943bca79df
---

# <span id="p_hlk_test.8cb4f87c-d2a4-4d90-92a7-edd016ccdeac"></span>LoadGen Server Stress - Run Last - Reset Machine Policies


This automated test resets the machine policies that are used by the test on the test computers in the machine pool.

>[!NOTE]
>  
This test should be run after all other tests are finished.

 

This test job completes the following actions:

1.  RunJob - ReSet the policies on SUT

2.  Reset AutoLogon on SUT

3.  Reboot SUT

4.  Reset AutoLogon on MC

5.  RunJob - ReSet the policies on MC

6.  Reboot MC

7.  Remove stressclients dimension on MC

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
<li>System.Server.SystemStress.ServerStress</li>
<li>System.Server.FaultTolerant.Core</li>
<li>System.Server.SVVP.SVVP</li>
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
<td>30</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Scenario</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>1800</td>
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

-   [System.Server additional documentation](system-server-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [System Server Testing Prerequisites](system-server-testing-prerequisites.md) and [Test Server Configuration](test-server-configuration.md). This test should be run after all other tests are finished.

1.  Navigate to the **Tests** tab
2.  Select **LoadGen Server Stress - Run Last - Reset Machine Policies**
3.  Click the **Run Selected** link
4.  In the **Schedule** dialog, map machines to roles
    -   Use the **Role** dropdown to select machines for the MC and SC roles (SUT will be prepopulated)
5.  Click **OK** to schedule the test

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting System Server Testing](troubleshooting-system-server-testing.md).

 

 






