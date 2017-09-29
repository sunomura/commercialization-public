---
title: Wireless LAN (802.11) Testing Prerequisites
description: Wireless LAN (802.11) Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e8a87fcd-b289-45b4-bdb8-1530ef8bf558
---

# Wireless LAN (802.11) Testing Prerequisites


This topic describes the process to test a Wireless LAN (WLAN) device to make sure that it functions correctly with Windows®. These procedures use the Microsoft Windows Driver Kit (WDK) and Windows Hardware Lab Kit (Windows HLK). To comply with the WLAN Windows Hardware Certification Program, you must run all of the tests that Windows HLK identifies as being required for the device. We also recommend that you work through the tests in order by the following levels: “Basic”, “Functional”, “Reliability”, and “Certification.”

>[!NOTE]
>  
For a driver to pass testing and obtain Windows Hardware Certification, you must use the latest version of the WDK to compile the driver.

>[!NOTE]
>  
WLAN Windows HLK tests that use software-based access points are exclusively supported by using specific Atheros WLAN NICs. Windows HLK customers who test WLAN drivers must use two Atheros WLAN adapters that are installed in the SoftAP Machine to complete their submissions. Only two devices have been specifically tested at the time of Windows 8.1 release: Dlink DWA-552 and Dlink DWA-556. Additional models might have worked in the past and might continue to work, but cannot be guaranteed. If you have questions about this, please contact us at wlanndt@microsoft.com.

 

The tests to run depend on the capabilities of the device or system that you are testing. For devices that are running on Windows 7, the tests take 13 to 15 hours to run. For devices that are running on Windows 8, the tests take 30-32 hours to run. For devices that are running on Windows 8.1, tests take approximately 36-40 hours to run. These times represent fully passing results. Failures in any test or reboots due to crashes add additional time to the tests. These times can vary slightly by platform and performance of individual machines that are used in the tests.

**In this topic:**

