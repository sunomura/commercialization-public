---
title: Optical Disk Drive Testing Prerequisites
description: Optical Disk Drive Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6aa632a1-0d96-454e-94f5-0d88fc67ea32
---

# Optical Disk Drive Testing Prerequisites


This topic describes the tasks that you must complete before you test an optical storage device by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware Requirements](#bkmk-hardwarerequirements).

-   [Software Requirements](#bkmk-softwarerequirements).

-   [Configuring the Test Computer](#bkmk-configure).

The optical storage device includes rewritable drives for CD, DVD, and Blu-ray media.

## <span id="BKMK_HardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware Requirements


To test an optical drive, you need the following hardware. You might need additional hardware if the test device offers other features. To determine whether additional hardware requirements apply, see the description for each test that appears for the device in Windows HLK Studio.

-   1 test computer that meets the Windows HLK requirements. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md). In addition, this computer must have one of the following types of processors:

    -   Dual-core or equivalent processor and 4 gigabytes (GB) of memory for Windows client operating systems (for example, Windows 8, Windows 7, and Windows Vista).

    -   Quad-core or equivalent processor and 6 GB of memory for Windows Server® operating systems.

    The test computer must contain one dual-channel Advanced Technology Attachment (ATA)/Advanced Technology Attachment Packet Interface (ATAPI) controller that's implemented on the motherboard. The test computer must also contain a logo-compliant Advanced Configuration and Power Interface (ACPI) BIOS, with ACPI enabled by default. For Windows 8, Windows 7, and Windows Vista, BIOS configuration and Serial Advanced Technology Attachment (SATA) controller support of SATA Advanced Host Controller Interface (AHCI) mode are required.

-   2 identical optical disk drives for testing.

    >[!NOTE]
    >  
    If the optical disk drive that you're testing is read-only, you must connect a writer drive in addition to the two drives that you test.

     

-   1 host controller of the same bus type as the optical storage device. The USB controller must be able to wake the system by using ACPI mechanisms.

-   Appropriate cables for connecting devices.

-   Blank media for each type of media that the test device supports.

To certify your product for use on servers, the test computer must support four processors and a minimum of 1 GB of RAM. These system capabilities are required to test the Rebalance, D3 State, and Multiple Processor Group functionality of the device and driver. You do not need a computer that actually has more than 64 processors to test your device. Additionally, the server system(s) being used for device or driver testing must have Server Core installed prior to testing. For more information see [Windows Server Installation Options](http://go.microsoft.com/fwlink/p/?LinkID=251454).

If you use a pool of test computers to test your device, at least 1 computer in the pool must contain 4 processors and a minimum of 1 GB of RAM. Additionally, that computer must contain the device and the driver that you want to test. As long as the driver is the same on all the computers in the pool, the system creates a schedule to run against all test computers.

For tests that don't include a driver to test, like tests for a hard disk drive, the Windows HLK scheduler constrains the tests that validate the device's and driver's Rebalance, D3 State, and Multiple Processor Groups functionality to run on the default test computer. You must manually configure this computer to have multiple processor groups. The default computer is the first test computer in the list. Make sure that the first test computer in the list meets the minimum hardware requirements.

>[!NOTE]
>  
Except for para-virtualization drivers (as defined by the [WHCP Policies and Processes](http://go.microsoft.com/fwlink/p/?LinkID=615222) document), you can't use any form of virtualization when you test physical devices and their associated drivers for server certification or signature. Virtualization products don't support the underlying functionality that's required to pass the tests that relate to multiple processor groups, device power management, device Peripheral Component Interconnect (PCI) functionality, and other tests.

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


To test an optical storage device, you need this software:

-   The drivers for the test device

-   The latest Windows HLK filters or updates

## <span id="BKMK_Configure"></span><span id="bkmk-configure"></span><span id="BKMK_CONFIGURE"></span>Configuring the Test Computer


To configure the test computer for your test device, follow these steps:

1.  Turn off the test system, disconnect it from the power supply, and install a hard disk drive. Depending on the bus type of the test optical storage device, take one of these actions:

    -   For ATA/ATAPI, install the hard disk drive as stand-alone Device 0 on the primary ATA/ATAPI channel.

    -   For SCSI, set the SCSI ID on the SCSI hard disk drive to 0.

2.  If the host controller is not embedded on the system motherboard, install the host controller.

3.  Install the test optical storage devices in the test system by attaching them to the host controller. Depending on the bus type of the test optical storage device, take one of these actions:

    -   For ATA/ATAPI, install the test device as Device 1 or Cable Select Device 1 on the primary ATA/ATAPI channel. Or install the test device as Device 0, Device 1, Cable Select Device 0, or Cable Select Device 1 on the secondary ATA/ATAPI channel.

    -   For SCSI, set the SCSI ID on the test device to 6.

    -   For USB, connect the test device to the downstream port of the high-speed USB 2.0 hub.

        >[!NOTE]
        >  
        Don't connect the USB test device directly to the root hub of the USB 2.0 controller.

         

4.  Turn on the test system and set the system BIOS to support the S3 state.

    >[!NOTE]
    >  
    All adapters are operated with BIOS enabled and external termination unless otherwise noted.

     

5.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

6.  If you must install the manufacturer-supplied device driver on the test computer, do this now.

7.  Verify that both optical storage devices function correctly on the test computer.

8.  Install the Windows HLK client application on the test computer.

9.  Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires you to set parameters before you run it, a dialog box will appear for that test. For more information, review the specific test topic.

Some Windows HLK tests require user intervention. When you're running tests for a submission, it's a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting the completion of an automated test.

>[!WARNING]
>  
When testing storage devices, we strongly recommend that you complete all Device Fundamentals tests before starting storage tests. Storage tests will reconfigure your test device, leaving the device in a state unsuitable to support Device Fundamentals tests. The following configurations provide steps to create volume on the storage test device. This is important to complete the Device Fundamental part of testing (DevFund).

 

 

 






