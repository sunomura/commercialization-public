---
title: Device.Portable Testing Prerequisites
description: Device.Portable Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d5c12d65-3ac9-4bf1-9fb8-9b40ce2e3d7f
---

# Device.Portable Testing Prerequisites


Before you test a portable device by using the Windows Hardware Lab Kit (Windows HLK), review the following requirements:

## <span id="BKMK_HCK_Devfund_hR"></span><span id="bkmk-hck-devfund-hr"></span><span id="BKMK_HCK_DEVFUND_HR"></span>Hardware requirements


-   System that supports USB 2.0 (at a minimum)

-   A USB cable for the device that you're testing

## <span id="BKMK_HCK_Devfund_sR"></span><span id="bkmk-hck-devfund-sr"></span><span id="BKMK_HCK_DEVFUND_SR"></span>Software requirements


-   The latest Windows HLK filters or updates

-   A class driver provided by Microsoft

## <span id="Other_requirements"></span><span id="other_requirements"></span><span id="OTHER_REQUIREMENTS"></span>Other requirements


-   If you provide a custom INF with your device, you must run the HLK tests using the Windows class driver (you may not test using your custom INF).

-   Your device must install with the Microsoft Media Transfer Protocol class driver.

-   For Windows Vista and later, your device must appear under the **Portable Devices** category in **Device Manager**.

-   Devices that are read-only must include at least one sample of each format type supported by the device.

-   If the device supports removable media, the media must be added before testing.

-   Run the test with only one portable device connected at a time (this includes Mass Storage Class devices).

-   The battery on the device should be fully charged before testing is started.

## <span id="BKMK_HCK_Devfund_tC"></span><span id="bkmk-hck-devfund-tc"></span><span id="BKMK_HCK_DEVFUND_TC"></span>Test computer configuration


To run portable device tests, you must know how to:

-   Switch a device to a computer connectivity mode before plugging it in.

-   Plug a device into a USB port of the computer and maintain the connectivity throughout the test.

-   Provide continuous power to the device throughout the test.

-   Troubleshoot device installation by checking if the device is installed successfully in **Device Manager** or by looking at the SetupAPI device installation logs.

 

 






