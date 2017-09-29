---
title: Secure boot
description: Provides guidance on what an OEM should do to enable Securely booting a device
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.author: dawnwood
ms.date: 10/05/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Secure boot

Secure boot is a security standard developed by members of the PC industry to help make sure that a device boots using only software that is trusted by the Original Equipment Manufacturer (OEM). When the PC starts, the firmware checks the signature of each piece of boot software, including UEFI firmware drivers (also known as Option ROMs), EFI applications, and the operating system. If the signatures are valid, the PC boots, and the firmware gives control to the operating system.

The OEM can use instructions from the firmware manufacturer to create Secure boot keys and to store them in the PC firmware. When you add UEFI drivers, you'll also need to make sure these are signed and included in the Secure Boot database. 

For information on how the secure boot process works included Trusted Boot and Measured Boot, see [Secure the Windows 10 boot process](https://docs.microsoft.com/en-us/windows/threat-protection/secure-the-windows-10-boot-process). 

## Secure boot requirements

In order to support Secure boot, you must provide the following. 

| Hardware requirement | Details |
|----------------------|---------|
| UEFI Version 2.3.1 Errata C variables | Variables must be set to **SecureBoot=1** and **SetupMode=0** with a signature database (EFI_IMAGE_SECURITY_DATABASE) necessary to boot the machine securely pre-provisioned, and including a PK that is set in a valid KEK database. For more information, see [System.Fundamentals.Firmware.UEFISecureBoot](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/systems#systemfundamentalsfirmwareuefisecureboot). |
| UEFI v2.3.1 Section 27 | The platform must expose an interface that adheres to the profile of UEFI v2.3.1 Section 27. |
| UEFI signature database | The platform must come provisioned with the correct keys in the UEFI Signature database (db) to allow Windows to boot. It must also support secure authenticated updates to the databases. Storage of secure variables must be isolated from the running operating system such that they cannot be modified without detection. |
| Firmware signing | All firmware components must be signed using at least RSA-2048 with SHA-256. |
| Boot manager | When power is turned on, the system must start executing code in the firmware and use public key cryptography as per algorithm policy to verify the signatures of all images in the boot sequence, up to and including the Windows Boot Manager. |
|Rollback protection | The system must protect against rollback of firmware to older versions. |
| EFI_HASH_PROTOCOL | The platform provides the EFI_HASH_PROTOCOL (per UEFI v2.3.1) for offloading cryptographic hash operations and the EFI_RNG_PROTOCOL (Microsoft defined) for accessing platform entropy. |

## Signature Databases and Keys

Before the PC is deployed, you as the OEM store the Secure Boot databases on the PC. This includes the signature database (db), revoked signatures database (dbx), and Key Enrollment Key database (KEK). These databases are stored on the firmware nonvolatile RAM (NV-RAM) at manufacturing time.

The signature database (db) and the revoked signatures database (dbx) list the signers or image hashes of UEFI applications, operating system loaders (such as the Microsoft Operating System Loader, or Boot Manager), and UEFI drivers that can be loaded on the device. The revoked list contains items that are no longer trusted and may not be loaded. If an image hash is in both databases, the revoked signatures database (dbx) takes precedent. 

The Key Enrollment Key database (KEK) is a separate database of signing keys that can be used to update the signature database and revoked signatures database. Microsoft requires a specified key to be included in the KEK database so that in the future Microsoft can add new operating systems to the signature database or add known bad images to the revoked signatures database.

After these databases have been added, and after final firmware validation and testing, the OEM locks the firmware from editing, except for updates that are signed with the correct key or updates by a physically present user who is using firmware menus, and then generates a platform key (PK). The PK can be used to sign updates to the KEK or to turn off Secure Boot.

You should contact your firmware manufacturer for tools and assistance in creating these databases. 

## Boot sequence

1. After the PC is turned on, the signature databases are each checked against the platform key.
2. If the firmware is not trusted, the UEFI firmware must initiate OEM-specific recovery to restore trusted firmware.
3. If there is a problem with Windows Boot Manager, the firmware will attempt to boot a backup copy of Windows Boot Manager. If this also fails, the firmware must initiate OEM-specific remediation.
4. After Windows Boot Manager has started running, if there is a problem with the drivers or NTOS kernel, Windows Recovery Environment (Windows RE) is loaded so that these drivers or the kernel image can be recovered.
5. Windows loads antimalware software.
6. Windows loads other kernel drivers and initializes the user mode processes.


## Related Topics

- [UEFI firmware requirements](https://review.docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-uefi?branch=dawn-security-toc)