-   [Windows HLK Setup for WLAN Device Testing](#hcksetup)

-   [Prepare for Wireless LAN (802.11) Testing](#prepwlan)

-   [Run Wireless LAN (802.11) tests for Certification](#run)

-   [View Results and Log Files](#view)

-   [Create a Package](#pkg)

-   [Notes and Troubleshooting for RT-N66U firmware](#notests)

-   [AP Firmware Troubleshooting](#ap)

## <span id="hcksetup"></span><span id="HCKSETUP"></span>Windows HLK Setup for WLAN Device Testing


A Windows HLK setup for WLAN device testing consists of the following nine components:

-   A computer that is running Windows HLK Studio. Through this application, you can control and configure the Windows HLK Controller to send jobs to the Windows HLK clients in the Windows HLK system pool. All requirements for a WLAN Windows HLK submission are enforced when the Windows HLK test execution job is configured.

-   A Windows HLK Controller computer. This computer must run Windows Server 2008 R2. (In many cases, this computer can be the same computer that runs Windows HLK Studio.) This component reserves Windows HLK clients in the system pool for a test job. In *Figure 1 WLAN Setup*, the Windows HLK Controller and Windows HLK Studio machine are represented as one machine.

-   A Device Under Test (DUT), which is a computer that is running the desired operating system and architecture for which you are seeking certification, and on which the device for certification is installed. You must install the Windows HLK Client on this machine.

-   A Support Device Under Test (SUT), which is a computer that is running the same version and processor architecture of Windows as the DUT. The SUT must have a WLAN device installed that is capable of passing all certification tests and has drivers properly loaded. We recommend that you use the same device in both the DUT and SUT.

-   A SoftAP Machine (also known as AP Controller), which is a machine that is running the same processor architecture of Windows as the DUT and SUT. If the DUT is running Windows RT, the SoftAP machine must be running a 32bit version of Windows. The SoftAP Machine should be running Windows 8.1 in all cases. This machine must have two compatible Atheros WLAN adapters installed (Dlink DWA-552 is recommended) and two Ethernet adapters installed, one of which must be capable of reaching 1Gbps. You must install the Windows HLK Client on this machine.

-   Two ASUS RT-N66U routers. See *Figure 1 WLAN Setup* for configuration details and physical arrangement of the routers.

-   An 802.11AC capable router/access point. See *Figure 1 WLAN Setup* for configuration details and physical arrangements. The 802.11AC router must support at least the same number of antennas, spatial streams, and max throughput as the DUT. We recommend that you use an ASUS RT-AC66U for testing. Using an 802.11AC router that does not support enough throughput will fail the 802.11 performance tests. You can use the 2.4Ghz side of the 802.11AC router as the AP for Wlan L1 and Device Fundamental tests. You should configure this with WPA2 Personal and an AES cipher. The defaults for these tests use an ssid of **kitstestssid** and a password of *password*.

-   An 802.11w-capable access point. This item is unchanged from previous WLAN Windows HLK releases and the previously used access point can be used.

>[!NOTE]
>  
Windows Vista and earlier versions of Windows are deprecated and are not supported for any role in the test configuration.

 

The following table summarizes the configurations:

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Test Client</th>
<th>Windows 8.1 Logo</th>
<th>Windows RT Logo</th>
<th>Windows 8 Logo</th>
<th>Windows 7 Logo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DUT</p></td>
<td><p>Windows 8.1</p></td>
<td><p>Windows RT</p></td>
<td><p>Windows 8</p></td>
<td><p>Windows 7</p></td>
</tr>
<tr class="even">
<td><p>SUT</p></td>
<td><p>Windows 8.1</p></td>
<td><p>Windows RT</p></td>
<td><p>Windows 8</p></td>
<td><p>Windows 7</p></td>
</tr>
<tr class="odd">
<td><p>SoftAP</p></td>
<td><p>Windows 8.1</p></td>
<td><p>Windows 8.1 32-bit</p></td>
<td><p>Windows 8</p></td>
<td><p>Windows 7</p></td>
</tr>
</tbody>
</table>

 

*Figure 1 WLAN Setup* shows the WLAN setup:

![wlan setup](images/wlansetup.png)

## <span id="prepwlan"></span><span id="PREPWLAN"></span>Prepare for Wireless LAN (802.11) Testing


**RT-N66U (AP1 & AP2) Preparation:**

-   The only current supported device for AP1 and AP2 is the ASUS RT-N66U.

-   Make sure that you are using 3.0.0.4.354 or later version firmware. New units might have a compatible firmware version directly out of the box. (We recommend that you keep a copy of working firmware available.)

-   You must pre-configure AP1 and AP2 before you connect them. You can use any of the machines or a separate machine to perform the configuration. During this process, make sure that the computer is connected to the RT-N66U LAN ports by using the Ethernet network only.

-   When you set up a new AP for the first time, we recommend that you skip the Configuration wizard on the aps by navigating directly to: http://192.168.1.1/index.asp .

-   The WAN/Internet ports on both AP1 and AP2 must be configured under the WAN section of Advanced Settings by using a connection type of Static IP. The static IPs that are used must be in the subnet that is being used for gigabit switch 2. (For example: 192.168.100.0/255.255.255.0) Do not use a static IP address that falls within an IP subnet to which the DUT and SUT connect. Switch 1 and switch 2 must use separate and non-overlapping IP subnets.

-   The WAN settings page requires that the Default Gateway, DNS Server1, and DNS Server2 fields are filled out. For ease of configuration, we recommend that you enter the static IP address of Nic 2 on the AP controller (which must be in the same subnet range as the WAN IP Setting).

-   You must disable the firewall in the **Firewall** section in **Advanced Settings**.

-   You must enable Telnet on the **System** tab in the **Administration** section of **Advanced Settings** on both AP1 and AP2.

-   For debugging purposes from the AP Controller, we highly recommend that you enable web access from WAN on the **System** tab in the **Administration** section of **Advanced Settings** on both AP1 and AP2.

    >[!IMPORTANT]
    >  
    When the tests run for the first time, the tests disable all LAN ports on both RT-N66U routers. This is expected. If you want to connect to the APs to verify settings during the testing, use the AP controller and connect over the WAN port by using the provisioned port. The tests enable the LAN ports of each AP as needed during testing. If you need to connect to a LAN port for testing, stop the tests from running and manually power off and on the AP. This action re-enables the LAN ports until the next test starts.

     

-   You can troubleshoot the tests’ ability to connect to the APs by using Telnet.exe to connect to both routers on the WAN IP address from the AP-Controller. If you cannot connect to either AP from the AP-Controller by using the WAN IP address, the username of admin, and password that you configured (default password is admin), the tests cannot connect and will fail.

-   These preparation steps do not apply to the 802.11 AC router in the setup. For the 802.11AC router, configure it to match the maximum bandwidth and spatial streams that your device supports.

**Topology Configuration and Preparation:**

-   Each line in *Figure 1. WLAN Setup* represents a connected physical Ethernet cable.

-   AP1 and AP2 must be connected to Gigabit Switch 2 by using the WAN/Internet port.

-   The Ethernet cable between the LAN ports on AP1 and AP2 is required. The connection can be between any LAN port on AP1 to any LAN port on AP2.

-   The AP Controller requires two LAN adapters. One LAN adapter (Nic 1) connects to Gigabit Switch 1 (or equivalent), and the second lan adapter (Nic 2) connects to Gigabit Switch 2. Nic 2 MUST be a gigabit adapter and cannot be a USB Ethernet adapter. This adapter is used to measure 802.11AC performance. The IP address on Nic 1 must be assigned by using DHCP. The IP address on Nic 2 must be statically assigned. This assignment method enables the tests to identify the adapters.

-   Do not use the same IP address space for Gigabit switch 1 and Gigabit Switch 2. They must contain IP/subnet masks that do not overlap. Further, you must use DHCP for address assignment on Gigabit Switch 1 (this can be the same network you typically use for other HLK testing) and the IP range for Gigabit Switch 1 must NOT be in the range 192.168.x.x. We suggest that you use 192.168.100.\* for the addressing on gigabit switch 2.

-   The DUT, SUT, AP Controller, and HLK Controller need a hard-wired LAN connection to gigabit switch 1. This cannot be the same switch as gigabit switch 2. A DHCP service must provide IP addresses on gigabit switch 1. If Nic 1 on the AP controller is not assigned an IP address by using DHCP, tests will fail.

-   Each static IP connected to gigabit switch 2 must be unique.

-   *Figure 1. WLAN Setup* includes some notes to keep regarding IP addresses, SSIDs, passwords, etc. You are prompted for these values during the test runs.

-   Both wireless adapters that are installed in the DUT and SUT must fully support Wifi-Direct. We recommend that you use the same device in both DUT and SUT, or use at least a Windows 8-certified device and driver in the SUT if the DUT is running Windows RT.

-   For devices that support 802.11AC, both the DUT and SUT must contain the same wireless adapter. If the DUT is Windows RT, both must support 802.11AC.

-   Install Network Monitor (Netmon) version 3.4 or greater on the AP controller and reboot if you are testing Windows WLAN feature NDIS Packet Coalescing. This requirement is moved from SUT to AP controller with HCKQFE \#4. Netmon is specifically required for the D0 Coalescing Feature Test.

**AP Controller Configuration:**

-   The AP Controller/SoftAP machine requires two Atheros-based WLAN adapters. We recommend a Dlink DWA-552 device. If you require PCI-Express, Dlink DWA-556 devices also work. The driver that is used for software-based AP testing is the same as for Windows 8 testing; however, these adapters are also used in Wifi-Direct testing in Windows 8.1. If your existing SoftAP machine WLAN cards from Windows 8 properly support Wifi-Direct, you can continue to use them.

-   You do not need to manually install the software-based AP driver on the Atheros adapters during setup. The driver will be automatically installed and uninstalled during the testing process.

-   The AP Controller requires 2 Ethernet adapters. One of these must support gigabit speeds.

-   The Ethernet adapter that is connected to gigabit switch 2 must be a gigabit Ethernet adapter. This requirement ensures unrestricted performance testing.

-   The architecture of the AP controller operating system must match the architecture of the DUT operating system (32bit for x86, 64bit for AMD64). For Windows RT DUT devices, use a 32bit operating system on the AP controller.

-   The AP Controller does not require a single-processor architecture. This detail is adjusted by the test automation.

**HLK Pool Configuration:**

After you configure the test topology, prepare the test systems for WLAN device testing by performing the following steps:

1.  Set up the following machine configurations by using the previous configuration instructions:

    -   One test device on the DUT.

    -   One test device on the SUT.

    -   Two Atheros chipset devices on the AP Controller.

    -   Two Ethernet adapters on the AP Controller

    -   Windows HLK Studio and Windows HLK Controller.

2.  Based on the operating system for which you are testing the device, install operating system builds on the Windows HLK clients (three test computers namely DUT, SUT and SoftAP machine) as described in the previous section.

3.  Install HLK controller and HLK studio machine on Windows Server 2008 R2 machine. For more information see [Step 2: Install Client on the test system(s)](..\getstarted\step-2--install-client-on-the-test-system-s-.md).

4.  Install HLK clients on three test computers namely DUT, SUT and SoftAP machine. For more information see the **Windows Hardware Certification Step-by-Step Guide**. Note that when the DUT is a Windows RT machine, the AP machines must be running a 32bit operating system. When the DUT is a Windows RT machine, the HLK client should be installed from (\\\\&lt;HCKcontroller&gt;\\HCKInstall\\WoAClient\\setup.exe), where &lt;*HCKcontroller*&gt; is the name of the Windows HLK Controller.

5.  On the Windows HLK Controller click **Start**, click **All Programs**, click **Windows Kits**, click **Hardware Certification Kit**, and click **Windows HLK Studio**.

6.  Click **Configuration** and then click **Machine Management**.

7.  Click **Create Machine Pool**.

8.  Type the machine pool name in the **New Pool** field and then press **Enter**. The new machine pool should appear as a node under **$ (Root)**.

9.  Select the **Default pool.** The Windows HLK Client machines should be listed in the **Machines** list.

10. Press and hold the **CTRL** key and click each of the three defined machines to select all three machines.

11. Drag the three selected machines to the newly created machine pool.

12. In the new machine pool, right-click the three machines. Click **Change Machine Status** and then click **Reset**. The machines will change from a **Not Ready** state to an **Initializing** state and then to a **Ready** state. During the initialization process, devices on the machine are enumerated and cataloged. It is important for all devices to have been installed by this point.

13. You can configure additional pools on one Windows HLK Controller by replicating the entire topology and restarting with step 4

14. If you are using a debugger machine with each topology (in the case of multiple topologies), you can install separate copies of the Windows HLK Studio on additional machines so that more than one tester can share the same controller. Use separate projects for each topology/pool and only use one topology per pool.

## <span id="run"></span><span id="RUN"></span>Run Wireless LAN (802.11) tests for Certification


The following procedure demonstrates how to run the WLAN device tests:

1.  Open the Windows HLK Studio.

2.  On the **Project** tab, click **Create Project** and name the project.

3.  Click the **Selection** tab.

4.  Select your new machine pool in the dropdown in the upper left and click **Device Manager**. The list should populate with the names of all the devices that are installed on the machines in that pool.

5.  In the list, locate the WLAN driver under test and check the box next to it.

    >[!NOTE]
    >  
    There might be more than one WLAN driver listed. Make sure you check the one that is on the DUT. The machine name is listed in the right column.

     

6.  Click the **Tests** tab – by default, all the available certification tests that are applicable to selected device will display.

7.  You can filter the displayed list by clicking **View by** and then selecting additional options, such as **Basic**, **Functional**, or **Reliability**.

    Only **Certification** tests are required for the certification process; however, running **Basic** and **Functional** tests provides a specific set of functionally important tests.

8.  Select the test to run by checking the box on the left next to it. Click **Run Selected**.  You are prompted to add any additional parameters. (You can also check the box next to multiple tests.)

9.  Not all parameters are used for all tests. Only the parameters that are necessary for the selected tests are shown. You can view detailed parameter descriptions by hovering the mouse pointer over the parameter name. Many of the parameters will be derived from the topology notes mentioned above. If you press the **F1** key while a test is selected, detailed information on that test and its parameters is shown.

10. **Machine Set** section is always present for Functional and Reliability tests. This section represents the machine resources that are necessary to run the tests. You must address all "**!**" symbols before you click **OK**.

    1.  Select the first test name from the list (if there is more than one).

    2.  From the **Role** menu, select **Client** – the DUT machine should already be selected and grayed out.

    3.  From the **Role** menu, select **Support** and check the box next to the SUT Machine.

    4.  From the **Role** menu, select **AP** and check the box next to the AP Machine.

11. Click OK to schedule. You can monitor the detailed progress of the tests in Windows HLK Manager, or simply watch as each test result displays in the **Status** column.

## <span id="view"></span><span id="VIEW"></span>View Results and Log Files


Results and logs can be viewed through Windows HLK Manager or Windows HLK Studio.

In Windows HLK Manager, click **Explorers** and then click **Job Monitor**.

When the client machines complete test jobs, you can gather information from the **Job Execution Status** frame by right-clicking a job and viewing errors, job reports, or result reports. You can also click **Browse Job Logs** to access NDISTest results.

In HLK Studio, click the **Results** tab. View the **Status** column to monitor the results of each test. You can choose each column to sort the results. If a test passes, you will see a green checkmark; if it fails, you will see a red X. For more detailed information on viewing logs, see [Step 7: View test results and log files](..\getstarted\step-7-view-test-results-and-log-files.md).

## <span id="pkg"></span><span id="PKG"></span>Create a Package


After passing all of the necessary tests, you are ready to create an .hlkx submission package for certification.

Windows HLK Studio supports package creation, so you don't have to use a separate submission tool. The package creation feature lets you add necessary resource files to complete the certification. For detailed instructions on how to create a package, see [Step 8: Create a submission package](..\getstarted\step-8-create-a-submission-package.md).

## <span id="notests"></span><span id="NOTESTS"></span>Notes and Troubleshooting for RT-N66U firmware


The tests are designed to work against RT-N66U vB1 APs that have at least firmware version 3.0.0.4.354. Purchases of new RT-N66U devices might meet this requirement with no firmware upgrades required. If your purchased devices meet this requirement, you can start testing as soon as you complete the configuration instructions described in this topic. Devices that come with a later version of firmware are expected to be compatible. Downgrade to the version 3.0.0.4.354 only in the case of confirmed problems or communication from Microsoft.

We highly recommend that you save a backup of the required software to recover the Aps, as well as a few versions of firmware. Make sure you have backup copies of the following:

-   ASUS Firmware Restoration Utility

-   ASUS RT-N66U B1 Firmware Version 3.0.0.4.354 (if available)

-   Current and/or latest version of ASUS RT-N66U B1 Firmware

You can download these items as follows:

1.  Go to http://support.asus.com and click **Download**.

2.  Type **RT-N66U** and then click **Search**.

3.  Click **RT-N66U (Ver.B1)** (or applicable version that matches your version).

4.  Next to **OS:**, select **Windows 8** from the OS dropdown menu. Match the architecture to that of the computer you are using for any updates to the APs.

5.  Click **+** next to **Utilities**, and download the latest available **Firmware Restoration** utility.

6.  Click **+** next to **Firmware**, and download **ASUS RT-N66U B1 Firmware Version 3.0.0.4.354**.

    You can also download the latest available firmware for future use.

## <span id="ap"></span><span id="AP"></span>AP Firmware Troubleshooting

>[!WARNING]
>  
Applying new firmware to consumer devices can sometimes, although rarely, cause permanent damage. You must read the device manual that came with your router and be careful when you flash new firmware on a device. Detailed steps, especially around the 30-30-30 reset, are required before flashing.

 

The most reliable way to install firmware on an RT-N66U device is by using the Firmware Restoration Utility. You might also be able to upgrade firmware by using the web interface. Consult the device manual for instructions. To upgrade firmware by using the restoration tool, the following steps are required. (These steps can also be found in your manual under Firmware Restoration.

1.  Remove power from the device.

2.  Press and hold the reset button on the device.

3.  Turn on/plug in the device keeping the reset button held for 8 seconds.

4.  Release the reset button when the power LED has started to slowly flash on and off.

5.  Connect one computer to one of the LAN ports on the device (do not connect any other ports during this process).

6.  Change the IP address on the computer to 192.168.1.4 with a subnet mask of 255.255.255.0 and no gateway address.

7.  Start the Asus firmware restoration utility.

8.  In the firmware restoration utility, browse for the firmware image you downloaded (version 3.0.0.4.354 or later).

9.  Click the **Upload** button.

10. If the upload is successful, multiple progress bars appear. The first progress bar shows the upload of the image to the device; additional progress bars show the overall upgrade process.

11. Do not use the device, press any buttons, or remove power while the device is being upgraded. We recommend that you leave it alone for 15 minutes.

12. After the upgrade is successful, you can remove the static IP address from the computer and access the devices web-server at http://192.168.1.1/index.asp to confirm a successful upgrade.

    >[!IMPORTANT]
    >  
    Every time that you upgrade firmware, after the device has finished the upgrade and has restarted, you should reset the NVRAM settings by performing a 30-30-30 reset. The steps for this are as follows:

     

    1.  When the device is ON and functioning, hold down the WPS button for 30 seconds.

    2.  While continuing to hold the WPS button, unplug the device and leave it unplugged for 30 seconds.

    3.  While continuing to hold the WPS button, plug the device back in and wait for an additional 30 seconds (90 seconds total).

    4.  Release the WPS button. This will cause all LEDs to flash on and off again. The device reboots and goes through a prolonged internal setup process again it becomes functional again.

13. After the router has restarted to respond to web requests, you can continue the preparation steps documented above starting here: http://192.168.1.1/index.asp .

If a device is no longer functional for any reason, or specifically because of a previous attempt to install firmware that was not compatible, try the following instructions first before you replace the device:

1.  With the device ON, perform the 30-30-30 reset instructions listed above with one modification:

2.  After the 90 seconds of holding the WPS button and removing/reapplying power, as soon as all leds on the device turn on and then off, immediately remove power as quickly as possible.

3.  Before plugging the device back in, hold in the reset button (not wps), then continue to plug in the device. Keep the reset button held for at least 8 seconds, but no more than 10.

    The power LED should be slowly flashing. If it is not, repeat the instructions above.

4.  Perform the Firmware Restoration instructions that are listed above to restore either the default firmware or newly downloaded firmware.

## <span id="related_topics"></span>Related topics


[Device.Network Testing](device-network-tests.md)

 

 







