---
title: UEFI firmware requirements
description: Provides guidance on what an OEM should do to enable UEFI
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.author: dawnwood
ms.date: 10/05/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# United Extensible Firmware Interface (UEFI) firmware requirements
When the devices starts, the firmware interface controls the booting process of the PC, and then passes control to Windows or another operating system.
UEFI is a replacement for the older BIOS firmware interface and the Extensible Firmware Interface (EFI) 1.10 specifications.
More than 140 leading technology companies participate in the Unified EFI Forum, including AMD, AMI, Apple, Dell, HP, IBM, Insyde, Intel, Lenovo, Microsoft, and Phoenix Technologies.

## UEFI benefits
Firmware that meets the UEFI 2.3.1 specifications provides the following benefits:
- Ability to support Windows 10 security features like Secure Boot, Windows Defender Device Guard, Windows Defender Credential Guard, and Windows Defender Exploit Guard. All require UEFI firmware.
- Faster boot and resume times.
- Ability to more easily support large hard drives (more than 2 terabytes) and drives with more than four partitions.
- Support for multicast deployment, which allows PC manufacturers to broadcast a PC image that can be received by multiple PCs without overwhelming the network or image server.
- Support for UEFI firmware drivers, applications, and option ROMs.



## Media installation considerations
To download Windows, see [the Windows 10 download page](https://www.microsoft.com/en-us/software-download/windows10). If you want to use media like a USB flash drive, a DVD, or an ISO, dowload the [Windows Media creation tool](https://www.microsoft.com/en-us/software-download/windows10?d2784474-fdb0-4e9d-9e47-5e88c0e053ec=True). 

## Boot and miminum security requirements
<p>As the OEM, you must provide support for the features outlined in the [Hardware Compatibility Specification for Systems for Windows](https://msdn.microsoft.com/en-us/library/windows/hardware/dn932805.aspx), specifically the following items that are divided into two groups: boot requiements and minimum security requirements. </p>

### Boot requirement

- [System.Fundamentals.Firmware.UEFICompatibility]()

### Minimum security requirements

- [System.Fundamentals.Firmware.UEFIBitLocker](https://msdn.microsoft.com/en-us/library/windows/hardware/dn932805.aspx#systemfundamentalsfirmwareuefibitlocker)
- [System.Fundamentals.Firmware.UEFICompatibility](https://msdn.microsoft.com/en-us/library/windows/hardware/dn932805.aspx#systemfundamentalsfirmwareueficompatibility)
- [System.Fundamentals.Firmware.UEFIDefaultBoot](https://msdn.microsoft.com/en-us/library/windows/hardware/dn932805.aspx#systemfundamentalsfirmwareuefidefaultboot)
- [System.Fundamentals.Firmware.UEFILegacyFallback](https://msdn.microsoft.com/en-us/library/windows/hardware/dn932805.aspx#systemfundamentalsfirmwareuefilegacyfallback)
- [System.Fundamentals.Firmware.UEFISecureBoot](https://msdn.microsoft.com/en-us/library/windows/hardware/dn932805.aspx#systemfundamentalsfirmwareuefisecureboot)
- [System.Fundamentals.Firmware.UEFITimingClass](https://msdn.microsoft.com/en-us/library/windows/hardware/dn932805.aspx#systemfundamentalsfirmwareuefitimingclass)
- [System.Fundamentals.Firmware.UEFIBootEntries](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/systems#systemfundamentalsfirmwareuefibootentries)

## Runtime requirements
Windows uses these services, but will not cause failure if they are unimplemented.
- GetTime
- SetTime
- UpdateCapsule
- ResetSystem: only required if there is no ACPI hardware support for resetting the device.

## Hibernation State (S4) transition requirements
Platform firmware must ensure that operating system physical memory is consistent across S4 sleep state transitions, in both size and location.
Operating system physical memory is defined according to the ACPI 3.0 specification as any memory that is described by the firmware system address map interface with a memory type other than AddressRangeReserved [2], AddressRangeUnusable [5], or Undefined [any value greater than 5].

On a UEFI platform, firmware runtime memory must be consistent across S4 sleep state transitions, in both size and location. Runtime memory is defined according to the UEFI specification as any memory that is described by the GetMemoryMap() boot service, with the attribute EFI_MEMORY_RUNTIME.

