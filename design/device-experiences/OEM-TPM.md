---
title: Trusted Plaform Module (TPM) 2.0 
description: Provides guidance on what an OEM should know about TPM 2.0 and the features that require it
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.author: dawnwood
ms.date: 10/05/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

#Trusted Platform Module 2.0

Trusted Platform Module (TPM) technology is designed to provide hardware-based, security-related functions. A TPM chip is a secure crypto-processor that helps you with actions such as generating, storing, and limiting the use of cryptographic keys. Many TPMs include multiple physical security mechanisms to make it tamper resistant, and malicious software is unable to tamper with the security functions of the TPM. 

Traditionally, TPMs have been discrete chips soldered to a computer’s motherboard. Such implementations allow you as the original equipment manufacturer (OEM) to evaluate and certify the TPM separate from the rest of the system. Some newer TPM implementations integrate TPM functionality into the same chipset as other platform components while still providing logical separation similar to discrete TPM chips.

TPMs are passive: they receive commands and return responses. To realize the full benefit of a TPM, you must carefully integrate system hardware and firmware with the TPM to send it commands and react to its responses. TPMs provide security and privacy benefits for system hardware, platform owners, and users. 

Before it can be used for advanced scenarios, however, a TPM must be provisioned. Starting with Windows 10, the operating system automatically initializes and takes ownership of the TPM. That means that IT professionals should not have to configure or monitor the system. 

For more information about the specific requirements that must be met, see [System.Fundamentals.TPM20](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/1703/systems#system.fundamentals.tpm20). 

Since July 28, 2016, all new device models, lines or series (or if you are updating the hardware configuration of a existing model, line or series with a major update, such as CPU, graphic cards) must implement and enable by default TPM 2.0 (details in section 3.7 of the [Minimum hardware requirements page](https://msdn.microsoft.com/library/windows/hardware/dn91508.aspx)). The requirement to enable TPM 2.0 only applies to the manufacturing of new devices. 

**IT Professionals:** To understand how TPM works in your enterprise, see [Trusted Platform Module](https://docs.microsoft.com/en-us/windows/device-security/tpm/trusted-platform-module-top-node).


### Related topics
- [Trusted Platform Module Overview](https://docs.microsoft.com/en-us/windows/device-security/tpm/trusted-platform-module-overview)
- [How Windows 10 uses the Trusted Platform Module](https://docs.microsoft.com/en-us/windows/device-security/tpm/how-windows-uses-the-tpm)
- [TPM recommendations](https://docs.microsoft.com/en-us/windows/device-security/tpm/tpm-recommendations)