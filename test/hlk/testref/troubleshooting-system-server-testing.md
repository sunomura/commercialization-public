---
title: Troubleshooting System Server Testing
description: Troubleshooting System Server Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3ee40494-a414-4469-9bf6-229c78d1d7ea
---

# Troubleshooting System Server Testing


To troubleshoot issues that occur with the Windows Hardware Lab Kit (Windows HLK) System.Server tests, follow the steps that are described in this article.

In this article:

-   [General system server troubleshooting](#gen)

-   [Troubleshooting failed system server tests](#failed)

-   [Server stress tests](#stress)

-   [Using virtual machines (VMs) in the test environment](#vm)

## <span id="gen"></span><span id="GEN"></span>General system server troubleshooting


1.  Review the following topics for help in server testing:

    -   The Windows HLK topics that are specific to the device, driver or system test.

    -   [Server Testing Overview](server-testing-overview.md)

    -   [System Server Testing Prerequisites](system-server-testing-prerequisites.md)

    -   [Test Server Configuration](test-server-configuration.md)

    -   [LoadGen Server Stress - Run First - Set Machine Policies](318d804e-aa8f-4ffb-8ce2-963cea2f1a40.md)

    -   [LoadGen Server Stress - Start Test for Server](6e9adb95-fca5-4e15-a255-bc96c0d12aa9.md)

    -   [LoadGen Server Stress - Run Last - Reset Machine Policies](8cb4f87c-d2a4-4d90-92a7-edd016ccdeac.md)

    -   [Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md).

2.  For server device and driver testing, make sure that the system under test (SUT) is configured as follows:

    -   The correct version of Windows® is installed.

    -   The Server Core option is installed.

    -   The SUT has a minimum of four cores\\logical processors.

    -   The SUT has a minimum of 6 GB of RAM installed.

    -   For storage device testing, you might need two device instances that have storage drives if the storage device is a boot device.

3.  If you get an error that Windows HLK Studio could not add targets to the project, reselect the target, close Windows HLK Studio and then restart Windows HLK Studio. The error means that the data is not refreshed.

4.  The Sysparse process directly runs the gatherer DLLs. A second process, Asset Configuration Manager Engine (ACME), watches for hardware changes and alerts the system if one or more hardware changes occur. ACME waits until a timeout occurs or for frequent hardware change reports to stop before it initiates the subscribed gatherers.

    Some tests cause hardware changes throughout the test run. This causes Sysparse to run regularly. Sysparse can consume large amounts of memory, which is caused by the gatherers that are running and collecting data. Sysparse should not interfere with testing because in most cases, the tests do not verify performance.

5.  Make sure that the system upon which the Windows HLK Controller is installed has adequate hardware capabilities to meet the test demands. See [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md) for a description of these hardware requirements. As the number of devices and systems that are being tested increases, you might need to add more processors, memory, or storage.

## <span id="failed"></span><span id="FAILED"></span>Troubleshooting failed system server tests


If a test fails, follow these steps:

1.  If the failure occurs within minutes of the test startup, it usually means something was not configured properly. Reconfirm the test environment set up.

2.  If the test ran, there should be a log file called Srvlog.xml in the Windows HLK Controller. Follow these steps:

    1.  In Windows HLK Studio, open **Job Monitor**.

    2.  Browse to the machine pool of the scheduled test.

    3.  In the **Job Execution Status** pane, select **Loadgen Server Stress – Start Test for Server**.

    4.  In the **Task Execution Status** pane, right-click **RunJob –Launch Server Logo Kit** and select **Child Job Result**.

    5.  Return to the **Job Execution Status** pane and select **Launch Server Logo Kit**.

    6.  In the **Task Execution Status** pane, right click **Start LogGen task** and select **View Task Log**. The log is parsed from the original Loadgen log and contains only errors and passes.

    7.  To retrieve the original Loadgen text log, repeat steps 1-5 and then click right-click **Launch Server Logo Kit** and select **Browse Job Logs**. This opens the log share on the Windows HLK Controller; the Loadgen log file srv.log is in the share.

    8.  Drag and drop the srv.log file into Notepad.

    9.  In Notepad, scroll to the bottom of the file.

    10. From the bottom up, search for the string *“Error -”*. The text in the same line will describe the failure. You might have to search several times to find the cause of the failure. The information in log file provides only a high level indicator of what failed.

### <span id="loadgen"></span><span id="LOADGEN"></span>Loadgen requests more clients

If existing clients cannot generate enough stress against the SUT, Loadgen asks for more stress clients (SCs). This feature is intended to accommodate large servers, and the possibility of some SCs failing in the middle of a run. In general, you should start with eight SCs. The stress level should stabilize in the first three to four hours of the test. If more clients are needed, you will generally see the pop-up in the master controller (MC) in that time frame. You will have sixty minutes to add a new client or the test will terminate and fail.

>[!NOTE]
>  
You cannot add more machines to a machine pool after a submission has started. If you start the test by using less than eight clients, make sure that you have additional clients in the machine pool before you start to test.

 

If Loadgen asks for more clients after four hours of testing, it probably means that something has failed. One or more of the existing clients dropped out, network connectivity issues have occurred, or another issue is preventing the SUT from sensing the required 40% utilization load. This can be an issue of the NIC driver in combination with the network speed, or the driver’s implementation of performance monitor counters upon which the Loadgen MC depends.

In this case, try the following troubleshooting steps:

1.  To rule out a transient hardware failure in the NIC, use a different NIC that is the same model and manufacturer.

2.  Use a different model NIC from the same manufacturer, but which uses the same driver.

3.  Use a NIC and driver from a different manufacturer driver.

4.  If one or more NICs are installed directly on to the system board, go into the hardware system setup and disable the NIC at that level so that Windows does not detect it; then use a different device and driver for the testing.

5.  If multiple NICs are installed directly on to the system board, and you cannot install an additional device into a PCI Express slot, go into the hardware system setup and disable all but one of the NICs so that Windows does not detect them.

>[!NOTE]
>  
Each detected NIC must be stressed during the test. This requires that each NIC has SCs on a separate physical network segment.

 

Switches that have advanced features built in to them can interfere with the test in various ways. For example:

-   A switch can have the capability to slow down the ports in the switch if it detects dropped packets or other errors on one port. If a 10GigE NIC on the SUT is intended to receive the traffic that would result from all ports being slowed down to 1 GigE, the Loadgen test cannot reach the requisite 40% network bandwidth utilization level that is needed to pass the test.

-   A switch can route traffic or segment the network in response to rules and logic that internal to the switch (such as load balancing, redundancy, quality of service (QoS), mirroring, duplex versus. simplex operation, adaptive or intelligent bridging, port prioritization, or MAC filtering), that can impact the network bandwidth utilization level on a NIC.

### <span id="error0x80004005"></span><span id="ERROR0X80004005"></span>Error=0x80004005

If you receive the following error: **Main::RunMain:: Test Check**, Spsrv stopped and did not pass required pass percentage (100) (Error=0x80004005). In this case, perform the following steps:

1.  Close the Windows HLK Studio.

2.  Change the SUT computer name to 15 characters or less.

3.  Reboot the SUT.

4.  Open Windows HLK Studio and re-run the **LoadGen Server Stress – Start Test for Server** test.

## <span id="stress"></span><span id="STRESS"></span>Server stress tests


When you perform server stress tests, make sure that the network infrastructure that connects the SUT to the SCs and the MC can perform at the level of the network interface card (NIC) in the SUT. If an SUT has one or more 10GigE NICs, the SCs and the network infrastructure must meet that level of performance.

Make sure that the network infrastructure that connects the DHCP, DNS, Active Directory, Windows HLK Controller, Windows HLK Studio, SUT, SCs and MC is operating correctly. All systems must communicate with each other by using a host name or IP address. This can be confirmed by using a simple ping test.

Make sure that the DHCP, DNS and Active Directory Server(s) are functioning correctly. There should be no stale DNS records. The DHCP server should be authorized to operate on the network, the configuration must be correct, the DHCP scopes must be correct, there should be no incorrect multi-homing, and there should be no errors in the DHCP system event log. The Active Directory domain controller should report no errors and the time service must be synchronized across all systems.

## <span id="vm"></span><span id="VM"></span>Using virtual machines (VMs) in the test environment


There are no known issues by the DHCP, DNS, AD, and other systems being in a VM. Issues can occur by having SCs running in a VM. These issues are typically related to network bandwidth load generation. To avoid problems, make sure the following configuration is set up:

-   Each SC VM must have a dedicated physical NIC to place load on the network connected to the SUT NIC.

-   At a minimum, you must have physical NICs that are affinitized to the SC VMs that are capable of at least two times the maximum bandwidth of the SUT NIC.

-   Make sure that the physical system(s) that are used for SC VMs is not overstressed by high levels of CPU utilization, and that there is adequate physical memory for all VMs.

## <span id="related_topics"></span>Related topics


[System.Server Testing](system-server-tests.md)

 

 







