---
title: Printer Testing Prerequisites
description: Printer Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 033deddf-8fba-4570-8f33-0c3070f312de
---

# Printer Testing Prerequisites


This section describes the tasks that you must complete before you test a printer by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware requirements](#bkmk-hck-printer-hr).

-   [Software requirements](#bkmk-hck-printer-sr).

-   [Test computer configuration](#bkmk-hck-printer-sc).

## <span id="BKMK_HCK_Printer_hR"></span><span id="bkmk-hck-printer-hr"></span><span id="BKMK_HCK_PRINTER_HR"></span>Hardware requirements


The following hardware is required for printer testing. Additional hardware may be required if the test device provides bus-specific support. See the test description for each bus-specific test to determine whether there are additional hardware requirements.

-   Basic Windows HLK test setup (Controller and Studio). See [Windows HLK Getting Started](..\getstarted\windows-hlk-getting-started.md).

-   One test computer.

    >[!NOTE]
    >  
    All computers must meet the Windows HLK requirements. If two test computers are required, both computers must be in the same computer pool. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

    For testing networking capabilities, the test computer that the scanner is physically attached to is referred to as the System Under Test (SUT) and the other computer is referred to as the support computer.

     

-   One test printer.

-   One wireless network card that supports SoftAP (for example, a D-Link WDA-1320 Desktop Adapter) and a Wireless router if the test printer includes wireless networking capabilities.

-   One stand-alone network adapter (if the test computer does not include an integrated network adapter) and an Ethernet hub or switch if the test scanner includes network printing capabilities.

-   One USB cable and one USB 3.0 hub for testing printers that support USB 3.0; or a USB 2.0 hub for testing a printer that supports USB 2.0

-   Printer paper.

Other hardware may be required to enable certain scenarios.

-   Kernel Debugger system attached to the Windows HLK client.

-   Print server to test print server configurations.

>[!NOTE]
>  
Testing a device for Server Device certification requires that the system that is being used to test the device supports four processors and a minimum of 1 GB of RAM. These system capabilities are required for testing the device and driver for their Rebalance, D3 State and Multiple Processor Group functionality. You do not need a computer that has more than 64 processors to test your device.

If a pool of test computers is used to test devices, at least one computer in the pool must contain four processors and a minimum of 1 GB of RAM. Additionally, that computer must contain the device and driver that is being tested. As long as the driver is the same on all computers in the pool, the test will be created to run against all computers.

For those tests that do not include a driver to test, such as testing a hard drive, the Windows HLK scheduler will require the tests that validate the device’s and driver’s Rebalance, D3 State and Multiple Processor Groups functionality to run on the default computer. This computer should also be manually configured to have multiple processor groups. The default computer is the first computer listed. Test personnel, in this case, should ensure that this first computer meets these minimum hardware requirements.

>[!NOTE]
>  
Except for para-virtualization drivers (as defined by the [WHCP Policies and Processes](http://go.microsoft.com/fwlink/p/?LinkID=615222) document), physical devices and their associated drivers being tested for a server certification or signature may not be tested in virtual machines using any form of virtualization. This is because not all virtualization products support the underlying functionality needed to pass the tests relating to Multiple Processor Groups, Device Power Management, Device PCI functionality, and so on.

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

 

## <span id="BKMK_HCK_Printer_sR"></span><span id="bkmk-hck-printer-sr"></span><span id="BKMK_HCK_PRINTER_SR"></span>Software requirements


Install the operating system on the client systems before the final test passes to ensure that the system is in a known good state.

The following software is required to run the printer tests:

-   The driver package that is being tested on the client system.

-   The AppVerifier application.

-   The Windows .NET Framework 4.0 for computers with Windows Server 2008 R2 installed. This ensures that the tests run correctly.

    >[!NOTE]
    >  
    Both AppVerifier and the .NET Framework are installed during the Windows HLK client application installation.

     

## <span id="Device_configuration"></span><span id="device_configuration"></span><span id="DEVICE_CONFIGURATION"></span>Device configuration


To configure the test device for HLK testing, follow these steps:

1.  Stage the driver you want like to use for testing to the driver store.

2.  Use Plug and Play to install the device on the test machine.

3.  Confirm that the driver you want to test was installed automatically.

If the driver you want to use for testing was not installed, follow these steps:

1.  Select the printer in **Device and Printers**.

2.  Right-click the printer and select **Printer Properties**.

3.  Select the **Advanced** tab.

4.  Under **Driver**, select the driver you want to test.

For the print tests to run properly, the queue must have plug and play data populated. Do not manually create a new queue using the same port and the driver.

## <span id="BKMK_HCK_Printer_sC"></span><span id="bkmk-hck-printer-sc"></span><span id="BKMK_HCK_PRINTER_SC"></span>Test computer configuration


To configure the test computer for printer testing, follow these steps:

1.  Install the appropriate Windows operating system on the test computer.

2.  Configure the test computer for your test network (the network that contains the Windows HLK Studio and Windows HLK Controller.

3.  Connect the SUT and the support computer to an Ethernet switch or hub to test wired networking capabilities of your printer. Connect a wireless router to the support computer to test wireless capabilities.

4.  Install the manufacturer-supplied device driver on the test computer, if the device requires one that is not included with Windows.

5.  Attach the test printer to the test computer using a USB cable.

6.  Check that the printer functions properly on the test computer.

7.  Install the Windows HLK client application on the test computer.

8.  Create a computer pool and move the test computers to that pool by using Windows HLK Studio.

Make sure that the test computers are in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

If a device supports multiple connectivity methods, you can either test each individual connectivity, or run them all at one time. Each connectivity will run all of the print features, and are separate from each other.

 

 






