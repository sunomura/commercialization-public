---
title: Hard Disk Drive Testing Prerequisites
description: Hard Disk Drive Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 53e9b41c-0dd8-4ea5-9bc9-a37a1ee7b30f
---

# Hard Disk Drive Testing Prerequisites


This topic describes the tasks that you must complete before you test a hard disk by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware Requirements](#bkmk-hardwarerequirements).

-   [Software Requirements](#bkmk-softwarerequirements).

-   [Configuring the Test Computer](#bkmk-configure).

The tests that you must run depend on the capabilities of the hard disk that you want to test, its connection type (for example, an external USB-based hard drive), or how it's configured (as part of a RAID system or part of an IP-based storage solution).

The Windows HLK supports the testing of hard disks that have these connection types:

-   Fibre Channel

-   IEEE 1394

-   Parallel Advanced Technology Attachment (PATA)

-   PC Card

-   Serial Attached SCSI (SAS)

-   Serial Advanced Technology Attachment (SATA)

-   SCSI

-   USB

-   SD / EMMC

## <span id="BKMK_HardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware Requirements


The hardware that's required for testing a hard drive varies depending on the connection type. But, all tests for hard disks require 1 test computer. The test computer must meet the Windows HLK requirements. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

>[!NOTE]
>  
You might need additional hardware if the hard drive is part of a storage system. To determine whether additional hardware requirements apply, see the test description for each test that appears for the device in Windows HLK Studio.

 

To certify your product for use on servers, the test computer must support four processors and a minimum of 1 GB of RAM. These system capabilities are required to test the Rebalance, D3 State, and Multiple Processor Group functionality of the device and driver. You do not need a computer that actually has more than 64 processors to test your device. Additionally, the server system(s) being used for device or driver testing must have Server Core installed prior to testing. For more information see [Windows Server Installation Options](http://go.microsoft.com/fwlink/p/?LinkID=251454).

If you use a pool of test computers to test your device, at least 1 computer in the pool must contain 4 processors and a minimum of 1 GB of RAM. Additionally, that computer must contain the device and the driver that you want to test. As long as the driver is the same on all the computers in the pool, the system creates a schedule to run against all test computers.

For tests that don't include a driver, like tests for a hard disk drive, the Windows HLK scheduler constrains the tests that validate the device's and driver's Rebalance, D3 State, and Multiple Processor Groups functionality to run on the default test computer. You must manually configure this computer to have multiple processor groups. The default computer is the first test computer in the list. Make sure that the first test computer in the list meets the minimum hardware requirements.

>[!NOTE]
>  
Except for para-virtualization drivers (as defined by the [WHCP Policies and Processes](http://go.microsoft.com/fwlink/p/?LinkID=615222) document), you can't use any form of virtualization when you test physical devices and their associated drivers for server certification or signature. Virtualization products don't support the underlying functionality that's required to pass the tests that relate to multiple processor groups, device power management, device PCI functionality, and other tests.

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

 

The following sections provide additional hardware requirements for the test computer, based on the connection type.

### <span id="General"></span><span id="general"></span><span id="GENERAL"></span>General

For all configurations:

-   1 disk drive with a minimum capacity of 6 GB used as the boot drive.

-   1 CD-ROM drive (may be optional)

-   Network card, keyboard, mouse, display, power cable as needed

-   For each physical interface, please see the table below for additional hardware requirements.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Interface</th>
<th>Hardware Equipment Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Fibre Channel</p></td>
<td><ul>
<li><p>1 Fibre Channel controller</p></li>
<li><p>2 identical Fibre Channel hard disk drives for the test devices</p></li>
<li><p>1 Fibre Channel hub</p></li>
<li><p>Appropriate cables for connecting the drives</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>IEEE 1394</p></td>
<td><ul>
<li><p>IEEE 1394 host controller</p></li>
<li><p>1 IEEE 1394 hard disk drive (for the test device)</p></li>
<li><p>Appropriate cables for connecting the drives</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>PATA</p></td>
<td><p>If the connection type is PATA, you need this hardware:</p>
<ul>
<li><p>1 dual-channel ATA/ATAPI controller on the motherboard</p></li>
<li><p>2 identical PATA hard disk drives (for the test devices)</p></li>
<li><p>Appropriate cables for connecting the drives</p></li>
</ul>
<div class="alert">
<strong>Note</strong>  
<p>ATA-66 and ATA-100 controllers require 80-conductor cables.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>PC Card</p></td>
<td><ul>
<li><p>2 PC Card controllers</p></li>
<li><p>2 PC Card hard disk drives for the test devices</p></li>
<li><p>Appropriate cables for connecting the drives</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>SAS</p></td>
<td><ul>
<li><p>2 dual-ported SAS controllers</p></li>
<li><p>2 identical SAS hard disk drives for the test devices</p></li>
<li><p>Appropriate cables for connecting the drives</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>SATA</p></td>
<td><ul>
<li><p>1 SATA controller that has at least 2 channels</p></li>
<li><p>2 SATA hard disk drives for the test devices</p></li>
<li><p>Appropriate cables for connecting the drives</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>SCSI</p></td>
<td><ul>
<li><p>1 SCSI adapter that has the appropriate bus interface for the test device, such as narrow, wide, or low voltage differential (LVD)</p></li>
<li><p>2 identical SCSI hard disk drives for the test devices</p></li>
<li><p>Appropriate cables for connecting the drives</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>USB 2.0</p></td>
<td><ul>
<li><p>A USB 2.0 host controller that's embedded on the system motherboard, or a USB 2.0 controller PCI adapter. The USB controller must be able to wake the system by using Advanced Configuration and Power Interface (ACPI) mechanisms.</p></li>
<li><p>2 identical USB hard disk drives for the test devices</p></li>
<li><p>1 USB 2.0 high-speed hub</p></li>
<li><p>Appropriate cables for connecting the drives</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>USB 3.0</p></td>
<td><ul>
<li><p>A USB 3.0 host controller that's embedded on the system motherboard, or a USB 3.0 controller PCI adapter. The USB controller must be able to wake the system by using Advanced Configuration and Power Interface (ACPI) mechanisms.</p></li>
<li><p>A USB 2.0 host controller that's embedded on the system motherboard, or a USB 2.0 controller PCI adapter. The USB controller must be able to wake the system by using Advanced Configuration and Power Interface (ACPI) mechanisms.</p></li>
<li><p>2 identical USB hard disk drives for the test devices</p></li>
<li><p>1 USB 2.0 high-speed hub</p></li>
<li><p>Appropriate cables for connecting the drives</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <span id="BKMK_SoftwareRequirements"></span><span id="bkmk-softwarerequirements"></span><span id="BKMK_SOFTWAREREQUIREMENTS"></span>Software Requirements


To test a hard disk, you need this software:

-   The drivers for the hard disk controllers, if required

-   The latest Windows HLK filters or updates

## <span id="BKMK_Configure"></span><span id="bkmk-configure"></span><span id="BKMK_CONFIGURE"></span>Configuring the Test Computer


Before you begin testing the hard disk, you must configure the test computer and install the appropriate controller (if the test computer doesn't include this kind of controller). Then, you must complete the appropriate configuration steps, based on the type of hard disk that you're certifying.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires you to set parameters before you run it, a dialog box will appear for that test. For more information, review the specific test topic.

Some Windows HLK tests require user intervention. When you're running tests for a submission, it's a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting the completion of an automated test.

>[!WARNING]
>  
When testing storage devices, we strongly recommend that you complete all Device Fundamentals tests before starting storage tests. Storage tests will reconfigure your test device, leaving the device in a state unsuitable to support Device Fundamentals tests. The following configurations provide steps to create volume on the storage test device. This is important to complete the Device Fundamental part of testing (DevFund).

 

**To configure the test computer to test your Fibre Channel hard disk**

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

2.  If the test system doesn't have a SCSI adapter installed, install the SCSI adapter.

3.  Install 2 identical SCSI hard disk drives and 1 CD-ROM drive onto the SCSI bus.

4.  Install 1 Fibre Channel controller.

5.  Install 1 Fibre Channel hub on the Fibre Channel controller.

6.  Connect the Fibre Channel hard disk drives (test devices) to the Fibre Channel hub.

7.  Set the system BIOS to support the S3 state.

8.  Install the appropriate operating system on 1 of the SCSI hard disk drives.

9.  Install any manufacturer-supplied drivers that devices in the test system require, and then restart the system.

10. Use the Windows Disk Management tool to delete all existing partitions on the Fibre Channel hard disk drives.

11. Install the Windows HLK client application on the test computer.

12. Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

**To configure the test computer to test your IEEE 1394 hard disk**

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

2.  Install the ATA/ATAPI hard disk drive as a stand-alone Device 0 on the primary ATA/ATAPI channel by using a standard ATA/ATAPI cable.

3.  Install the ATA/ATAPI CD-ROM drive as a stand-alone Device 0 on the secondary ATA/ATAPI channel by using a standard ATA/ATAPI cable.

4.  If the IEEE 1394 controller isn't an embedded component, install 1 IEEE 1394 controller.

5.  By using an IEEE 1394 cable, install the IEEE 1394 hard disk drive (test device) as a stand-alone device on IEEE 1394 socket port 1 of the IEEE 1394 controller.

6.  Set the system BIOS to support the S3 state.

7.  Install the appropriate Windows operating system on the ATA/ATAPI hard disk drive.

8.  Install any manufacturer-supplied drivers that devices in the test system require.

9.  Remove any partitions on the test device, and then convert the test device to use the master boot record (MBR) partitioning style.

10. Install the Windows HLK client application on the test computer.

11. Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

**To configure the test computer to test your PATA hard disk**

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

2.  Install the hard disk drive (test device) as a stand-alone Device 0 on the primary ATA/ATAPI channel by using a standard ATA/ATAPI cable. This drive is called Drive 1.

3.  Install the CD-ROM drive by using a standard ATA/ATAPI cable.

    You can install the CD-ROM drive as Device 1 or Cable Select Device 1 on the primary ATA/ATAPI channel. Or, you can install the CD-ROM as Device 0, Device 1, Cable Select Device 0, or Cable Select Device 1 on the secondary ATA/ATAPI channel.

4.  Set the system BIOS to support the S3 state.

5.  Install the appropriate Windows operating system on Drive 1.

6.  Install any manufacturer-supplied drivers that devices in the test system require.

7.  With the test system turned off, install an identical hard disk drive by using a standard ATA/ATAPI cable.

    You can install this drive as Device 1 or Cable Select Device 1 on the primary ATA/ATAPI channel. Or, you can install this drive as Device 0, Device 1, Cable Select Device 0, or Cable Select Device 1 on the secondary ATA/ATAPI channel. This drive is called Drive 2.

8.  If you're testing a hybrid disk, install the disk on a secondary channel and make sure that the disk is a secondary disk.

9.  Remove any partitions on Drive 2, and then convert the drive to use the MBR partitioning style.

10. Create three 4-GB NTFS-formatted partitions.

11. Install the Windows HLK client application on the test computer.

12. Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

**To configure the test computer to test your PC Card hard disk**

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

2.  Install 1 PC Card hard disk drive (test device) on the PC Card channel of the test system.

3.  Install the PC Card network adapter on the second PC Card controller in the test system.

4.  Set the system BIOS to support the S3 state.

5.  Install the appropriate Windows operating system on the ATA/ATAPI hard disk in the test system.

6.  Install any manufacturer-supplied drivers that devices in the test system require.

7.  Remove any partitions on the test device, and then convert the test device to use the MBR partitioning style.

8.  Install the Windows HLK client application on the test computer.

9.  Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

**To configure the test computer to test your SAS hard disk**

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

2.  If the test system doesn't contain a SCSI adapter, install the SCSI adapter.

3.  Install a SCSI hard disk drive on the SCSI bus.

4.  Install the SCSI CD-ROM drive on the SCSI bus.

5.  Install 2 dual-ported SAS controllers

6.  Connect 1 SAS hard disk drive to the SAS port.

7.  Set the system BIOS to support the S3 state.

8.  Install the appropriate Windows operating system on the SCSI hard disk drive.

9.  Install any manufacturer-supplied drivers that devices in the test system require.

10. Restart the test computer.

11. By using the Windows Disk Management tool, delete all existing partitions on the SAS hard disk drives.

12. Install the Windows HLK client application on the test computer.

13. Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

**To configure the test computer to test your SATA hard disk**

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

2.  Install the CD-ROM drive as Drive 0 on an ATA/ATAPI controller.

3.  Install a SATA controller and attach 2 SATA hard disks. These hard disks are called Drive 1 and Drive 2.

4.  Set the system BIOS to support the S3 state.

5.  Install the appropriate Windows operating system on Drive 1.

    During installation, delete any existing partitions on Drive 2 and create three 4-GB NTFS partitions.

6.  Install any manufacturer-supplied drivers that devices in the test system require.

7.  Install the Windows HLK client application on the test computer.

8.  Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

**To configure the test computer to test your SCSI hard disk**

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

2.  Set the SCSI IDs on the hard disk drives (test devices) to the following:

    -   Drive 1 = SCSI ID 0

    -   Drive 2 = SCSI ID 1

3.  Install the hard disk drives (test devices) on the SCSI adapter.

4.  Set the SCSI ID on the SCSI CD-ROM drive to 6, and then physically install the SCSI CD-ROM drive on the SCSI adapter on a separate channel from the test devices.

5.  Set the system BIOS to support the S3 state.

6.  Install the appropriate Windows operating system on an NTFS-formatted volume on Drive 1.

7.  Install any manufacturer-supplied drivers that devices in the test system require.

8.  Remove any partitions on Drive 2, and then convert the test device to use the MBR partitioning style.

9.  Create three 4-GB NTFS-formatted partitions on Drive 2.

10. Install the Windows HLK client application on the test computer.

11. Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

**To configure the test computer to test your USB hard disk**

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

2.  If the test system doesn't have an embedded USB 2.0 controller, install a USB 2.0 controller.

3.  Connect the USB 2.0 controller to the high-speed USB 2.0 hub.

4.  Connect the test device to the downstream port of the high-speed USB 2.0 hub.

    >[!NOTE]
    >  
    Don't connect the USB test device directly to the root hub of the USB 2.0 controller.

     

5.  Set the system BIOS to support the S3 state.

6.  Install the appropriate Windows operating system on hard disk drive.

7.  Install any manufacturer-supplied drivers that devices in the test system require.

8.  Remove any partitions on the test device, and then convert the test device to use the MBR partitioning style.

9.  Create three 4-GB partitions on the test device.

10. Install the Windows HLK client application on the test computer.

11. Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

## <span id="Feature-Based_Configuration"></span><span id="feature-based_configuration"></span><span id="FEATURE-BASED_CONFIGURATION"></span>Feature-Based Configuration


If your device supports any of the feature(s) in this section, please update the associated configurations steps in addition to the general interface-based configuration steps in “Configuring the Test Computer.” Minor modifications may be applicable depending on the specifics of your device form-factor.

**Device.Storage.Hd.Ehdd**

-   If testing as a boot device, the system must support UEFI 2.3.1 (with TCG OPAL 2.0 implementation).

-   A secondary non-boot device is still required to be installed for testing.

**Device.Storage.Hd.Flush**

-   This feature and testing requires an external programmable power strip.

-   See the [Flush Test](b7df764f-ab21-4e7a-9594-e6f814711b4d.md) for more details.

**Device.Storage.Hd.Sata.HybridInformation**

-   The target test device cannot be a boot device.

-   The target test device should be a different product (e.g. Hardware ID) than the boot device.

-   Set system BIOS to boot from AHCI.

-   Start the system using Microsoft AHCI driver.

**Device.Storage.Hd.Trim**

-   The target test device cannot be a boot device.

-   The target test device should be a different product (e.g. Hardware ID) than the boot device.

-   Set system BIOS to boot from AHCI.

-   Start the system using Microsoft AHCI driver.

**Device.Storage.Hd.Uas**

1.  Install a USB 3.0 XHCI host controller in test system 1 ().

    >[!NOTE]
    >  
    Ff the host controller is already available as an embedded device on the system, skip this step.

     

2.  Attach target device 1 to system 1 into the 3.0 port.

3.  Attach target device 2 to system 2 into the 2.0 port. This step is necessary for testing cross XHCI and EHCI compatibility of UAS support on the test device.

4.  Upon completing the configuration on the two systems, run the following tests:

    -   UAS device connected to XHCI port: Run full test suite.

    -   UAS device connected to EHCI port: Run the following 3 tests.

        -   Disk Stress for UAS on EHCI (LOGO)

        -   UAS Stress Reset logo test for UAS on EHCI

        -   USB 2.0 & 3.0 SCSI Compliance test for UAS on EHCI (LOGO)

 

 






