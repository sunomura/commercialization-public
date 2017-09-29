---
title: Troubleshooting Device.Connectivity Testing
description: Troubleshooting Device.Connectivity Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2d03925a-fdee-4be3-9ef7-4177b1aa8117
---

# Troubleshooting Device.Connectivity Testing


To troubleshoot issues with PCI device, USB devices, or USB hub connectivity tests, follow these steps:

1.  Review:

    -   [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md)

    -   The following topics, depending on the device type:

        -   [PCI Device.Connectivity Testing Prerequisites](pci-deviceconnectivity-testing-prerequisites.md)

        -   [Proximity Device.Connectivity Testing Prerequisites](proximity-deviceconnectivity-testing-prerequisites.md)

        -   [USB Device.Connectivity Testing Prerequisites](usb-deviceconnectivity-testing-prerequisites.md)

        -   [USB Hub.Connectivity Testing Prerequisites](usb-hubconnectivity-testing-prerequisites.md)

    -   

2.  Verify that you have installed the latest Windows HLK filters and kit updates. For more information, see [Windows Hardware Lab Kit Filters](..\user\windows-hardware-lab-kit-filters.md).

3.  For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

4.  If you cannot obtain a successful test result, contact [Windows HLK Support](..\user\windows-hlk-support.md).

### <span id="Information_about_USB_connectivity_tests_for_Windows_7"></span><span id="information_about_usb_connectivity_tests_for_windows_7"></span><span id="INFORMATION_ABOUT_USB_CONNECTIVITY_TESTS_FOR_WINDOWS_7"></span>Information about USB connectivity tests for Windows 7

The advantages of connecting a device to a USB 2.0 hub are as follows:

-   We recommended this connection for regular USB devices.

-   This connection is required for the USB Selective Suspend test. For more information, see [USB Internal Device Idle Test - Compat](06e1e2d7-ac7c-4ded-82f7-9c6a31386880.md).

-   This connection forces the Enhanced Host Controller Interface (EHCI) high-speed controller to enumerate low-speed and full-speed devices.

The disadvantages of connecting a device to a USB 2.0 hub are as follows:

-   Devices that have embedded hubs must be directly connected for certification tests.

-   We do not recommend multi-TT (transaction translator) hubs for certification testing.

When you are testing a device that has an embedded high-speed hub, attach the device directly to the system for all tests.

## <span id="related_topics"></span>Related topics


[Device.Connectivity Tests](device-connectivity-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







