---
title: Smart Card Reader Testing Prerequisites
description: Smart Card Reader Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2bab039a-c5ba-4b52-92d1-835665197231
---

# Smart Card Reader Testing Prerequisites


This section describes the tasks that you must complete before you test a smart card reader by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware requirements](#bkmk-hck-sc-hr)

-   [Software requirements](#bkmk-hck-sc-sr)

-   [Test computer configuration](#bkmk-hck-sc-tc)

## <span id="BKMK_HCK_SC_hR"></span><span id="bkmk-hck-sc-hr"></span><span id="BKMK_HCK_SC_HR"></span>Hardware requirements


The following hardware is required for testing a smart card reader. You might need additional hardware if the test device offers other features. To determine whether additional hardware requirements apply, see the test description for each test that appears for the device in Windows HLK Studio.

-   One test computer. The test computer must meet the Windows HLK requirements. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

-   The smart card reader that you want to test.

    >[!NOTE]
    >  
    If the device supports universal serial bus (USB), you must have two test devices to run the USB Serial Number test. For more information, see [USB Serial Number](0f2d5113-cf70-4cda-8afc-b7005d1e2739.md).

     

-   One Personal Computer / Smart Card (PC/SC) workgroup test card (from card set 2).

    This card set can be purchased from the [PC/SC website](http://go.microsoft.com/fwlink/?LinkId=228902). Test the product by using the smart cards that the PC/SC workgroup test card set includes. Do not include these smart cards with your test submission.

-   One of the following, depending on the type of connection that the smart card reader implements:

    -   A USB 2.0 hub (if the card reader connects through a USB connection).

    -   An IEEE 1394 controller (if the card reader connects through a 1394 connection).

        >[!NOTE]
        >  
        Support for IEEE 1394 has been deprecated.

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

 

## <span id="BKMK_HCK_SC_sR"></span><span id="bkmk-hck-sc-sr"></span><span id="BKMK_HCK_SC_SR"></span>Software requirements


The following software is required for testing a smart card reader:

-   The drivers for the test device.

-   The latest Windows HLK filters or updates.

## <span id="BKMK_HCK_SC_tC"></span><span id="bkmk-hck-sc-tc"></span><span id="BKMK_HCK_SC_TC"></span>Test computer configuration


To configure the test computer for your test device, follow these steps:

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains Windows HLK Studio and Windows HLK Controller.

2.  If the reader is an internal device, install the smart card reader in the computer. If the reader is an external device, attach a controller to the test computer, and then attach the reader to the external controller.

    If the test device is connected through the USB port, connect the USB 2.0 controller to the high-speed USB 2.0 hub, and then connect the test device to the downstream port of the high-speed USB 2.0 hub.

    >[!NOTE]
    >  
    Do not connect the USB test device directly to the root hub of the USB 2.0 controller.

     

3.  If you have to install the manufacturer-supplied device driver on the test computer, do this now.

4.  Verify that the smart card reader functions correctly on the test computer.

5.  Install the Windows HLK client application on the test computer.

6.  Use Windows HLK Studio to create a machine pool, and then move the test computer to that pool.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

 

 






