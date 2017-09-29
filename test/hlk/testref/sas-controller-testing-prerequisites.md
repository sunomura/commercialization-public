---
title: SAS Controller Testing Prerequisites
description: SAS Controller Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 46cfa8cf-175b-4909-bb4c-7c98c8ee5a22
---

# SAS Controller Testing Prerequisites


This section describes the tasks that you must complete before you test an SAS controller by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware Requirements](#bkmk-hardwarerequirements).

-   [Software Requirements](#bkmk-softwarerequirements).

-   [Test Computer Configuration](#bkmk-configure).

## <span id="BKMK_HardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware Requirements


The following hardware is required for testing an SAS controller. You might need additional hardware if the test device offers other features. To determine whether additional hardware requirements apply, see the test description for each test displayed for the device in Windows HLK Studio.

>[!NOTE]
>  
With the exception of the test computer and test controller, all hardware that is involved in the test must already have a logo.

 

-   One test computer. The test computer must meet the Windows HLK requirements as described in [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md). Additionally, the computer must meet the following operating system-specific requirements.

    -   For testing on Windows 8, Windows 7, Windows Vista or Windows XP:

        -   One dual-core or equivalent processor

        -   4 GB of memory

    -   For testing on Windows Server® 2012, Windows Server 2008 R2, Windows Server 2008, or Windows Server 2003:

        -   One quad-core or equivalent processor

        -   6 GB of memory

-   Two identical SAS controllers (the test devices), unless the test device is an integrated controller.

-   One PCI-to-PCI bridge adapter, unless any of the following conditions apply:

    -   The RAID controllers cannot fit into PCI bridge adapters. This may occur if the controllers are integrated controllers or if the controllers can only fit into specially designed slots.

    -   The RAID controller is designed and sold only for systems that cannot accept full height PCI-to-PCI bridge adapters, such as blade servers.

    -   You can put one of the RAID controllers into a PCI bus slot that is already behind a PCI bridge.

-   If the test device is an add-in SAS RAID controller, one of the following items:

    -   Two SAS JBODs. One JBOD must have at least three hard disk drives. The other JBOD must have six hard drives.

    -   One SAS JBOD that includes at least six hard disk drives and three SAS hard disk drives.

    -   One SAS JBOD that includes at least three hard disk drives and six SATA hard disk drives.

    -   Three SAS hard disk drives and six SATA hard disk drives.

-   

    -   One SAS JBOD that has at least six hard disk drives

    -   Six SAS hard disk drives

-   If the SCSI controller does not support RAID, all of the following items are required:

    -   One SAS hard disk drive that is at least 40 GB

    -   One SATA hard disk drive that is at least 40 GB

    -   Two SAS edge expanders

    -   One SAS fanout expander

-   One bootable controller and hard disk drive that has at least 36 GB if the test device does not support boot.

>[!NOTE]
>  
To certify your product for use on servers, the test computer must support four processors and a minimum of 1 GB of RAM. These system capabilities are required to test the Rebalance, D3 State, and Multiple Processor Group functionality of the device and driver. You do not need a computer that actually has more than 64 processors to test your device. Additionally, the server system(s) being used for device or driver testing must have Server Core installed prior to testing. For more information see [Windows Server Installation Options](http://go.microsoft.com/fwlink/p/?LinkID=251454).

If you use a pool of test computers to test devices, at least one computer in the pool must contain four processors and a minimum of 1 GB of RAM. Additionally, that computer must contain the device and the driver that you want to test. If the driver is the same on all the computers in the pool, the system creates a schedule to run against all test computers.

For tests that do not include a driver to test, such as hard disk drive tests, the Windows HLK scheduler constrains the tests that validate the device’s and driver’s rebalance, D3 state, and multiple processor groups functionality to run on the default test computer. You must manually configure this computer to have multiple processor groups. The default computer is the first test computer in the list. Test personnel must make sure that the first test computer in the list meets the minimum hardware requirements.

>[!NOTE]
>  
Except for para-virtualization drivers (as defined by the [WHCP Policies and Processes](http://go.microsoft.com/fwlink/p/?LinkID=615222) document), you may not use any form of virtualization when you test physical devices and their associated drivers for server certification or signature. All virtualization products do not support the underlying functionality that is required to pass the tests that relate to multiple processor groups, device power management, device PCI functionality, and other tests.

>[!NOTE]
>  Multiple Processor Groups Setting
>You must set the value for the processor group size for Hardware Lab Kit testing of Windows Server 2008 R2 and later device drivers for certification. This is done by running bcdedit in an elevated command prompt window, using the /set option.
>
>The commands for adding the group settings and restarting are as follows:
>
``` syntax
bcdedit.exe /set groupsize 2
bcdedit.exe /set groupaware on
shutdown.exe -r -t 0 -f
```
>
>
>The commands for removing the group settings and rebooting are as follows:
>
``` syntax
bcdedit.exe /deletevalue groupsize
bcdedit.exe /deletevalue groupaware
shutdown.exe -r -t 0 -f
```
>

>[!NOTE]
>  
**Code Integrity Setting**

>The Virtualization Based Security feature (VBS) of Windows Server 2016 must be enabled using Server Manager first.
>
>Once that has occurred, the following Registry key must be created and set:
>
``` syntax
HKLM\System\CurrentControlSet\Control\DeviceGuard
HypervisorEnforcedCodeIntegrity:REG_DWORD
0 or 1 (disabled, enabled)
```

 

## <span id="BKMK_SoftwareRequirements"></span><span id="bkmk-softwarerequirements"></span><span id="BKMK_SOFTWAREREQUIREMENTS"></span>Software Requirements


The following software is required for testing a SAS controller:

-   The drivers for the test device.

-   The latest Windows HLK filters or updates.

-   Windows symbol files. These are available from the [Symbol Files website](http://go.microsoft.com/fwlink/?LinkId=231439).

-   The current release of the Windows Driver Kit (WDK).

## <span id="BKMK_Configure"></span><span id="bkmk-configure"></span><span id="BKMK_CONFIGURE"></span>Test Computer Configuration


There are three possible configurations for testing SAS controllers:

-   If the test device is an add-in controller that supports RAID, use the [Add-in RAID controller test configuration](#bkmk-addin).

-   If the test device is an integrated controller that supports RAID, use the [Integrated RAID controller test configuration](#bkmk-integrated).

-   If the test device does not support RAID, use the [Non-RAID controller test configuration](#bkmk-nonraid).

Before you test an SAS controller in any of the three usage scenarios, make sure that the test computer is in the ready state. If a test requires parameters to be set before the test is run, a dialog box appears for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When you run tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

Additionally, the automated Disk Verification test is a 72-hour test. We recommend that you run this test last or over the weekend, so that you can collect and analyze the results from other tests without waiting for this test to finish.

>[!WARNING]
>  
When testing storage devices, we strongly recommend that you complete all Device Fundamentals tests before starting storage tests. Storage tests will reconfigure your test device, leaving the device in a state unsuitable to support Device Fundamentals tests. The following configurations provide steps to create volume on the storage test device. This is important to complete the Device Fundamental part of testing (DevFund).

 

### <span id="BKMK-addin"></span><span id="bkmk-addin"></span><span id="BKMK_ADDIN"></span>Add-in RAID controller test configuration

To configure the test computer to test an SAS controller in an add-in RAID configuration, follow these steps:

1.  When the test computer is turned off, complete the following assembly steps:

    1.  Install a boot-capable controller (not the test device) and hard disk drive, if the test devices do not support boot.

    2.  Install one test controller (Controller 1).

    3.  Install a PCI-to-PCI bridge, unless one of the following items is true:

        -   The RAID controllers cannot fit into PCI bridge adapters. This may occur if the controllers are integrated controllers or if the controllers can only fit into specially designed slots.

        -   The RAID controller is designed and sold only for systems that cannot accept full height PCI-to-PCI bridge adapters, such as blade servers.

        -   You can put one of the RAID controllers into a PCI bus slot that is already behind a PCI bridge.

    4.  Install a second, duplicate test controller (Controller 2) in the PCI-to-PCI bridge card (or in the PCI bridge if the bridge card is not required).

    5.  Attach the disks to the test devices according to the following table:

        <table>
        <colgroup>
        <col width="33%" />
        <col width="33%" />
        <col width="33%" />
        </colgroup>
        <thead>
        <tr class="header">
        <th>Controller type</th>
        <th>Controller 1</th>
        <th>Controller 2</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td><p>SAS RAID</p></td>
        <td><p>One SAS JBOD or three SAS hard disk drives</p></td>
        <td><p>One SAS JBOD or six SATA hard disk drives that are connected by a fanout expander in between two edge expanders</p></td>
        </tr>
        </tbody>
        </table>

         

    6.  Attach an optical drive to the system, if one is not already attached.

2.  Turn on the test system.

3.  Set the system BIOS to support the S3 state.

4.  Create one 60-GB RAID array on Controller 1 and two 60-GB RAID arrays on Controller 2.

5.  Configure the RAID arrays according to the following table:

    <table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>RAID levels that the test device supports</th>
    <th>RAID level for RAID Array 1</th>
    <th>RAID level for RAID Array 2</th>
    <th>RAID level for RAID Array 3</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>0 only</p></td>
    <td><p>0</p></td>
    <td><p>0</p></td>
    <td><p>0</p></td>
    </tr>
    <tr class="even">
    <td><p>1 only</p></td>
    <td><p>1</p></td>
    <td><p>1</p></td>
    <td><p>1</p></td>
    </tr>
    <tr class="odd">
    <td><p>5 only</p></td>
    <td><p>5</p></td>
    <td><p>5</p></td>
    <td><p>5</p></td>
    </tr>
    <tr class="even">
    <td><p>0 and 1 only</p></td>
    <td><p>1</p></td>
    <td><p>9</p></td>
    <td><p>0</p></td>
    </tr>
    <tr class="odd">
    <td><p>0 and 5 only</p></td>
    <td><p>5</p></td>
    <td><p>9</p></td>
    <td><p>0</p></td>
    </tr>
    <tr class="even">
    <td><p>1 and 5 only</p></td>
    <td><p>5</p></td>
    <td><p>1</p></td>
    <td><p>1</p></td>
    </tr>
    <tr class="odd">
    <td><p>0, 1, and 10</p></td>
    <td><p>10</p></td>
    <td><p>1</p></td>
    <td><p>0</p></td>
    </tr>
    <tr class="even">
    <td><p>0, 1, and 5</p></td>
    <td><p>5</p></td>
    <td><p>1</p></td>
    <td><p>0</p></td>
    </tr>
    <tr class="odd">
    <td><p>0, 1, 10, and 5</p></td>
    <td><p>5</p></td>
    <td><p>10</p></td>
    <td><p>0</p></td>
    </tr>
    </tbody>
    </table>

     

6.  Install the appropriate Windows operating system on disk 1 (using a newly created NTFS partition that has at least 36 GB of disk space), and then configure the computer for your test network. The test network is the network that contains the Windows HLK Studio and Windows HLK Controller. If the test controller is not bootable, install a separate hard disk drive on a bootable controller.

7.  If you have to install the manufacturer-supplied device driver on the test computer, do this now.

8.  Start the test computer in the Windows operating system, and then use Disk Manager to create three 4-GB partitions on RAID Array 2.

9.  If you are testing by using a client operating system, create a 4-GB NTFS spanned volume that uses unallocated space on RAID Array 1, RAID Array 2, and RAID Array 3, as the following diagram shows.

    ![add-in raid array configuration diagram (client)](images/hck-win8-ata-raid-config-16-1.png)

    If you are testing by using a server operating system, do the following:

    1.  Create a software RAID 1 mirror from one of the NTFS partitions on RAID Array 2 to the unallocated space on RAID Array 1

    2.  Create a 4-GB NTFS software RAID 5 array that uses unallocated space on RAID Array 1, RAID Array 2, and RAID Array 3, as the following diagram shows.

        ![add-in raid array configuration diagram (server)](images/hck-win8-ata-raid-config-16-2.png)

10. To set the system page file and enable crashdump, do the following:

    1.  Click the **Start** button, right-click **My Computer**, and then click **Properties.**

    2.  Click the **General** tab, and then note the amount of RAM that the computer contains.

    3.  Click the **Advanced** tab (or click **Advanced system settings** in the left pane for Windows Vista, Windows 7, Windows 8, Windows Server 2008, Windows Server 2008 R2 or Windows Server® 2012), and then, in the **Performance** area, click **Settings**.

        >[!NOTE]
        >  
        If you are prompted to enter administrative credentials or allow the action, enter the credentials or allow the action.

         

    4.  Click the **Advanced** tab, and then, in the **Virtual Memory** area, click **Change**.

    5.  Select **Custom Size**, and then enter a number in the **Initial size (MB)** box that is larger than the size of RAM that you noted in step b.

    6.  In the **Maximum size (MB)** text box, enter a maximum size value that is larger than the initial size that you entered in the **Initial size (MB)** box. (The maximum size is typically 1.5 to 2 times the initial size.)

    7.  Click **Set**, and then click **OK** two times.

    8.  Click **OK**, and then restart the computer to update the page file size.

11. Verify that the storage array is accessible from the test computer.

12. Copy the Windows symbol files to %SystemDrive%\\Symbols.

13. Install the Windows HLK client application on the test computer.

14. Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

### <span id="BKMK-integrated"></span><span id="bkmk-integrated"></span><span id="BKMK_INTEGRATED"></span>Integrated RAID controller test configuration

To configure the test computer for testing of an SAS controller in an integrated RAID configuration, follow these steps:

1.  When the test computer is turned off, complete the following assembly steps:

    1.  Install a boot-capable controller (not the test device) and hard disk drive, if the test devices do not support boot.

    2.  Attach the disks to the integrated test controller (Controller 1) according to the following table:

        <table>
        <colgroup>
        <col width="50%" />
        <col width="50%" />
        </colgroup>
        <thead>
        <tr class="header">
        <th>Controller type</th>
        <th>Controller 1</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td><p>SAS RAID</p></td>
        <td><p>One SAS JBOD or six SAS hard disk drives</p></td>
        </tr>
        </tbody>
        </table>

         

    3.  Attach an optical drive to the system, if one is not already attached.

2.  Turn on the test system.

3.  Set the system BIOS to support the S3 state.

4.  Create two 60-GB RAID arrays on Controller 1.

    If the controller does not support a configuration that includes two arrays, use a non-RAID disk instead of Array 2 for these procedures. For SCSI, create a third 60-GB RAID array (using any supported RAID level).

    The RAID arrays on Controller 1 are RAID Array 1 and RAID Array 2.

5.  Configure the RAID arrays according to the following table:

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>RAID levels that the test device supports</th>
    <th>RAID level for RAID Array 1</th>
    <th>RAID level for RAID Array 2</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>0 only</p></td>
    <td><p>0</p></td>
    <td><p>0</p></td>
    </tr>
    <tr class="even">
    <td><p>1 only</p></td>
    <td><p>1</p></td>
    <td><p>1</p></td>
    </tr>
    <tr class="odd">
    <td><p>5 only</p></td>
    <td><p>5</p></td>
    <td><p>5 or Non-RAID disk</p></td>
    </tr>
    <tr class="even">
    <td><p>0 and 1 only</p></td>
    <td><p>1</p></td>
    <td><p>0</p></td>
    </tr>
    <tr class="odd">
    <td><p>0 and 5 only</p></td>
    <td><p>5</p></td>
    <td><p>0 or Non-RAID disk</p></td>
    </tr>
    <tr class="even">
    <td><p>1 and 5 only</p></td>
    <td><p>5</p></td>
    <td><p>1or Non-RAID disk</p></td>
    </tr>
    <tr class="odd">
    <td><p>0, 1, and 10</p></td>
    <td><p>10</p></td>
    <td><p>1 or Non-RAID disk</p></td>
    </tr>
    <tr class="even">
    <td><p>0, 1, and 5</p></td>
    <td><p>5</p></td>
    <td><p>0 or Non-RAID disk</p></td>
    </tr>
    <tr class="odd">
    <td><p>0, 1, 10, and 5</p></td>
    <td><p>5</p></td>
    <td><p>10 or Non-RAID disk</p></td>
    </tr>
    </tbody>
    </table>

     

6.  Install the appropriate Microsoft Windows operating system to a 36-GB NTFS volume on RAID Array 1, and then configure the computer for your test network. The test network is the network that contains the Windows HLK Studio and Windows HLK Controller. If the test controller is not bootable, install a separate hard disk drive on a bootable controller.

7.  If it is necessary, install any drivers that a manufacturer supplies that the devices in the test system require.

8.  Start Windows on the test computer.

9.  To set the system page file and enable crashdump, do the following:

    1.  Click the **Start** button, right-click **My Computer**, and then click **Properties.**

    2.  Click the **General** tab, and then note the amount of RAM that the computer contains.

    3.  Click the **Advanced** tab (or click **Advanced system settings** in the left pane for Windows Vista, Windows 7, Windows 8, Windows Server 2008, Windows Server 2008 R2 or Windows Server® 2012), and then, in the **Performance** area, click **Settings**.

        >[!NOTE]
        >  
        If you are prompted to enter administrative credentials or allow the action, enter the credentials or allow the action.

         

    4.  Click the **Advanced** tab, and then, in the **Virtual Memory** area, click **Change**.

    5.  Select **Custom Size**, and then enter a number in the **Initial size (MB)** box that is larger than the size of RAM that you noted in step b.

    6.  In the **Maximum size (MB)** text box, enter a maximum size value that is larger than the initial size that you entered in the **Initial size (MB)** box. (The maximum size is typically 1.5 to 2 times the initial size.)

    7.  Click **Set**, and then click **OK** two times.

    8.  Click **OK**, and then restart the computer to update the page file size.

10. Verify that the storage array is accessible from the test computer.

11. Copy the Windows symbol files to %SystemDrive%\\Symbols.

12. Install the Windows HLK client application on the test computer.

13. Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

### <span id="BKMK-nonraid"></span><span id="bkmk-nonraid"></span><span id="BKMK_NONRAID"></span>Non-RAID controller test configuration

To configure the test computer to test an SAS controller in a non-RAID configuration, follow these steps:

1.  When the test computer is turned off, complete the following assembly steps:

    1.  Install a boot-capable controller (not the test device) and hard disk drive if the test devices do not support boot.

    2.  Install the test device (Controller 1).

    3.  For add-in SAS controllers, install a PCI-to-PCI bridge, unless you meet the following requirements:

        -   The controllers cannot fit into PCI bridge adapters. This may occur if the controllers are integrated controllers or if the controllers can only fit into specially designed slots.

        -   The controller is designed and sold only for systems that cannot accept full height PCI-to-PCI bridge adapters, such as blade servers.

        -   You can put one of the controllers into a PCI bus slot that is already behind a PCI bridge.

    4.  For add-in SAS controllers, install a second, duplicate test controller (Controller 2) in the PCI-to-PCI bridge card (or in the PCI bridge if the bridge card is not required).

    5.  Attach the disks to the test devices according to the following table:

        <table>
        <colgroup>
        <col width="33%" />
        <col width="33%" />
        <col width="33%" />
        </colgroup>
        <thead>
        <tr class="header">
        <th>Controller type</th>
        <th>Controller 1</th>
        <th>Controller 2</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td><p>SAS add-in controllers</p></td>
        <td><p>SAS HDD (Disk 1)</p></td>
        <td><p>Edge expander, then Fanout expander, then Edge expander, then SATA HDD</p>
        <p>(Disk 2)</p></td>
        </tr>
        <tr class="even">
        <td><p>SAS integrated controllers</p></td>
        <td><p>SAS HDD (Disk 1), and Fanout expander, then Edge expander, then SATA HDD</p>
        <p>(Disk 2)</p></td>
        <td><p>N/A</p></td>
        </tr>
        </tbody>
        </table>

         

        SAS add-in controllers configuration diagram

        ![diagram of an add-in sas assembly](images/hck-win8-non-raid-config-add-in-sas.png)

        SAS integrated controllers configuration diagram

        ![diagram of an integrated sas assembly](images/hck-win8-non-raid-config-integrated-sas.png)

    6.  Attach an optical drive to the system, if one is not already attached.

2.  Turn on the test computer, install the appropriate Windows operating system on disk 1 (using a newly created NTFS partition that has at least 36 GB of disk space), and then configure the computer for your test network. The test network is the network that contains the Windows HLK Studio and Windows HLK Controller. If the test controller is not bootable, install a separate hard disk drive on a bootable controller.

3.  Set the system BIOS to support the S3 state.

4.  If you have to install the manufacturer-supplied device driver on the test computer, do this now.

5.  Create three 4-GB partitions on Disk 2.

6.  Use the following procedure to set the system page file and enable crashdump:

    1.  Click the **Start** button, right-click **My Computer**, and then click **Properties.**

    2.  Click the **General** tab, and then note the amount of RAM that the computer contains.

    3.  Click the **Advanced** tab (or click **Advanced system settings** in the left pane for Windows Vista, Windows 7, Windows 8, Windows Server 2008, Windows Server 2008 R2 or Windows Server® 2012), and then, in the **Performance** area, click **Settings**.

        >[!NOTE]
        >  
        If you are prompted to enter administrative credentials or allow the action, enter the credentials or allow the action.

         

    4.  Click the **Advanced** tab, and then, in the **Virtual Memory** area, click **Change**.

    5.  Select **Custom Size**, and then enter a number in the **Initial size (MB)** box that is larger than the size of RAM that you noted in step b.

    6.  In the **Maximum size (MB)** text box, enter a maximum size value that is larger than the initial size that you entered in the **Initial size (MB)** box. (The maximum size is typically 1.5 to 2 times the initial size.)

    7.  Click **Set**, and then click **OK** two times.

    8.  Click **OK**, and then restart the computer to update the page file size.

7.  Copy the Windows symbol files to %SystemDrive%\\Symbols.

8.  Install the Windows HLK client application on the test computer.

9.  Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

 

 






