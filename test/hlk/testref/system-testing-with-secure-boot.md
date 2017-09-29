---
title: System Testing with Secure Boot
description: System Testing with Secure Boot
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5b4c9667-357c-4d5e-8ec7-063f57e30882
---

# System Testing with Secure Boot


In some cases, having Secure Boot enabled on a test computer can cause the HLK Client installation to fail. You should not see this failure on Windows RT devices, but might see them on non-Windows RT devices. Follow these steps to ensure proper installation:

## <span id="For_system_tests_and_non-class_driver_device_tests"></span><span id="for_system_tests_and_non-class_driver_device_tests"></span><span id="FOR_SYSTEM_TESTS_AND_NON-CLASS_DRIVER_DEVICE_TESTS"></span>For system tests and non-class driver device tests


1.  Disable Secure Boot protections.

    -   For x86/x64, enter the BIOS configuration and disable Secure Boot.

    -   For Windows RT, install the **Windows Debug Policy**; you don't need to disable Secure Boot.

        >[!NOTE]
        >  
        Only OEMs and Microsoft can perform this step.

         

2.  Install the Windows HLK Client software.

3.  Run the following applicable tests for the test platform:

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Test</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>System Must include SuperSpeed Port</p></td>
    </tr>
    <tr class="even">
    <td><p>USB 3.0 Hub Enumeration Stress</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB 3.0 Insertion Test</p></td>
    </tr>
    <tr class="even">
    <td><p>USB 3.0 Speed Switch Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB 3.0 Suspend Test</p></td>
    </tr>
    <tr class="even">
    <td><p>USB Controller Power State Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB Controller Power State Test for System</p></td>
    </tr>
    <tr class="even">
    <td><p>USB Descriptor Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB Device Connection S3+S4</p></td>
    </tr>
    <tr class="even">
    <td><p>USB Device Control Request Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB Enumeration Stress</p></td>
    </tr>
    <tr class="even">
    <td><p>USB Exposed Port Controller Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB Exposed Port System Test</p></td>
    </tr>
    <tr class="even">
    <td><p>USB Host Controller Enable Disable Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB Hub Exposed Port Test</p></td>
    </tr>
    <tr class="even">
    <td><p>USB Hub Selective Suspend Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB Internal Device Idle</p></td>
    </tr>
    <tr class="even">
    <td><p>USB MS OS Descriptor Test (xHCI)</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB Selective Suspend Test (xHCI)</p></td>
    </tr>
    <tr class="even">
    <td><p>USB Serial Number</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB xHCI Compliance Suite (ARM)</p></td>
    </tr>
    <tr class="even">
    <td><p>USB xHCI Register System test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB xHCI Register Test</p></td>
    </tr>
    <tr class="even">
    <td><p>USB xHCI Runtime Power Management System Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB xHCI Runtime Power Management Test</p></td>
    </tr>
    <tr class="even">
    <td><p>USB xHCI Transfer Speed Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>USB3 Termination</p></td>
    </tr>
    <tr class="even">
    <td><p>USB-IF Certification Validation Test (Device)</p></td>
    </tr>
    <tr class="odd">
    <td><p>Debug Capability Test (Logo)</p></td>
    </tr>
    <tr class="even">
    <td><p>xHCI Debug Capability Compliance (Logo)</p></td>
    </tr>
    <tr class="odd">
    <td><p>xHCI Debug Capability Device Compliance (Logo)</p></td>
    </tr>
    <tr class="even">
    <td><p>GFXIntegration Power Management Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>WDDM CCD Test for PersistentReset Monitor</p></td>
    </tr>
    <tr class="even">
    <td><p>DMA Extension Test - UART DMA</p></td>
    </tr>
    <tr class="odd">
    <td><p>NPCTEST - Clock Interrupt Test</p></td>
    </tr>
    <tr class="even">
    <td><p>PCI Hardware Compliance Test For a Single Device (PCIHCT)</p></td>
    </tr>
    <tr class="odd">
    <td><p>PCI Hardware Compliance Test For Systems</p></td>
    </tr>
    <tr class="even">
    <td><p>UEFI Firmware Certification Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>PPM Perf Logo Test</p></td>
    </tr>
    <tr class="even">
    <td><p>WHEAHCT Logo</p></td>
    </tr>
    <tr class="odd">
    <td><p>Connected Standby IO Stress</p></td>
    </tr>
    <tr class="even">
    <td><p>BitLocker Drive Encryption USB BIOS Logo Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>TPM 2.0 Hardware Interface Test (Manual)</p></td>
    </tr>
    <tr class="even">
    <td><p>TPM 2.0 TCG Physical Presence Interface 1.2 Test</p></td>
    </tr>
    <tr class="odd">
    <td><p>TPM 2.0 UEFI Preboot Interface Test</p></td>
    </tr>
    <tr class="even">
    <td><p>TPM Revoke Attestation</p></td>
    </tr>
    <tr class="odd">
    <td><p>ACPI Logo Test</p></td>
    </tr>
    <tr class="even">
    <td><p>Crypto Capabilities – UEFI Hash Provider</p></td>
    </tr>
    <tr class="odd">
    <td><p>Firmware Update test</p></td>
    </tr>
    <tr class="even">
    <td><p>UEFI GOP Mode Test</p></td>
    </tr>
    </tbody>
    </table>

     

4.  Enter the BIOS configuration, enable Secure Boot, and restore Secure Boot to the Default configuration. For Windows RT devices, remove the secure boot debug policy.

5.  Run the rest of the HLK tests.

6.  Enter the BIOS configuration and clear the Secure Boot configuration. This restores the system to Setup Mode by deleting PK and other keys.

    >[!NOTE]
    >  
    Support for clearing is required for x86/x64 and prohibited for production Windows RT devices.

     

7.  Run the Secure Boot Manual Logo Test.

## <span id="For_devices_that_use_drivers_on_Windows_RT"></span><span id="for_devices_that_use_drivers_on_windows_rt"></span><span id="FOR_DEVICES_THAT_USE_DRIVERS_ON_WINDOWS_RT"></span>For devices that use drivers on Windows RT


1.  Install the Windows HLK Client software.

2.  Run device tests for only your devices.

    >[!NOTE]
    >  
    System tests and tests that use drivers that are not signed by Microsoft will fail.

     

 

 






