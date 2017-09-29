---
title: Device Guard hardware requirements
description: Provides guidance on what an OEM should do to enable Windows Defemder Device Guard
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.author: dawnwood
ms.date: 10/05/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Windows Defender Device Guard
Starting with Windows 10, version 1709, Windows Defender Device Guard is split into two features known as Windows Defender Exploit Guard and Windows Defender Application Control. These features are a combination of enterprise-related hardware and software security features that, when configured together, will lock a device down so that it can only run trusted applications that are defined in an enterprise's code integrity policies. If the app isn’t trusted it can’t run, period. 

With hardware that meets basic requirements, it also means that even if an attacker manages to get control of the Windows kernel, he or she will be much less likely to be able to run malicious executable code. 

Windows Defender Device Guard can also leverage advanced hardware features on hardware that supports them. These features include CPU virtualization extensions (called "Intel VT-x" or "AMD-V") and second-level address translation (SLAT). In addition, hardware that includes input/output memory management units (IOMMUs) provides even stronger protections. When you enable the features associated with CPU virtualization extensions and SLAT, the Code Integrity service can run alongside the kernel in a Windows hypervisor-protected container. 

If you are an OEM building secure systems, you must provide the hardware to enable these features.

**IT Professionals:**  If you want more information on how to deploy Windows Defender Device Guard, see [Windows Defender Device Guard deployment guide](https://docs.microsoft.com/en-us/windows/device-security/device-guard/device-guard-deployment-guide).

## Windows Defender Exploit Guard

Windows Defender Exploit Guard includes hypervisor-protected code integrity (HVCI), which is a kernel process mitigation that leverages virtualization based security to isolate the process that performs integrity validation and authorization for kernel-mode code.

For a device to support Windows Defender Exploit Guard as specified in the Windows Hardware Compatibility Requirements (WHCR), you as the OEM must provide the following hardware, software, or firmware features. 

| Requirement | Details |
|----------------------|---------|
| Secure Boot | Hardware-based Secure Boot must be supported. To learn more, see [Secure Boot](OEM-secure-boot.md). | 
| Secure Boot configuration and management | <ul><li>The OEM has to be able to add ISV, OEM, or Enterprise Certificate in Secure Boot DB at manufacturing time. </li><li>Microsoft UEFI CA must be removed from Secure Boot DB. Support for 3rd-party UEFI modules is permitted but should leverage ISV-provided certificates or OEM certificate for the specific UEFI software.</li></ul> |
| Secure firmware update process | Like UEFI software, UEFI firmware can have security vulnerabilities. It is essential to have the capability to immediately patch such vulnerabilities when found through firmware updates. UEFI firmware must support secure firmware update following Hardware Compatibility Specification for Systems for Windows 10 under [System.Fundamentals.Firmware.UEFISecureBoot](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/systems#systemfundamentalsfirmwareuefisecureboot).|
| Trusted Platform Module (TPM) 2.0 | To learn more about TPM, see [Trusted Platform Module](OEM-TPM.md).|
| United Extensible Firmware Interface (UEFI) | To lern more, see [United Extensible Firmware Interface (UEFI) firmware requirements](OEM-UEFI.md). |
| Virtualization-based security (VBS) | Device Guard requires VBS. You can learn more about VBS by reading [Virtualization-based Security (VBS)](OEM-VBS.md). |



## Windows Defender Application control

Starting with Windows 10, version 1709, the code integretity part of Windows Defender Device Guard has been split out into a separate feature known as Windows Defender Application control. 

 WDAC is used to control what code can run on the system in either kernel or user mode. When HVCI is enabled, WDAC benefits from the increased kernel memory protections since the kernel mode CI checks occur in virtualization based security and user mode code integrity runs as part of the kernel itself and is thus protected against kernel memory exploits.
 There are no hardware requirements for WDAC. 


## Windows Defender Device Guard and Windows Defender Credential Guard Readiness Tool

To determine if a device is able to run Windows Defender Device Guard and Windows Defender Credential Guard, download the [Device Guard and Credential Guard hardware readiness tool](https://www.microsoft.com/en-us/download/details.aspx?id=53337).

## Related topics

- [Driver Compatibility with Device Guard on Windows 10](https://blogs.msdn.microsoft.com/windows_hardware_certification/2015/05/22/driver-compatibility-with-device-guard-in-windows-10)
- [Managing Managing Windows 10 Device Guard with Configuration Manager](https://blogs.technet.microsoft.com/enterprisemobility/2015/10/30/managing-windows-10-device-guard-with-configuration-manager/)
-[Device Guard signing](https://docs.microsoft.com/en-us/microsoft-store/device-guard-signing-portal)
