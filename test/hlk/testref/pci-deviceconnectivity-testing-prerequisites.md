---
title: PCI Device.Connectivity Testing Prerequisites
description: PCI Device.Connectivity Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: aeae6137-2279-4504-b5e3-53a620ed335c
---

# PCI Device.Connectivity Testing Prerequisites


This section describes the tasks that you must complete before you test a PCI-based test device using the Windows Hardware Lab Kit (Windows HLK).

Before beginning testing, complete the following:

-   [Hardware requirements](#bkmk-hck-pci-hr).

-   [Software requirements](#bkmk-hck-pci-sr).

-   [Test computer configuration](#bkmk-hck-pci-tc).

## <span id="BKMK_HCK_PCI_hR"></span><span id="bkmk-hck-pci-hr"></span><span id="BKMK_HCK_PCI_HR"></span>Hardware requirements


The following hardware is required for PCI device testing. You might need additional hardware if the test device includes additional features.

-   One test computer. The test computer must meet Windows HLK prerequisites. See [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md) for more information.

-   One test PCI device.

>[!NOTE]
>  
Additional test hardware will be required depending on that type of PCI device is being tested. For example, if the PCI test device is a graphic adapter, review the Device.Graphics test prerequisites.

 

## <span id="BKMK_HCK_PCI_sR"></span><span id="bkmk-hck-pci-sr"></span><span id="BKMK_HCK_PCI_SR"></span>Software requirements


The following software is required to run the Device.Connectivity tests:

-   The latest Windows HLK filters or updates.

-   The drivers for the test device.

## <span id="BKMK_HCK_PCI_tC"></span><span id="bkmk-hck-pci-tc"></span><span id="BKMK_HCK_PCI_TC"></span>Test computer configuration


To configure the test computer for PCI device testing:

1.  Install the appropriate Windows operating system on the test computer and then configure the computer for your test network (the network that contains the Windows HLK Studio and Windows HLK Controller.

2.  Install the test PCI device in the test computer.

3.  Install any required drivers for the test PCI device.

4.  Check that the test PCI device is detected by the test computer.

5.  Install the Windows HLK client application on the test computer.

6.  Using the Windows HLK Studio, create a machine pool, and move the test computer to that pool.

7.  Review the features detected by the Windows HLK Studio and review any additional prerequisites for the features detected for the test device.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

>[!NOTE]
>  
If a device supports multiple connectivity methods, complete a separate submission for each connectivity method.

 

 

 






