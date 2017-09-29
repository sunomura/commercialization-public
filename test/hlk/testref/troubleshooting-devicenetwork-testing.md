---
title: Troubleshooting Device.Network Testing
description: Troubleshooting Device.Network Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1e8ce900-ca80-4d8e-b507-2976262aa8f4
---

# Troubleshooting Device.Network Testing


## <span id="troubleshooting_device.network_testing"></span><span id="TROUBLESHOOTING_DEVICE.NETWORK_TESTING"></span>Troubleshooting Device.Network Testing


To troubleshoot issues that occur with Device.Network tests, follow these steps:

1.  Review [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

    Review one of the following topics, depending on the type of networking product or feature that you are testing:

    -   [IPsec Task Offload v2 Testing Prerequisites](ipsec-task-offload-v2-testing-prerequisites.md)

    -   [LAN Testing Prerequisites](lan-testing-prerequisites.md)

    -   [Mobile Broadband Testing Prerequisites](mobile-broadband-testing-prerequisites.md)

    -   [Router Testing (Non-wireless) Prerequisites](router-testing--non-wireless--prerequisites.md)

    -   [Wireless LAN (802.11) Testing Prerequisites](wireless-lan--80211--testing-prerequisites.md)

    -   [Wireless Router Testing Prerequisites](wireless-router-testing-prerequisites.md)

2.  Review the [Windows HLK release notes](http://go.microsoft.com/fwlink/?LinkID=236110) for current test issues.

3.  For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

### <span id="Known_IPsec_test_issues"></span><span id="known_ipsec_test_issues"></span><span id="KNOWN_IPSEC_TEST_ISSUES"></span>Known IPsec test issues

If the Windows HLK Controller cannot connect to clients, follow these steps:

1.  The very first test case is designed to ensure that the setup is correct. It does nothing but check the public and private network for connectivity. If this test fails, then there is a test setup issue.

2.  Check to ensure that the file config.dat is placed in the %SystemDrive%\\IPsecTestKit\\IPsecScenario\\ directory and has the right IP addresses for the controller and the clients. This file is auto generated, but in certain cases such as DNS resolution failures, the config.dat file may contain incorrect data or be missing altogether. Please use the format described in the Test Setup section to verify the config.dat file.

3.  Check to ensure that you have firewall exemptions for IPsecControl.exe and IPsecScenario.exe.

4.  Check to ensure that after running the setup scripts, the IPsec Offload V2 interfaces are successfully renamed to "Test1".

Genconfig\_phase2.vbs may not generate the necessary CMD files if there is only 1 default gateway for the message adapter. If your DHCP server does not support IP V6, you may only get 1 IP V6 default gateway address.

**Running Individual Test Variations**

In certain cases when tests fail, run a single test variation instead of re-running the whole suite. To do this, follow these steps:

1.  Make sure that the IPsecScenario.exe sessions are running on all clients.

2.  Copy individual variations to run from within OffloadV2\_logoTests.cmd and run them from a new command window (%SYSTEMDRIVE%\\IPsecTestKit\\IPSecscenario\\Controller

`Troubleshooting LAN (Ethernet) Testing`

The IPSec test job may fail due to issues with related LAN test jobs. See the following section for details.

### <span id="Known_LAN__Ethernet__test_issues"></span><span id="known_lan__ethernet__test_issues"></span><span id="KNOWN_LAN__ETHERNET__TEST_ISSUES"></span>Known LAN (Ethernet) test issues

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Issue</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The &quot;IPsec Offloadv2 logo verification (Win7)&quot; test jobs stay in the &quot;Scheduler&quot; status and never run.</p></td>
<td><p>This problem is usually caused by various communication issues between the DTM client and the controller. You can check whether the &quot;Last Heartbeat time&quot; is close to the current time. To force the DTM client that is reporting a heartbeat, you can manually change the status of the machine to <strong>Reset</strong> or <strong>Unsafe</strong> in the DTM Studio, and then wait until the status of the machine changes back to &quot;Normal&quot;. After the status of all machines that are required to run the job is changed to <strong>Normal</strong>, the job will be scheduled on the DTM clients. If the machine status changes to <strong>Debug</strong>, verify whether the DTM client machine is still responsive. Sometimes, the machine status is <strong>Normal</strong> and the heartbeat is correct, but the job still won't run. This is most likely caused by the firewall or IPsec blocking the communication between the DTM client and the controller. Make sure that the DTM client and controller have the same IPsec configuration. If the client has IPsec turned on but the controller turned off, or vice versa, the job will not get scheduled. The DTM client is designed to work with a firewall, but sometimes the firewall blocks normal traffic between the client and the controller.</p></td>
</tr>
<tr class="even">
<td><p>The following error message is observer in the test log: “The Job xxx requires a device to be selected, not a driver&quot; when clicking &quot;Add Information&quot;.</p></td>
<td><p>The error happens because you have selected a driver, not a test device, in the <strong>Device Console</strong> to run the test job. If you cannot find a device under the driver in the <strong>Device Console,</strong> the INF file and driver files that you provided during the logo submission do not match the actual INF file and driver files on the DTM client. Update your INF file and driver files by using the actual INF file and driver files installed on the DTM client.</p></td>
</tr>
<tr class="odd">
<td><p>No &quot;IPsec Offloadv2 logo verification (Win7)&quot; job shows up in the &quot;Device Console&quot;.</p></td>
<td><p>Make sure your device is an Ethernet (LAN) device and report media type to NDIS as NdisMedium802_3. This error sometimes happens when the hardware information reported by the DTM client is incomplete. To solve this problem, try to can reboot the DTM client machine and refresh the view of <strong>Device Console</strong>. If this doesn't work, try to stop and restart the &quot;wttsvc&quot; service on the DTM client, and then refresh the view of <strong>Device Console</strong>.</p></td>
</tr>
<tr class="even">
<td><p>The Ethernet - NDISTest 6.0 (priority) test may properly fail the 2c_priority and Directed Packets - NdisSendPackets assertion with a <strong>Unable to get test results on the test network adapter</strong> message.</p></td>
<td><p>This issue may occur when the network switch incorrectly strips priority bits. To confirm that this issue occurs because of the network switch, test the adapter by removing the switch and connecting the cables directly.</p>
<p>You can do this by using an alternate test configuration. This test configuration can only be used by devices that do not support Chimney, (TCP Offload) as the local support device is required for those devices. Please remove the Local Support Device and Test Network Switch altogether, and connect the Local Test Device directly back-to-back with the Remote Support Device. If this is the passes, this is acceptable for certification but please work with the switch manufacturer to correct the switch configuration.</p></td>
</tr>
<tr class="odd">
<td><p>The Ethernet - NDISTest 6.5 (WoL and PM) may correctly fail devices within the Send a FAKE LLMNRv4 network packet assertion with an error indicating the machine is working incorrectly.</p></td>
<td><p>To help determine if your device is properly failing, unbound the protocols on the remote device only.</p>
<p>If this does not resolve the issue, open a support incident</p></td>
</tr>
</tbody>
</table>

>[!NOTE]
>  
To troubleshoot the NDISTest (6.0 or 6.5), attach a debugger to the test computer.

 

### <span id="Known_mobile_broadband_test_issues"></span><span id="known_mobile_broadband_test_issues"></span><span id="KNOWN_MOBILE_BROADBAND_TEST_ISSUES"></span>Known mobile broadband test issues

The following list describes some common troubleshooting tips for Mobile Broadband testing:

Changes that were made to devices on DTM client computers are not reflected in DTM Studio. For example, the machine is expected to be in the Ready state but it is not.

1.  Open a command prompt window on the client computer, and then run `net stop wttsvc`.

2.  Run `net start wttsvc`. This command updates the C:\\wtt\\JobsWorkingDir\\AssetCfg\\Log\\ directory.

3.  Refresh the **Device Console** window in DTM Studio. It may take several minutes for the DTM Controller to poll the client computer for changes in its device list.

Computers have not been discovered for the machine pool.

1.  Open the **Job Monitor** window in DTM Studio.

2.  Click the **Show Query Builder** button at the top of the screen.

3.  Click the **Machine Query** tab.

4.  Define search parameters for the targeted computers. Typically, set a single rule such as "DataStore equals 'Controller Name'".

5.  Right-click the rule that was just defined, and then click **Execute**. An extensive list of computers populates the **Machines** list below the query fields.

6.  Drag any machines in the **Machines** list into new machine pool that was created.

Computers do not seem to run jobs that are scheduled for them.

1.  Open the **Job Monitor** window in DTM Studio.

2.  In the **Machine Pool** tab, select the machine pool that is expected to be running jobs.

3.  For each computer in that pool, verify that its status is **Ready**.

4.  If a computer's status is not **Ready**, right-click the computer, point to **Change Status**, and then click **Reset**.

5.  After a few minutes, refresh the screen and the status changes to **Ready**.

6.  Schedule and start the jobs again.

### <span id="Known_network_security_software_testing_prerequisites"></span><span id="known_network_security_software_testing_prerequisites"></span><span id="KNOWN_NETWORK_SECURITY_SOFTWARE_TESTING_PREREQUISITES"></span>Known network security software testing prerequisites

The network security software tests ([TransitionTechnologies\_Tests](92628629-82bb-4c60-9750-ce2842d2fd92.md) and [WindowsFilteringPlatform\_Tests](a9a199cc-29b0-4805-9362-a2e7da39810c.md)) require that the Sparta miniport drivers are installed and configured correctly. The Sparta miniport drivers are installed when each test runs, However, if you choose to, you can verify that they are present by opening a command prompt and typing **IPConfig.exe /all**. You should see four new Sparta interfaces named Sparta Miniport Primary, Sparta Miniport Secondary, Sparta Miniport Tertiary, and Sparta Miniport Quaternary.

### <span id="Known_router_test_issues"></span><span id="known_router_test_issues"></span><span id="KNOWN_ROUTER_TEST_ISSUES"></span>Known router test issues

Currently there are no known router test issues.

### <span id="Known_wireless_LAN__802.11__test_issues"></span><span id="known_wireless_lan__802.11__test_issues"></span><span id="KNOWN_WIRELESS_LAN__802.11__TEST_ISSUES"></span>Known wireless LAN (802.11) test issues

The following list describes some common troubleshooting tips for WLAN testing:

**Changes that you made to devices on DTM clients machines are not reflected in DTM Studio. For example, the machine is expected to be in the Ready state but it is not.**

1.  Open a Command Prompt window on the client machine, and then run `net stop wttsvc.`

2.  Run `net start wttsvc`. This command will update the C:\\wtt\\JobsWorkingDir\\AssetCfg\\Log\\ directory.

3.  Refresh the **Device Console** window in DTM Studio. You might have to wait several minutes for the DTM controller to poll the client machine for changes in its device list.

**Machines have not been discovered for the machine pool.**

1.  Open the **Job Monitor** window in DTM Studio.

2.  Select the **Show Query Builder** button at the top of the screen.

3.  Click the **Machine Query** tab.

4.  Define search parameters for the machines that you are looking for. Typically, you can set a single rule such as "DataStore equals 'Controller Name'".

5.  Right-click the rule that you just defined, and then click **Execute**. An extensive list of machines should populate the Machines list below the query fields that you defined.

6.  Drag any machines in the **Machines** list into new machine pools that you created.

Machines do not seem to run jobs that are scheduled for them.

1.  Open the **Job Monitor** window in DTM Studio.

2.  In the **Machine Pool** tab, select the machine pool that you expect to be running jobs.

3.  For each machine in that pool, verify that its status is **Ready**.

4.  If a machine's status is not **Ready**, right-click the machine, point to **Change Status**, and then click **Reset**.

5.  After a few minutes, refresh the screen and the status will change to **Ready**.

6.  Schedule and start the jobs again.

**Problems with installing the Test SoftAP driver on the topology: Device Manager reports code 52**

Do not install the x64 Test SoftAP driver before installing the DTM client. When the DTM client is installed, the Root Certificate is installed. Because the Test SoftAP driver signing depends on installation of the Root Certificate, the device manager reports device code 52.

**Configuring NDISTest for stand-alone execution**

Installing NDISTest separate from DTM Studio enables you to execute individual tests. A DUT, SUT, and Test SoftAP needs to be configured to enable stand-alone execution.

>[!NOTE]
>  
All test machines must use the same processor architecture.

>[!NOTE]
>  
To troubleshoot the NDISTest, try attaching a debugger to the test machine.

 

**Configuring a Support Device Under Test (SUT)**

1.  Copy all NDISTest binaries and sub directories from the following DTM controller:

    `\\<ControllerMachine]>\tests\<architecture>\nttest\nettest\ndis\ndistest.net\`

    &lt;ControllerMachine&gt; is the name of the DTM controller computer and &lt;architecture&gt; is either x86 (for x86-based processors) or amd64 (for x64-based processors).

2.  Launch NDISTest.exe from the install directory. When the main form opens, select **Server** from the **File** menu to launch the server form.

3.  Select the message device from the **Message Device** list. This device must be IP-enabled and on the same subnet as the client message device that will be set up later.

4.  Select SUT device(s) from **Support Devices**. The support device selected on this server from will be visible to the client after the server is started.

5.  Select the "server" job from **Jobs**. This is the server side test that will be launched after you click the start button.

After all the options have been selected, click **Start** to start the server.

**Configuring a Test Software Access Point (Test SoftAP)**

1.  Copy all NDISTest binaries and sub directories from the following DTM controller:

    `\\<ControllerMachine]>\tests\<architecture>\nttest\nettest\ndis\ndistest.net\`

    &lt;ControllerMachine&gt; is the name of the DTM controller computer and &lt;architecture&gt; is either x86 (for x86-based processors) or amd64 (for x64-based processors).

2.  Install SoftAP driver for both of the Atheros WLAN devices on the Test SoftAP. You can install this driver from Device Manager, which you can open by running `devmgmt.msc` from a command prompt. Complete the following step:

    In **Device Manager**, install the driver for SoftAP stations from:

    `\\<ControllerMachine]>\Tests\<architecture>\nttest\nettest\ndis\NDISTest.net\SoftAPMiniport\`

    &lt;ControllerMachine&gt; is the name of the DTM controller computer and &lt;architecture&gt; is either x86 (for x86-based processors) or amd64 (for x64-based processors), depending on the processor architecture of the DTM client machine that have the SoftAP devices.

3.  Launch NDISTest.exe from the install directory. When the main form opens, select **Server** from the **File** menu to launch the server form.

4.  Select the message device from the **Message Device** list. This device must be IP-enabled device and on the same subnet as the client message device that will be set up later.

5.  Select the AP device(s) from **AP Devices**. AP devices selected on this server will be visible to the client after the server is started.

6.  Select the "server" job from **Jobs**. This is the server side test that will be launched after you click the start button.

After all the options have been selected, click **Start** to start the server.

**Configuring the Device Under Test (DUT)**

1.  Copy all NDISTest binaries and sub directories from the following DTM controller:

    `\\<ControllerMachine>\tests\<architecture>\nttest\nettest\ndis\ndistest.net\`

    &lt;ControllerMachine&gt; is the name of the DTM controller computer and &lt;architecture&gt; is either x86 (for x86-based processors) or amd64 (for x64-based processors).

2.  Launch NDISTest.exe from the install directory. When the main form opens, select **Client** from the **File** menu to launch the client form.

3.  Select the test target from the **Test Target** list. For network device, this test target should be **Miniport**.

4.  Select the test device from the **Test Device** list. This must be a vendor-specific test device.

5.  Select a message device from the **Message Device** list. This should be an IP-enabled device that is on the same subnet as the server message device. After the message device has been selected, the AP device section should be displayed and the server AP device should be available in the list.

6.  Select a support device from **Support Devices**. This must be a vendor-specific support device.

7.  Select an AP device from **AP Devices**. This must be the AP device that was select on the server side.

8.  Select the tests from the **Jobs** section that will be run after the client is launched.

After all the options have been selected, click **Start** to start the client. Any jobs that were selected will begin execution. Test results will be stored on the client in the following logging sub-folder:

`<NDISTestRootFolder>/logs/<AdapterName>/`

**Configuring Client Packet Capture**

1.  Configure a test topology for stand-alone execution. For more information, go to "Configuring NDISTest for stand-alone execution."

2.  Setup a second SUT. For more information, go to "Configuring a Support Device Under Test (SUT)."

3.  Launch NDISTest.exe from the install directory. When the main form opens, select **Debug** from the **View** menu to launch the **Packet Capture** section on the client.

4.  Select a Capture device from **Packet Capture**. This must be a Support device that was selected on the server side.

5.  From **Jobs**, select the tests that will be run after the client is launched.

6.  After all of the options have been selected, click **Start** to start the client.

7.  Packet captures corresponding to the Tests will be generated on the Server with the capture device. The logs will be in the following logging sub-folder:

    `<NDISTestRootFolder>/logs/<AdapterName>/`

**Troubleshooting when the Packet Capture section does not show up on client**

Verify that the message center user interface is closed. If the NDISTest user interface is not maximized, the **Packet Capture** section may be hidden behind the message center user interface.

### <span id="Known_wireless_router_test_issues"></span><span id="known_wireless_router_test_issues"></span><span id="KNOWN_WIRELESS_ROUTER_TEST_ISSUES"></span>Known wireless router test issues

This tip will help you in testing the ability of machine sending higher bit rates using Ethernet connection (i.e. validates the machine).

For this test procedure, setup two computers as shown in the following diagram:

![diagram of computers s and c connected to a hub](images/hck-win8-wireless-router-troubleshooting-speed-1-6.png)

1.  Setup the hardware as shown below with only Ethernet connection

2.  Assign a static IP address to Machine S.

    For Example: 10.0.0.2

3.  Assign a static IP address to Machine C.

    For Example: 10.0.0.3

4.  On Machine C, open a command prompt and run the following command:

    `stats.exe -z DISCARD -i 20 -x 50 -y 30 -r 20000000 -c 3600 -l -h -u`

5.  On Machine S, open a command prompt and run the following command:

    **stats.exe -d 10.0.0.3 -r 20000000 -c 4200 -l -h -u**

6.  Review the output of Step 4 and Step 5.

If the output of either Step 4 or Step 5 shows any failures then your machines cannot make bit rates using wireless adapters.

If you need to add a wireless profile manually, you can do so by using the netsh command.

For Example: To add the 802\_11a\_wpa-psk.xml wireless profile:

1.  Click **Start**, click **Run**, and enter **cmd.exe**.

2.  Type **netsh wlan add profile filename=802\_11a\_wpa-psk.xml i=\***

3.  Click **OK**.

>[!NOTE]
>  
Make sure that Wireless Profile XML file exists in the current directory or specify the full path.

 

## <span id="related_topics"></span>Related topics


[Device.Network Testing](device-network-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







