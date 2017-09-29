---
title: USB Hub.Connectivity Testing Prerequisites
description: USB Hub.Connectivity Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 73f0bf0d-c98e-4fa4-9cc6-459d409acf44
---

# USB Hub.Connectivity Testing Prerequisites


This topic describes the tasks that you must complete before you test your USB hub by using the Windows Hardware Lab Kit (Windows HLK):

-   [USB Device.Connectivity Testing Prerequisites](usb-deviceconnectivity-testing-prerequisites.md#bkmk-hardwarerequirements).

-   [USB Device.Connectivity Testing Prerequisites](usb-deviceconnectivity-testing-prerequisites.md#bkmk-softwarerequirements).

-   [USB Device.Connectivity Testing Prerequisites](usb-deviceconnectivity-testing-prerequisites.md#bkmk-configuringtestcomputer).

## <span id="BKMK_hardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware requirements


The following hardware is required for USB device testing. You might need additional hardware if the device includes additional features.

-   One test computer. The test computer must meet Windows HLK prerequisites and include a USB 2.0–compliant controller and a USB 3.0 or xHCI-compliant controller. The controllers can be either embedded or included on an adapter that is attached or installed in the test computer. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

-   One USB device to connect to the test hub. If you are testing a USB 3.0 hub, you need a USB 3.0-compliant device. Otherwise a high or low speed USB device is sufficient.

-   One USB test hub (for USB 2.0 compliant hubs) or two USB 3.0 test hubs. USB 3.0 hubs require another USB 3.0 hub to validate port mapping in the [USB Hub Exposed Port Test](68f6e04f-4b7f-4548-9562-db9d46105554.md).

    >[!NOTE]
    >  
    Two identical USB test hubs are required to verify the USB serial number is unique for classes of USB devices that include a USB serial number.

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


Before you run the USB tests in the Device.Connectivity category, you should install the latest Windows HLK filters or updates .

## <span id="BKMK_configuringTestComputer"></span><span id="bkmk-configuringtestcomputer"></span><span id="BKMK_CONFIGURINGTESTCOMPUTER"></span>Test computer configuration


To configure the test computer for USB hub testing, follow these steps:

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network (the network that contains Windows HLK Studio and Windows HLK Controller).

2.  Attach the USB hub to the test computer through an xHCI controller port (Windows 8) or an EHCI controller port (Windows 7). USB tests must be run while connected to the xHCI port with the exception of the USB Topology Compatibility test, which requires you to unplug and reattach the hub to other USB ports on the test computer.

    >[!NOTE]
    >  
    If the USB hub supports a USB serial number, attach an additional USB 3.0–compliant device to the test computer before you run the USB Serial Number test. For more information about this test, see [USB Serial Number](0f2d5113-cf70-4cda-8afc-b7005d1e2739.md).

    To test USB 3.0 or 2.0 devices or hubs on a system running Windows 7, make sure that the device or hub is attached to a USB 2.0 port of an EHCI controller. xHCI controllers on systems running Windows 7 load non-Microsoft drivers. HLK tests cannot detect devices and hubs enumerated by third-party drivers.

     

3.  Optionally, verify that the test device is visible from **Device Manager** on the test computer.

4.  Install the Windows HLK client application on the test computer.

5.  By using Windows HLK Studio, create a machine pool, and then move the test computer to that pool.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

If a device supports multiple connectivity methods, complete a separate submission for each connectivity method.

 

 






