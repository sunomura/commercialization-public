---
title: Virtualization-based Security (VBS)
description: Provides guidance on what an OEM should do to enable VBS
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.author: dawnwood
ms.date: 10/05/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Virtualization-based Security (VBS)
Virtualization-based security, or VBS, uses hardware virtualization features to create and isolate a secure region of memory from the normal operating system. Windows can use this "virtual secure mode" to host a number of security solutions, providing them with greatly increased protection from vulnerabilities in the operating system, and preventing the use of malicious exploits which attempt to defeat protections. 

VBS uses the Windows hypervisor to create this virtual secure mode, and to enforce restrictions which protect vital system and operating system resources, or to protect security assets such as authenticated user credentials. With the increased protections offered by VBS, even if malware gains access to the OS kernel the possible exploits can be greatly limited and contained, because the hypervisor can prevent the malware from executing code or accessing platform secrets.

One such example security solution is Hypervisor-Enforced Code Integrity (HVCI), which uses VBS to significantly strengthen code integrity policy enforcement.  Kernel mode code integrity checks all kernel mode drivers and binaries before they're started, and prevents unsigned drivers or system files from being loaded into system memory. 

Similarly, user mode configurable code integrity policy checks applications before they're loaded, and will only start executables that are signed by known, approved signers. HVCI leverages VBS to run the code integrity service inside a secure environment, providing stronger protections against kernel viruses and malware. The hypervisor, the most privileged level of system software, sets and enforces page permissions across all system memory. Pages are only made executable after code integrity checks inside the secure region have passed, and executable pages are not writable. That way, even if there are vulnerabilities like a buffer overflow that allow malware to attempt to modify memory, code pages cannot be modified, and modified memory cannot be made executable.

VBS requires the following components be present and properly configured.

| Hardware requirement | Details |
|----------------------|---------|
| 64-bit CPU | Virtualization-based security (VBS) features require the Windows hypervisor, which is only supported on 64-bit IA processors, or ARM v8.2 CPUs.
| IOMMUs or SMMUs (Intel VT-D, AMD-Vi, ARM64 SMMUs) | All I/O devices capable of DMA must be behind an IOMMU or SMMU.  An IOMMU can be used to enhance system resiliency against memory attacks. |
| Trusted Platform Module (TPM) 2.0 | TPMs, either discrete or firmware, will suffice. For more information, see [Trusted Platform Module (TPM) 2.0](OEM-TPM.md). |
| Firmware support for SMM protection | System firmware must adhere to the recommendations for hardening SMM code described in the [Windows SMM Security Mitigations Table (WMST) specification](https://docs.microsoft.com/en-us/windows-hardware/drivers/bringup/acpi-system-description-tables). The WSMT specification contains details of an ACPI table that was created for use with Windows operating systems that support Windows virtualization-based security (VBS) features. Firmware must implement the protections described in the WSMT specification, and set the corresponding protection flags as described in the specification to report compliance with these requirements to the operating system. |
|United Extensible Firmware Interface (UEFI) Memory Reporting | UEFI firmware must adhere to the following memory map reporting format and memory allocation guidelines in order for firmware to ensure compatibility with VBS. <br><br><li><b>UEFI v2.6 Memory Attributes Table (MAT) -</b> To ensure compatibility with VBS, firmware must cleanly separate EFI runtime memory ranges for code and data, and report this to the operating system.  Proper segregation and reporting of EFI runtime memory ranges allows VBS to apply the necessary page protections to EFI runtime services code pages within the VBS secure region. Conveying this information to the OS is accomplished using the EFI_MEMORY_ATTRIBUTES_TABLE. To implement the UEFI MAT, follow these guidelines:<br><ol><li>The entire EFI runtime must be described by this table.</li><li> All appropriate attribures for EfiRuntimeServicesData and EfiRuntimeServicesCode pages must be marked.</li><li>These ranges must be aligned on page boundaries (4KB), and can not overlap.</ol></li> <li><b>EFI Page Protections -</b>All entries must include attributes EFI_MEMORY_RO, EFI_MEMORY_XP, or both. All UEFI memory that is marked executable must be read only. Memory marked writable must not be executable. Entries may not be left with neither of the attributes set, indicating memory that is both executable and writable. </li> |
| Secure Memory Overwrite Request (MOR) revision 2 | Secure MOR v2 is enhanced to protect the MOR lock setting using a UEFI secure variable.  This helps guard against advanced memory attacks.  For details, see [Secure MOR implementation](https://docs.microsoft.com/en-us/windows-hardware/drivers/bringup/device-guard-requirements). |
| Hypervisor Code Integrity (HVCI)-compatible drivers | Ensure all system drivers have been tested and verified to be compatible with HVCI. The [Windows Driver Kit](https://developer.microsoft.com/en-us/windows/hardware/windows-driver-kit) and [Driver Verifier](https://docs.microsoft.com/en-us/windows-hardware/drivers/devtest/driver-verifier) contain tests for driver HVCI compatibility. There are four steps to verify driver compatibility:<br><ol><li>Use Driver Verifier with the new <b>Code Integrity compatibility </b> checks enabled.</li><li>Run the [Hypervisor Code Integrity Readiness Test](https://docs.microsoft.com/en-us/windows-hardware/test/hlk/testref/b972fc52-2468-4462-9799-6a1898808c86) in the Windows HLK.</li><li>Test the driver on a system with VBS and HVCI enabled. This step is imperative to validate the driver's behavior with HVCI, as static code analysis tools simply aren't capable of detecting all HVCI violations possible at runtime.</li><li>Use the [Device Guard and Credential Guard hardware readiness tool](https://www.microsoft.com/en-us/download/details.aspx?id=53337).</li></ol> |

## Related topics
For more info about Hyper-V, see [Hyper-V on Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/hyper-v-on-windows-server) or [Introduction to Hyper-V on Windows 10](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/about/). For more info about hypervisor, see [Hypervisor Specifications](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/reference/tlfs).
