---
title: Windows Defender Credential Guard hardware requirements
description: Provides guidance on what an OEM should do to enable Windows Defender Credential Guard
ms.author: dawnwood
ms.date: 10/05/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Windows Defender Credential Guard hardware requirements

Windows Defender Credential Guard uses virtualization-based security to isolate and protect secrets (e.g., NTLM password hashes and Kerberos ticket-granting tickets) to block pass-the-hash or pass-the-ticket (PtH) attacks. When Windows Defender Credential Guard is enabled, NTLMv1, MS-CHAPv2, Digest, and CredSSP cannot use the signed-in credentials. Thus, single sign-on does not work with these protocols. However, applications can prompt for credentials or use credentials stored in the Windows Vault which are not protected by Windows Defender Credential Guard with any of these protocols. 

It is strongly recommended that valuable credentials, such as the sign-in credentials, not be used with any of these protocols. If these protocols must be used by domain or Azure AD users, secondary credentials should be provisioned for these use cases.

When Windows Defender Credential Guard is enabled, Kerberos does not allow unconstrained Kerberos delegation or DES encryption, not only for signed-in credentials, but also prompted or saved credentials.

**Note:** Intel TXT fully works when enabled and operates in parallel with Windows Defender Credential Guard.

For a better understanding of what Windows Defender Credential Guard is and what attacks it protects againt, see [Deep Dive into Credential Guard](https://mva.microsoft.com/en-us/training-courses/deep-dive-into-credential-guard-16651).

**IT Professionals:** To learn how to deploy Windows Defender Credential Guard in your enterprise, see [Protect derived domain credentials with Credential Guard](https://docs.microsoft.com/en-us/windows/access-protection/credential-guard/credential-guard#hardware-and-software-requirements).

For a device to support Windows Defender Credential Guard as specified in the Windows Hardware Compatibility Requirements (WHCR), you as the OEM must provide the following hardware, software, or firmware features. 

| Requirement | Details |
|----------------------|---------|
| Secure Boot | Hardware-based Secure Boot must be supported. To learn more, see [Secure Boot](OEM-secure-boot.md). | 
| Secure Boot configuration and management | <ul><li>You must be able to add ISV, OEM, or Enterprise Certificate to the Secure Boot database at manufacturing time. </li><li>Microsoft UEFI CA must be removed from the Secure Boot database. Support for 3rd-party UEFI modules is permitted but should leverage ISV-provided certificates or OEM certificate for the specific UEFI software.</li></ul> |
| Secure firmware update process | Like UEFI software, UEFI firmware can have security vulnerabilities. It is essential to have the capability to immediately patch such vulnerabilities when found through firmware updates. UEFI firmware must support secure firmware update following Hardware Compatibility Specification for Systems for Windows 10 under [System.Fundamentals.Firmware.UEFISecureBoot](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/systems#systemfundamentalsfirmwareuefisecureboot).|
| Trusted Platform Module (TPM) 2.0 | To learn more about TPM, see [Trusted Platform Module](OEM-TPM.md).|
| United Extensible Firmware Interface (UEFI) | To lern more, see [United Extensible Firmware Interface (UEFI) firmware requirements](OEM-UEFI.md). |
| Virtualization-based security (VBS) | Device Guard requires VBS. You can learn more about VBS by reading [Virtualization-based Security (VBS)](OEM-VBS.md). |

## Windows Defender Device Guard and Credential Guard Readiness Tool

To determine if a device is able to run Window Defender Device Guard and Credential Guard, download the [Device Guard and Credential Guard hardware readiness tool](https://www.microsoft.com/en-us/download/details.aspx?id=53337).

## Related topics
-
- [Windows Defender Device Guard hardware requirements](OEM-device-guard.md)
- [Windows Defender Application Guard hardware requirements](OEM-app-guard.md)



 

 







