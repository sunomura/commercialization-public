---
title: Troubleshooting Wireless LAN (802.11) Tests
description: Troubleshooting Wireless LAN (802.11) Tests
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b2189bb0-ecb4-4dac-893d-7e6f077d1c2d
---

# Troubleshooting Wireless LAN (802.11) Tests


This topic describes some common troubleshooting tips for WLAN testing. To begin:

1.  Review [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

2.  Review the [Windows HLK release notes](http://go.microsoft.com/fwlink/?LinkID=236110) for current test issues.

3.  For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

## <span id="Changes_that_you_made_to_devices_on_HLK_clients_machines_are_not_reflected_in_HLK_Studio._For_example__the_machine_is_expected_to_be_in_the_Ready_state_but_it_is_not."></span><span id="changes_that_you_made_to_devices_on_hlk_clients_machines_are_not_reflected_in_hlk_studio._for_example__the_machine_is_expected_to_be_in_the_ready_state_but_it_is_not."></span><span id="CHANGES_THAT_YOU_MADE_TO_DEVICES_ON_HLK_CLIENTS_MACHINES_ARE_NOT_REFLECTED_IN_HLK_STUDIO._FOR_EXAMPLE__THE_MACHINE_IS_EXPECTED_TO_BE_IN_THE_READY_STATE_BUT_IT_IS_NOT."></span>Changes that you made to devices on HLK clients machines are not reflected in HLK Studio. For example, the machine is expected to be in the Ready state but it is not.


1.  Open a Command Prompt window on the client machine, and then run **net stop wttsvc**.

2.  Run **net start wttsvc**. This command will update the C:\\wtt\\JobsWorkingDir\\AssetCfg\\Log\\ directory.

3.  Restart the HLK Studio. You might have to wait several minutes for the HLK controller to poll the client machine for changes in its device list.

## <span id="machines_have_not_been_discovered_for_the_machine_pool."></span><span id="MACHINES_HAVE_NOT_BEEN_DISCOVERED_FOR_THE_MACHINE_POOL."></span>Machines have not been discovered for the machine pool.


1.  Open the **Job Monitor** window in HLK Manager.

2.  Select the **Show Query Builder** button at the top of the screen.

3.  Click the **Machine Query** tab.

4.  Define search parameters for the machines that you are looking for. Typically, you can set a single rule such as "DataStore equals 'Controller Name'".

5.  Right-click the rule that you just defined, and then click **Execute**. An extensive list of machines should populate the **Machines** list below the query fields that you defined.

6.  Drag any machines in the **Machines** list into new machine pools that you created.

## <span id="machines_do_not_seem_to_run_jobs_that_are_scheduled_for_them."></span><span id="MACHINES_DO_NOT_SEEM_TO_RUN_JOBS_THAT_ARE_SCHEDULED_FOR_THEM."></span>Machines do not seem to run jobs that are scheduled for them.


1.  Check the names of the NICs on the DUT, SUT and AP machines.  They must be MessageDevice for the Ethernet and SupportDevice0 and SupportDevice1 for the WLAN NICs. If not rename them manually.

2.  Make sure that for each machine in the pool, status is **Ready**.

    1.  Open the **Job Monitor** window in HLK Manager.

    2.  In the **Machine Pool** tab, select the machine pool that you expect to be running jobs.

    3.  If a machine's status is not **Ready**, right-click the machine, point to **Change Status**, and then click **Reset**.

    4.  After a few minutes, refresh the screen and the status will change to **Ready**.

3.  Schedule and start the jobs again.

## <span id="Problems_with_installing_the_Test_SoftAP_driver_on_the_topology__Device_Manager_reports_code_52"></span><span id="problems_with_installing_the_test_softap_driver_on_the_topology__device_manager_reports_code_52"></span><span id="PROBLEMS_WITH_INSTALLING_THE_TEST_SOFTAP_DRIVER_ON_THE_TOPOLOGY__DEVICE_MANAGER_REPORTS_CODE_52"></span>Problems with installing the Test SoftAP driver on the topology: Device Manager reports code 52


Do not install the x64 Test SoftAP driver before installing the HLK client. When the HLK client is installed, the Root Certificate is installed. Because the Test SoftAP driver signing depends on installation of the Root Certificate, the device manager reports device code 52.

## <span id="Configuring_NDISTest_for_stand-alone_execution"></span><span id="configuring_ndistest_for_stand-alone_execution"></span><span id="CONFIGURING_NDISTEST_FOR_STAND-ALONE_EXECUTION"></span>Configuring NDISTest for stand-alone execution


Installing NDISTest separate from HLK Studio enables you to execute individual tests. A DUT, SUT, and Test SoftAP need to be configured to enable stand-alone execution.

>[!NOTE]
>  
All test machines must use the same processor architecture.

>[!NOTE]
>  
To troubleshoot the NDISTest, try attaching a debugger to the test machine.

 

## <span id="Configuring_a_Support_Device_Under_Test__SUT_"></span><span id="configuring_a_support_device_under_test__sut_"></span><span id="CONFIGURING_A_SUPPORT_DEVICE_UNDER_TEST__SUT_"></span>Configuring a Support Device Under Test (SUT)


1.  Copy all NDISTest binaries and sub directories from the following HLK controller:

    \\\\&lt;ControllerName&gt;\\tests\\&lt;architecture&gt;\\nttest\\nettest\\ndis\\ndistest.net\\

    &lt;ControllerName&gt; is the name of the HLK controller computer and &lt;architecture&gt; is either **x86** (for x86-based processors) or **amd64** (for x64-based processors).

2.  Launch NDISTest.exe from the install directory. When the main form opens, select **Server** from the **File** menu to launch the server form.

3.  Select the message device from the **Message Device** list. This device must be IP-enabled and on the same subnet as the client message device that will be set up later.

4.  Select SUT device(s) from **Support Devices**. The support device selected on this server from will be visible to the client after the server is started.

5.  Select the "server" job from **Jobs**. This is the server side test that will be launched after you click the start button.

After all the options have been selected, click **Start** to start the server.

## <span id="Configuring_a_Test_Software_Access_Point__Test_SoftAP_"></span><span id="configuring_a_test_software_access_point__test_softap_"></span><span id="CONFIGURING_A_TEST_SOFTWARE_ACCESS_POINT__TEST_SOFTAP_"></span>Configuring a Test Software Access Point (Test SoftAP)


1.  Copy all NDISTest binaries and sub directories from the following HLK controller:

    \\\\&lt;ControllerName&gt;\\tests\\&lt;architecture&gt;\\nttest\\nettest\\ndis\\ndistest.net\\

    &lt;ControllerName&gt; is the name of the HLK controller computer and &lt;architecture&gt; is either **x86** (for x86-based processors) or **amd64** (for x64-based processors).

2.  Install SoftAP driver for both of the Atheros WLAN devices on the Test SoftAP. You can install this driver from Device Manager, which you can open by running **devmgmt.msc** from a command prompt. Complete the following step:

    -   In Device Manager, install the driver for SoftAP stations from \\\\&lt;ControllerName&gt;\\Tests\\&lt;architecture&gt;\\nttest\\nettest\\ndis\\NDISTest.net\\SoftAPMiniport\\

        &lt;ControllerName&gt; is the name of the HLK controller computer and &lt;architecture&gt; is either x86 (for x86-based processors) or amd64 (for x64-based processors), depending on the processor architecture of the HLK client machine that have the SoftAP devices.

3.  Launch NDISTest.exe from the install directory. When the main form opens, select **Server** from the **File** menu to launch the server form.

4.  Select the message device from the **Message Device** list. This device must be IP-enabled device and on the same subnet as the client message device that will be set up later.

5.  Select the AP device(s) from **AP Devices**. AP devices selected on this server will be visible to the client after the server is started.

6.  Select the "server" job from **Jobs**. This is the server side test that will be launched after you click the start button.

After all the options have been selected, click **Start** to start the server.

## <span id="Configuring_the_Device_Under_Test__DUT_"></span><span id="configuring_the_device_under_test__dut_"></span><span id="CONFIGURING_THE_DEVICE_UNDER_TEST__DUT_"></span>Configuring the Device Under Test (DUT)


1.  Copy all NDISTest binaries and sub directories from the following HLK controller:

    \\\\&lt;ControllerName&gt;\\tests\\&lt;architecture&gt;\\nttest\\nettest\\ndis\\ndistest.net\\

    &lt;ControllerName&gt; is the name of the HLK controller computer and &lt;architecture&gt; is either x86 (for x86-based processors) or amd64 (for x64-based processors).

2.  Launch NDISTest.exe from the install directory. When the main form opens, select **Client** from the **File** menu to launch the client form.

3.  Select the test target from the **Test Target** list. For network device, this test target should be **Miniport**.

4.  Select the test device from the **Test Device** list. This must be a vendor-specific test device.

5.  Select a message device from the **Message Device** list. This should be an IP-enabled device that is on the same subnet as the server message device. After the message device has been selected, the AP device section should be displayed and the server AP device should be available in the list.

6.  Select a support device from **Support Devices**. This must be a vendor-specific support device.

7.  Select an AP device from **AP Devices**. This must be the AP device that was select on the server side.

8.  Select the tests from the **Jobs** section that will be run after the client is launched.

After all the options have been selected, click Start to start the client. Any jobs that were selected will begin execution. Test results will be stored on the client in the following logging sub-folder:

&lt;NDISTestRootFolder&gt;/logs/&lt;AdapterName&gt;/

## <span id="Configuring_Client_Packet_Capture"></span><span id="configuring_client_packet_capture"></span><span id="CONFIGURING_CLIENT_PACKET_CAPTURE"></span>Configuring Client Packet Capture


1.  Configure a test topology for stand-alone execution. For more information, go to "Configuring NDISTest for stand-alone execution."

2.  Setup a second SUT. For more information, go to "Configuring a Support Device Under Test (SUT)."

3.  Launch NDISTest.exe from the install directory. When the main form opens, select **Debug** from the **View** menu to launch the **Packet Capture** section on the client.

4.  Select a Capture device from **Packet Capture**. This must be a Support device that was selected on the server side.

5.  From **Jobs**, select the tests that will be run after the client is launched.

6.  After all of the options have been selected, click **Start** to start the client.

7.  Packet captures corresponding to the Tests will be generated on the Server with the capture device. The logs will be in the following logging sub-folder:

    &lt;NDISTestRootFolder&gt;/logs/&lt;AdapterName&gt;/

## <span id="Troubleshooting_when_the_Packet_Capture_section_does_not_show_up_on_client"></span><span id="troubleshooting_when_the_packet_capture_section_does_not_show_up_on_client"></span><span id="TROUBLESHOOTING_WHEN_THE_PACKET_CAPTURE_SECTION_DOES_NOT_SHOW_UP_ON_CLIENT"></span>Troubleshooting when the Packet Capture section does not show up on client


Verify that the message center user interface is closed. If the NDISTest user interface is not maximized, the **Packet Capture** section may be hidden behind the message center user interface.

## <span id="i_want_to_open_a_bug._what_should_i_include_in_the_bug_"></span><span id="I_WANT_TO_OPEN_A_BUG._WHAT_SHOULD_I_INCLUDE_IN_THE_BUG_"></span>I want to open a bug. What should I include in the bug:


-   Create a .hlkx package containing the failed tests – see the “Creating a Package” section and attach it to the bug.

-   Failing Logs –Please gather the ndistest logs from the test run and include them with the package in the bug.  The logs can be found by doing the following:

1.  Open the HLK Manager

2.  Choose **Explorers&gt; Job Monitor**

3.  Choose the **Machine Pool** that you scheduled the tests on.

4.  In the right pane choose the DUT machine.

5.  Under **Job Execution Status** right click the Job name of the test you ran and select **Browse Job logs**.

6.  This will open up an explorer window with an AP, Server, and Test directories.  Zip these directories and attach them to the bug.

## <span id="How_do_I_reset_my_machines_after_a_failed_run___"></span><span id="how_do_i_reset_my_machines_after_a_failed_run___"></span><span id="HOW_DO_I_RESET_MY_MACHINES_AFTER_A_FAILED_RUN___"></span>How do I reset my machines after a failed run?


Below is a chart with common problems and solutions.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Symptom</strong></p></td>
<td><p><strong>Solution</strong></p></td>
</tr>
<tr class="even">
<td><p>The VAN UI doesn’t show any networks</p></td>
<td><p>1</p></td>
</tr>
<tr class="odd">
<td><p>When I connect my WLAN device to a DHCP enabled network I don’t get an IP.</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>I get strange &quot;Back Channel&quot; failures</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>The (SUT, DUT, or AP) machine crashed and now all tests are failing</p></td>
<td><p>1,2,3</p></td>
</tr>
<tr class="even">
<td><p>NDISTest isn’t auto finding my test adapter when running through the HLK</p></td>
<td><p>3</p></td>
</tr>
<tr class="odd">
<td><p>The HLK test is failing to populate either a MessageDevice or SupportDevice</p></td>
<td><p>3</p></td>
</tr>
<tr class="even">
<td><p>I updated my HLK Controller and not my clients and now I am seeing strange crashes and failures that I have never seen before</p></td>
<td><p>When moving to a new controller you should also rebuild your clients. In the event that is not feasible you will need to remove <strong>ndprot630.sys</strong> from all three machines and athr.sys and softap.sys from the AP machine. All these files are in the c:\windows\system32\drivers directory. <strong>Ndprot630.sys</strong> will be automatically re-loaded when NDISTest is run, but not overwritten. <strong>ather.sys</strong> and <strong>Sofap.sys</strong> will need to be copied over from the new controller.</p></td>
</tr>
<tr class="odd">
<td><p>My physical AP's don’t seem to be working like before</p></td>
<td><p>You may have to reset/reboot your physical ap. If you factory reset it make sure you set the channel and radio per the setup instructions.</p></td>
</tr>
<tr class="even">
<td><p>I have tried all the steps above but nothing worked</p></td>
<td><p>If you have tried the above steps and are still seeing issues you can uninstall then reinstall the WLAN adapter. Make sure when you are done to rename the adapter SupportDevice0.</p></td>
</tr>
</tbody>
</table>

 

## <span id="related_topics"></span>Related topics


[Device.Network Testing](device-network-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







