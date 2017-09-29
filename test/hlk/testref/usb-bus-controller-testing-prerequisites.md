---
title: USB Bus Controller Testing Prerequisites
description: USB Bus Controller Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e3e74e64-31ae-412c-a28f-3157238e7276
---

# USB Bus Controller Testing Prerequisites


This topic describes the tasks that you must complete before you test your USB host controller by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware requirements](#bkmk-hardwarerequirements).

-   [Software requirements](#bkmk-softwarerequirements).

-   [Test computer configuration](#bkmk-testcomputerconfiguration).

## <span id="BKMK_HardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware requirements


The following hardware is required for USB host controller testing. You might need additional hardware if the USB host controller includes additional capabilities. See the test description for each test that the Windows HLK identifies to determine whether the USB host controller requires additional hardware.

-   One test computer that meets the Windows HLK prerequisites. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

-   One test USB host controller.

For USB 3.0 controller certification you will need a device of each speed and one Windows certified USB 3.0 hub\* on each exposed port.

\*We recommend that you use a USB 3.0 hub that is both USB-IF certified and Windows certified.

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

>[!NOTE]
>  
To run USB Bus Controller Tests, a Windows 10 Mobile device currently requires a separate dedicated USB function controller that can provide connectivity to the HLK server. This is in addition to the USB host controller or USB dual-role controller being tested. Typically this will be an engineering device rather than a retail device.

 

## <span id="BKMK_SoftwareRequirements"></span><span id="bkmk-softwarerequirements"></span><span id="BKMK_SOFTWAREREQUIREMENTS"></span>Software requirements


The following software is required to run the USB host controller tests:

-   The drivers for the USB host controller.

-   The latest Windows HLK filters or updates.

-   Other tools and drivers that are installed as part of the [Install MUTT Tools](8d46285a-8018-4547-9182-86d825375f6a.md) Bring-Up job. This job is not included as part of certification, so you'll need to schedule this job manually.

## <span id="BKMK_TestComputerConfiguration"></span><span id="bkmk-testcomputerconfiguration"></span><span id="BKMK_TESTCOMPUTERCONFIGURATION"></span>Test computer configuration


Only one test computer is required for USB host controller testing. To configure the test computer for USB host controller testing, follow these steps:

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains the Windows HLK Studio and Windows HLK Controller.

2.  Install or attach the USB host controller to the test computer, if the controller is not embedded on the motherboard.

3.  Verify that the USB host controller functions correctly by using a USB device.

    >[!NOTE]
    >  
    It is a best practice to verify full functionality of the USB host controller before you begin testing.

     

4.  Install the Windows HLK client application on the test computer.

5.  Use Windows HLK Studio to create a machine pool, and then move the test computer to that pool.

>[!NOTE]
>  When running a USB Host Controller or System test that requires a MUTT device, be sure to plug in the device before you begin testing.

 

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

## <span id="related_topics"></span>Related topics


[Device.BusController Tests](device-buscontroller-tests.md)

 

 







