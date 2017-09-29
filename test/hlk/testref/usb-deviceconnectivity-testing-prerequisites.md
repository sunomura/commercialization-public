---
title: USB Device.Connectivity Testing Prerequisites
description: USB Device.Connectivity Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9410f022-510b-49b3-b966-555feff62cc8
---

# USB Device.Connectivity Testing Prerequisites


This topic describes the tasks that you must complete before you test your USB device by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware requirements](#bkmk-hardwarerequirements).

-   [Software requirements](#bkmk-softwarerequirements),

-   [Test computer configuration](#bkmk-configuringtestcomputer).

## <span id="BKMK_hardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware requirements


The following hardware is required for USB device testing. You might need additional hardware if the device includes additional features.

-   A test computer that meets the [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

-   An EHCI–compliant controller and an xHCI version 1.0 compliant controller, or an xHCI-compliant controller and a high speed hub. The controllers can be either embedded or included on an adapter that is attached or installed in the test computer.

-   Two identical USB test devices. (Note that if the device does not support serial numbers,a legacy test mode option supports using one device only.)

-   A high speed hub if you are using an xHCI controller only.

>[!NOTE]
>  
To certify your product for use on servers, the test computer must support four processors and a minimum of 1 GB of RAM. These system capabilities are required to test the Rebalance, D3 State, and Multiple Processor Group functionality of the device and driver. You do not need a computer that actually has more than 64 processors to test your device. Additionally, the server system(s) being used for device or driver testing must have Server Core installed prior to testing. For more information see [Windows Server Installation Options](http://go.microsoft.com/fwlink/p/?LinkID=251454).

If you use a pool of test computers to test devices, at least one computer in the pool must contain four processors and a minimum of 1 GB of RAM. Additionally, that computer must contain the device and the driver that you want to test. As long as the driver is the same on all the computers in the pool, the system creates a schedule to run against all test computers.

For tests that do not include a driver to test, such as hard disk drive tests, the Windows HLK scheduler constrains the tests that validate the device’s and driver’s Rebalance, D3 State and Multiple Processor Groups functionality to run on the default test computer. You must manually configure this computer to have multiple processor groups. The default computer is the first test computer in the list. Test personnel must make sure that the first test computer in the list meets the minimum hardware requirements.

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

 

## <span id="BKMK_softwareRequirements"></span><span id="bkmk-softwarerequirements"></span><span id="BKMK_SOFTWAREREQUIREMENTS"></span>Software requirements


Before you run the USB tests in the Device.Connectivity category, you should install the latest Windows HLK filters or updates.

## <span id="BKMK_configuringTestComputer"></span><span id="bkmk-configuringtestcomputer"></span><span id="BKMK_CONFIGURINGTESTCOMPUTER"></span>Test computer configuration


To configure the test computer for USB device testing, follow these steps:

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network (the network that contains Windows HLK Studio and Windows HLK Controller).

2.  Attach one of the USB devices to the test computer through an xHCI controller (it can either be attached directly to the root hub port or through a SuperSpeed hub.)

3.  Attach the other USB device to the EHCI port or to a high speed hub that is connected to the XHCI port.

    >[!NOTE]
    >  
    If the USB device supports a USB serial number, attach an additional USB 3.0–compliant device to the test computer before you run the USB Serial Number test. For more information about this test, see [USB Serial Number](0f2d5113-cf70-4cda-8afc-b7005d1e2739.md).

    To test USB 3.0 or 2.0 devices or hubs on a system running Windows 7, make sure that the device or hub is attached to a USB 2.0 port of an EHCI controller. xHCI controllers on systems running Windows 7 load non-Microsoft drivers. HLK tests cannot detect devices and hubs enumerated by third-party drivers.

     

4.  Optionally, verify that the test device is visible from **Device Manager** on the test computer.

5.  Install the Windows HLK client application on the test computer.

6.  By using Windows HLK Studio, create a machine pool, and then move the test computer to that pool.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

If a device supports multiple connectivity methods, complete a separate submission for each connectivity method.

## <span id="related_topics"></span>Related topics


[Device.Connectivity Tests](device-connectivity-tests.md)

 

 







