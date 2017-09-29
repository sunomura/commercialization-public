---
title: IPsec Task Offload v2 Testing Prerequisites
description: IPsec Task Offload v2 Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d5a26f57-7d23-4b0e-ae6c-0730412ff6ec
---

# IPsec Task Offload v2 Testing Prerequisites


This section describes the IPsec Task Offload v2 testing prerequisites that you should complete before testing your network adapter using the Windows Hardware Lab Kit (Windows HLK). The Network Driver Interface Specification (NDIS) test suite includes test jobs that verify Internet Protocol Security (IPsec) functionality. If your network adapter supports IPsec, you must complete the IPsec-specific NDIS test jobs to certify your device.

>[!NOTE]
>  
This content applies to both standalone network and integrated network devices.

 

Before beginning testing, do this:

-   [Hardware requirements](#bkmk-hck-ipsec-hr)

-   [Software requirements](#bkmk-hck-ipsec-sr)

-   [Test computer configuration](#bkmk-hck-ipsec-tc)

**In this section:**

-   [IPsec Task Offload v2 Test](ipsec-task-offload-v2-testmissing.md)

-   [IPsec Task Offload v2 Manual Test](ipsec-task-offload-v2-manual-test.md)

## <span id="BKMK_HCK_IPSec_hR"></span><span id="bkmk-hck-ipsec-hr"></span><span id="BKMK_HCK_IPSEC_HR"></span>Hardware requirements


This hardware is required for testing:

-   IPsec offload–capable network adapters.

-   Two test computers that meet the Windows HLK prerequisites. For more info, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

    >[!NOTE]
    >  
    The test computers must be in the same machine pool.

     

-   Three identical LAN test devices.

-   Two 100 MB switches. Gigabit Ethernet switches are also supported.

-   An Ethernet crossover cable.

To be included in the Windows HLK, the device must pass the certification tests for both x86 and AMD64 platforms.

A Windows HLK setup for LAN (Ethernet) device testing consists of a test server (controller) and test computers (clients).

## <span id="BKMK_HCK_IPSec_sR"></span><span id="bkmk-hck-ipsec-sr"></span><span id="BKMK_HCK_IPSEC_SR"></span>Software requirements


To run Device.Networking tests, you need any drivers that aren't shipped with the operating system.

## <span id="BKMK_HCK_IPSec_tC"></span><span id="bkmk-hck-ipsec-tc"></span><span id="BKMK_HCK_IPSEC_TC"></span>Test computer configuration


IPsec functionality testing requires two computers. One hosts the device being tested, while the other receives and sends data to the test device. The computers also need a separate line of communication to exchange information about ongoing tests. For example, it's beneficial for the receiver of a Send test to know how much data is coming.

The suggested setup for LAN device testing consists of a test server that has the Windows HLK Studio software installed, and three test computers that have the Windows HLK Client software installed.

The following diagram shows the relationship between these computers.

Here's a summary of each computer shown, devices installed on them, and their role during testing.

-   **Windows HLK Studio computer.** Used to manage all of the client computers during testing.

-   **Windows HLK Controller computer.** Used to control client computers and gather all test information from them.

    >[!NOTE]
    >  
    Windows HLK Studio and Windows HLK Controller can run on the same test server, which can help reduce setup complexity.

     

-   **Windows HLK Client 1 computer.** During the LAN device testing, this computer, is referred to as the *remote test machine*, or *Network Driver Interface Specification Test (NDISTest) server*. It contains these network devices:

    -   **Remote support device.** Communicates with the Windows HLK controller. It also communicates test status information to the local support device in the local test computer via the support network.

    -   **Remote message device.** Communicates with the local test device in the local test computer via the test network.

-   **Windows HLK Client 2 computer.** During device testing, this computer is referred to as the *local test machine*, or *NDISTest client*. It contains these network devices:

    -   **Local test device.** The device under test. During testing, it communicates to the remote message device in the remote test machine via the test network.

    -   **Local message device.** Communicates with the controller. It also communicates test status information to the remote support device in the remote test machine via the support network.

    -   **Other local devices.** The NDISTest 6.5 (PM and WoL) job requires that any local device other than local test and local support devices be disconnected from the network.

We recommended that the backchannel switch be on the same network that the clients use to communicate with the controller, and that the network be DHCP-enabled.

The following diagram shows

![lan machine topology](images/hck-win8-lan-machinetopology.png)

The following table matches device roles with interface aliases.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Device role</th>
<th>Interface alias</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Test machine, test target (DUT)</p></td>
<td><p>No name necessary; jobs automatically choose it.</p></td>
</tr>
<tr class="even">
<td><p>Test machine, message device</p></td>
<td><p>MessageDevice</p></td>
</tr>
<tr class="odd">
<td><p>Support machine, support device</p></td>
<td><p>SupportDevice0</p></td>
</tr>
<tr class="even">
<td><p>Support machine, message device</p></td>
<td><p>MessageDevice</p></td>
</tr>
</tbody>
</table>

 

You can use Windows HLK Studio to schedule the LAN device test jobs on the clients that are registered on the controller. The following steps summarize the scheduling procedure.

**To schedule LAN device test jobs**

1.  In Windows HLK Studio, enter all of the information that the LAN device test job needs, and then schedule the job.

    >[!NOTE]
    >  
    Test computers must be in the ready state before testing begins. If a test requires parameters to be set before it's run, a dialog box is displayed for that test. Review the specific test topic for more information.

     

    The LAN device test job requires two Windows HLK test computers. For your submission, you will also need three identical network cards. These requirements are enforced when you configure the Windows HLK job.

2.  Windows HLK Studio sends job configuration information to the controller, which reserves the clients and dispatches the job to them.

3.  The clients run the job. They first copy the NDISTest and all related files, which is the actual LAN device test tool, to the clients and run the NDISTest on the computer using the credentials of the user that's currently signed in.

4.  When the test finishes, the log files are gathered and copied on the controller.

Some Windows HLK tests require user intervention. When running tests for a submission, it's best to run manual and automated tests separately. This prevents a manual test from interrupting completion of an automated test.

### <span id="Overview_of_changes_in_network_device_selection"></span><span id="overview_of_changes_in_network_device_selection"></span><span id="OVERVIEW_OF_CHANGES_IN_NETWORK_DEVICE_SELECTION"></span>Overview of changes in network device selection

For LAN device testing, message and support adapters are no longer selected in the UI—they must be renamed on the test and support machines before running tests. Renaming refers to the device's ifAlias, which is visible from the **Network Connections** window, among other places.

The following image shows

![network connections dialog box](images/hck-win8-lan-networkconnections.png)

The support device on the support machine needs to be renamed to " SupportDevice0". The message devices on both the test and support machines need to be renamed to " MessageDevice".

We have provided a job that tries to automatically detect the network configuration and rename the devices accordingly. You have the option of using this job (recommended), renaming the devices manually, or writing your own renaming script or tool.

### <span id="Device_selection_criteria"></span><span id="device_selection_criteria"></span><span id="DEVICE_SELECTION_CRITERIA"></span>Device selection criteria

The test and support machines must be set up in the same configuration shown in the following figure.

![back-to-back connection](images/hck-win8-lan-networkconnectionsdialog.png)

Any Ethernet devices/ports not involved in testing must be disconnected or disabled. The reconfigure job uses these criteria to find the message device:

1.  Ethernet device

2.  Link connected

3.  Enabled

4.  TCP bound

5.  IP address assigned using DHCP

The message adapter is typically connected to the controller and standard corporate network. When the message device is found, the job searches the remaining adapters for a support device that's an Ethernet device, link connected, enabled, and doesn't have a DHCP-assigned IP address.

## <span id="Running_the_renaming_job"></span><span id="running_the_renaming_job"></span><span id="RUNNING_THE_RENAMING_JOB"></span>Running the renaming job


The renaming job automatically displays when an Ethernet device is selected as a target. It's named **Configure network devices for LAN testing** and it must run before any test job. The Windows HLK doesn't guarantee a run order when multiple jobs are scheduled, so the configuration job must be run alone.

**To run an automatic renaming job**

1.  Create a new project and select only the target device. Don't select message or support adapters.

2.  Select the **Configure network devices for LAN testing** job and clear all other jobs as shown in the following image.

    ![step 2](images/hck-win8-lan-renamingjobstep2.png)

3.  Click **Run Selected**. The Parameters/Machine Set dialog appears. Change the value of the **Reconfigure** parameter to **YES** as shown in the following image.

    ![step 3](images/hck-win8-lan-renamingjobstep3.png)

4.  Select **Support** from the **Role** list box as shown in the following image.

    ![step 4](images/hck-win8-lan-renamingjobstep4.png)

5.  Assign your support machine to the **Support** role by checking its box. Click **OK** to schedule the renamed job, and then wait for it to complete.

6.  Go to the **Results** tab to view the logs. Open the autoconfigure.wtl log from both machines.

    ![step 7](images/hck-win8-lan-renamingjobstep7.png)

7.  Review the logs to ensure that the script automatically detected the correct devices.

    ![step 8](images/hck-win8-lan-renamingjobstep8.png)

## <span id="Preparing_for_IPsec_Task_Offload_v2_testing"></span><span id="preparing_for_ipsec_task_offload_v2_testing"></span><span id="PREPARING_FOR_IPSEC_TASK_OFFLOAD_V2_TESTING"></span>Preparing for IPsec Task Offload v2 testing


Before running tests, you must first configure the system and install the operating system.

Many of the tests in the Windows HLK require a test system to restart (often more than once) to complete a test run. The test description and the running instructions specify whether a test requires a system restart. Although these tests programmatically restart the test system, you must manually sign in to the test system after each system restart so that the test run can resume. You can avoid this requirement by enabling autologon functionality on the test system. For more info about autologon, see Running with autologon enabled.

After you install the Windows HLK Controller, Studio, and Client software, you can monitor the status of the clients through Windows HLK Studio. The clients are grouped into logical machine pools that the controller monitors. New clients are automatically placed in the default pool.

Before LAN testing can begin, you must first create your own machine pool to hold the DTM clients. To do this, drag the DTM client from the default pool into your machine pool and wait for its status to change to Ready.

## <span id="related_topics"></span>Related topics


[Device.Network Testing](device-network-tests.md)

 

 







