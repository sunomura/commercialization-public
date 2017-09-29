---
title: iSCSI Boot Component Testing Prerequisites
description: iSCSI Boot Component Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 05846be7-bce1-4d44-b6f5-4ba9192a46eb
---

# iSCSI Boot Component Testing Prerequisites


This section describes the tasks that you must complete before you test an iSCSi boot component device by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware Requirements](#bkmk-hardwarerequirements).

-   [Software Requirements](#bkmk-softwarerequirements).

-   [Test Computer Configuration](#bkmk-configure).

Testing an iSCSI boot component verifies that a system supports using an iSCSI target as the startup disk. The iSCSI boot component can be part of the system BIOS, iSCSI host bus adapter (HBA), network card that has Extended BIOS, or network card that has a preboot execution environment (PXE) and iSCSI boot loader program to start the computer.

The iSCSI boot BIOS or loader program uses the Phoenix Int 13h BIOS interrupt call to allow the operating system to start as if there were a locally attached disk. Disk read and write operations through Phoenix Int 13h extensions are redirected through iSCSI to the remote disk. The iSCSI boot BIOS or loader program creates the iSCSI Boot Firmware table (iBFT) that contains the information that is needed for the Microsoft Windows operating system to continue loading after the operating system loader has completed and the Windows kernel has started.

The iSCSI boot component includes the following:

-   Pre-boot initiation code

-   An implementation of iBFT in firmware or BIOS

-   Crashdump support in new or existing drivers

## <span id="BKMK_HardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware Requirements


The following hardware is required for testing an iSCSI boot component. You might need additional hardware if the test device offers other features. To determine whether additional hardware requirements apply, see the test description for each test that appears for the device in Windows HLK Studio.

-   One test computer. The test computers must meet the Windows HLK requirements as described in [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md) and the following operating system-specific requirements:

    -   For testing on Windows 8, Windows 7, Windows Vista or Windows XP:

        -   One dual-core or equivalent processor

        -   4 GB of memory

    -   For testing on Windows Server® 2012, Windows Server 2008 R2, Windows Server 2008, or Windows Server 2003

        -   One quad-core or equivalent processor

        -   6 GB of memory

-   Hardware and software that contain the iSCSI boot component in the server option ROM, NIC option ROM, firmware, or PXE implementation.

-   Two Gigabit Ethernet network adapters that have logos.

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


The following software is required to test an iSCSI boot component:

-   The drivers for the test device.

-   The latest Windows HLK filters or updates.

-   The current release of the Windows Driver Kit (WDK).

-   Windows symbol files. These are available from the [Symbol Files website](http://go.microsoft.com/fwlink/p/?LinkId=231439).

-   Microsoft iSCSI Software Initiator 2.02Boot +.

-   A kernel-mode driver to read iBFT in firmware or BIOS (see Microsoft-iSCSI-Boot-Firmware-Table-Spec-v1.0.doc).

## <span id="BKMK_Configure"></span><span id="bkmk-configure"></span><span id="BKMK_CONFIGURE"></span>Test Computer Configuration


To configure the test computer to test an iSCSI boot component, follow these steps:

1.  When the test computer is turned off, complete the following assembly steps:

    1.  Install the test device that supports iSCSI boot.

    2.  Set up an iSCSI environment and record the IP addresses and target names of the devices.

2.  Turn on the test computer, install the appropriate Windows operating system, install all available Windows updates, and then configure the computer for your test network. The test network is the network that contains the Windows HLK Studio and Windows HLK Controller.

3.  If you have to install the manufacturer-supplied device driver on the test computer, do this now.

4.  Start the test system in the Microsoft Windows operating system.

5.  Verify that Windows can access the iSCSI boot device.

6.  Install the Windows HLK client application on the test computer.

7.  Use Windows HLK Studio to create a computer pool, and then move the test computer to that pool.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will appear for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When you run tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

>[!WARNING]
>  
When testing storage devices, we strongly recommend that you complete all Device Fundamentals tests before starting storage tests. Storage tests will reconfigure your test device, leaving the device in a state unsuitable to support Device Fundamentals tests. The following configurations provide steps to create volume on the storage test device. This is important to complete the Device Fundamental part of testing (DevFund).

 

 

 






