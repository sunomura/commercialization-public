---
title: Web Services on Devices Testing Prerequisites
description: Web Services on Devices Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5e366415-744d-4199-a3b7-9c6ad66d555f
---

# Web Services on Devices Testing Prerequisites


This section describes the tasks that you must complete before you test a Web Services on Devices (WSD)-compliant device by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware requirements](#bkmk-hck-wsd-hr).

-   [Software requirements](#bkmk-hck-wsd-sr).

-   [Test computer configuration](#bkmk-hck-wsd-tc).

## <span id="BKMK_HCK_WSD_hR"></span><span id="bkmk-hck-wsd-hr"></span><span id="BKMK_HCK_WSD_HR"></span>Hardware requirements


The following hardware is required for testing WSD compliance. Additional hardware may be required if the test device provides bus-specific support. See the test description for each bus-specific test to determine whether there are additional hardware requirements.

-   Basic Windows HLK test setup (Controller and Studio). See [Windows HLK Getting Started](..\getstarted\windows-hlk-getting-started.md).

-   Two test computers. For testing networking capabilities, the computer that the WDS-compliant device test device is physically attached to is referred to as the System Under Test (SUT) computer and the other computer is referred to as the support computer.

    >[!NOTE]
    >  
    All computers must meet the Windows HLK requirements. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

     

-   One WDS-compliant device to be tested.

-   One wireless network card that supports SoftAP (for example, a D-Link WDA-1320 Desktop Adapter) and a Wireless router if the test printer includes wireless networking capabilities.

-   One stand-alone network adapter (if the test computer does not include an integrated network adapter) and an Ethernet hub or switch if the test scanner includes network printing capabilities.

-   One USB cable and one USB 3.0 hub for testing a device that includes support for USB 3.0 or a USB 2.0 hub for testing a device that supports USB 2.0.

>[!NOTE]
>  
Testing a device for Server Device certification requires that the system that is being used to test the device supports four processors and a minimum of 1 GB of RAM. These system capabilities are required for testing the device and driver for their Rebalance, D3 State and Multiple Processor Group functionality. You do not need a computer that has more than 64 processors to test your device.

If a pool of test computers is used to test devices, at least one computer in the pool must contain four processors and a minimum of 1 GB of RAM. Additionally, that computer must contain the device and driver that is being tested. As long as the driver is the same on all computers in the pool, the test will be created to run against all computers.

For those tests that do not include a driver to test, such as testing a hard disk drive, the Windows HLK scheduler will require the tests that validate the device’s and driver’s Rebalance, D3 State and Multiple Processor Groups functionality to run on the default computer. This computer should also be manually configured to have multiple processor groups. The default computer is the first computer listed. Test personnel, in this case, should ensure that this first computer meets these minimum hardware requirements.

>[!NOTE]
>  
Except for para-virtualization drivers (as defined by the [WHCP Policies and Processes](http://go.microsoft.com/fwlink/p/?LinkID=615222) document), physical devices and their associated drivers being tested for a server certification or signature may not be tested in virtual machines using any form of virtualization. This is because not all virtualization products support the underlying functionality that is required to pass the tests that relate to Multiple Processor Groups, Device Power Management, Device PCI functionality, and so on.

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

 

## <span id="BKMK_HCK_WSD_sR"></span><span id="bkmk-hck-wsd-sr"></span><span id="BKMK_HCK_WSD_SR"></span>Software requirements


The following software is required to run the WSD tests:

-   The driver for the test device if the device does not include an inbox driver.

-   The latest Windows HLK filters or updates.

## <span id="BKMK_HCK_WSD_tC"></span><span id="bkmk-hck-wsd-tc"></span><span id="BKMK_HCK_WSD_TC"></span>Test computer configuration


To configure the test computer for WSD testing, follow these steps:

1.  Install the appropriate Windows operating system on the test computers.

2.  Configure the computers for your test network (the network that contains the Windows HLK Studio and Windows HLK Controller.

3.  Connect both the SUT and the support computer to an Ethernet switch or hub to test wired networking capabilities of your WSD-compliant test device. Connect a wireless router to the support computer to test wireless capabilities.

4.  Attach the WSD-compliant test device to the SUT using a USB cable.

5.  Install the manufacturer-supplied device driver, if you have to, on the test computer.

6.  Check that the WSD-compliant test device is visible from Device Manager on the SUT.

7.  Install the Windows HLK client application on the SUT.

8.  Create a machine pool by using Windows HLK Studio and move both the SUT and the support computer to that pool.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the appropriate test topic for more information.

Some Windows HLK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests separately from manual tests. This prevents a manual test from interrupting the completion of an automated test.

## <span id="WSD_testing_on_WSD_print_and_scan_devices"></span><span id="wsd_testing_on_wsd_print_and_scan_devices"></span><span id="WSD_TESTING_ON_WSD_PRINT_AND_SCAN_DEVICES"></span>WSD testing on WSD print and scan devices


PnPX and Vertical Pairing features are required for WSD devices. If you are testing your device over Ethernet, you need to manually add the Device.Connectivity.PnPX feature. If you are testing your device over WiFi, you need to manually add the Device.Connectivity.VerticalPairing feature.

To manually add a feature, follow these steps:

1.  In the HLK Client, choose the **Selection** tab.

2.  Select **Show Selected** in the left-hand menu.

3.  Right-click a selected devnode, and then select **Show Features**.

4.  Select the **Device.Connectivity.PnPX** or **Device.Connectivity.VerticalPairing** feature.

 

 






