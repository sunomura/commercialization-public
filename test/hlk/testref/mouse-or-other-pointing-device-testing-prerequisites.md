---
title: Mouse or other Pointing Device Testing Prerequisites
description: Mouse or other Pointing Device Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6939524c-aead-4fec-9fe4-aa1fd6458d52
---

# Mouse or other Pointing Device Testing Prerequisites


This section describes the tasks that you must complete before you test a mouse or similar pointing device by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware requirements](#bkmk-hck-mouse-hr).

-   [Software requirements](#bkmk-hck-mouse-sr).

-   [Test computer configuration](#bkmk-hck-mouse-tc).

## <span id="BKMK_HCK_Mouse_hR"></span><span id="bkmk-hck-mouse-hr"></span><span id="BKMK_HCK_MOUSE_HR"></span>Hardware requirements


The following hardware is required for testing a mouse or pointing device. You might need additional hardware if the test device offers other features. To determine whether additional hardware requirements apply, see the test description for each test displayed for the device in Windows HLK Studio.

-   One test computer. The test computer must meet the Windows HLK prerequisites. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

-   One test mouse or similar pointing device.

-   One USB 2.0 hub that has a logo.

## <span id="BKMK_HCK_Mouse_sR"></span><span id="bkmk-hck-mouse-sr"></span><span id="BKMK_HCK_MOUSE_SR"></span>Software requirements


The following software is required for testing a mouse or similar pointing device:

-   The drivers for the test device.

-   The latest Windows HLK filters or updates.

## <span id="BKMK_HCK_Mouse_tC"></span><span id="bkmk-hck-mouse-tc"></span><span id="BKMK_HCK_MOUSE_TC"></span>Test computer configuration


To configure the test computer for your test device, follow these steps:

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network. The test network is the network that contains the Windows HLK Studio and Windows HLK Controller.

2.  Attach a USB 2.0 hub to the test computer.

3.  If the mouse or pointing device supports USB, attach the device to the test computer. Verify that the device is plugged into the external USB 2.0 high-speed hub that is connected to the test computer. To test a mouse that supports Bluetooth or wireless connections, connect the associated base station to the USB 2.0 hub

    >[!NOTE]
    >  
    Do not connect the keyboard or wireless base station directly to the root hub of a USB 2.0 controller.

     

4.  If you have to install the manufacturer-supplied device driver on the test computer, do this now.

5.  Make sure that the mouse or pointing device functions correctly on the test computer.

6.  Install the Windows HLK client application on the test computer.

7.  Use Windows HLK Studio to create a machine pool, and then move the test computer to that pool.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

 

 






