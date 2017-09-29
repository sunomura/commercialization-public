---
title: Bluetooth Controller Testing Prerequisites
description: Bluetooth Controller Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 76a0105c-4009-4a0e-8995-240efd8bb76f
---

# Bluetooth Controller Testing Prerequisites


This document covers how to properly setup your test environment and test machines for running the Bluetooth Windows HLK tests for a Bluetooth radio.

## <span id="Bluetooth_Bus_Controller_Requirements__Device.BusController.Bluetooth_"></span><span id="bluetooth_bus_controller_requirements__device.buscontroller.bluetooth_"></span><span id="BLUETOOTH_BUS_CONTROLLER_REQUIREMENTS__DEVICE.BUSCONTROLLER.BLUETOOTH_"></span>Bluetooth Bus Controller Requirements (Device.BusController.Bluetooth)


When certifying a Bluetooth radio, it is required that all testing is done with the Microsoft Inbox Bluetooth stack. Filter drivers required for radio operation can still be used as long as the functionality of the Microsoft stack is not replaced.

The radio should be tested while connected over the transport type OEMs and ODMs will be using in their System. For example, if the radio will be connected over UART in a System, please certify the radio with it connected over UART as well.

The radio testing should be done in the default Windows configuration and no changes to Bluetooth settings should be made. For example, USB radios must support Selective Suspend and this will be enabled in Windows by default. Do not change this setting from the OS selected default.

>[!NOTE]
>  
It is **highly recommended** that IHVs who also produce a Profile Add-on pack perform additional Bluetooth System level testing (System.Client.BluetoothController) with their profile pack installed on the system as OEMs and ODMs will be required to certify their systems with these profile packs installed.

 

## <span id="Test_Environment_Setup"></span><span id="test_environment_setup"></span><span id="TEST_ENVIRONMENT_SETUP"></span>Test Environment Setup


The Bluetooth tests require up to 3 test systems, each with a 4.0 Bluetooth radio present on the machine and in the same WHLK machine pool. The machines are broken down into two roles.

-   Primary – Test system which has the Bluetooth radio to be certified (DUT).

-   Secondary – Supporting test systems which have a 4.0 Bluetooth Radio present on the system.

All of the test machines must be able to communicate over TCP/IP and must be able to resolve each other’s machine names using DNS. Back channel TCP/IP communication takes places over ports 5005 and 5006 and should be opened automatically by the test software.

### <span id="Machine_Setup_Instructions"></span><span id="machine_setup_instructions"></span><span id="MACHINE_SETUP_INSTRUCTIONS"></span>Machine Setup Instructions

1.  Install the newest available Windows Operating System on the test machines, and join the machines to your test network. All test machines must be able to communicate with each other over TCP/IP and the WHLK controller.

2.  If the systems do not have an internal Bluetooth radio, perform the following steps.

    1.  Install the Bluetooth controller to be certified (DUT) on the primary system.

    2.  Install the supporting Bluetooth 4.0 radios on the secondary machines. It is recommended to use a previously certified radio on your secondary test machines, but no 4.0 radios have received a logo at the time that this document was written.

3.  Install software packages.

    1.  If certifying the **Bluetooth radio**, install any required software (filter drivers, etc.) required for the radios operation. Functionality of the Microsoft inbox Bluetooth Stack must not be replaced when certifying a radio.

    2.  If certifying a **Windows System** which has an integrated Bluetooth radio, install any required software required for radio operation, as well as any software the machine will ship with (this includes 3rd party drivers such as profiles packs and filter drivers).

4.  Install Windows HLK client on the test computer.

5.  Use Windows HLK studio to create a machine pool and move the 3 test machines into the newly created pool.

6.  Place all test machines into the “Ready” state.

 

 






