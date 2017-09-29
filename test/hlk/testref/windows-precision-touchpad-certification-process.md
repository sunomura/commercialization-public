---
title: Windows Precision Touchpad Certification Process
description: Windows Precision Touchpad Certification Process
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 69ee5efa-94b5-4e40-83f8-8040fab8b36a
---

# Windows Precision Touchpad Certification Process


This paper provides information about how to certify Precision Touchpad (PTP) devices and systems for Windows 8.1.

There are two stages of Precision Touchpad (PTP) certification: *device-level* and *system-level*. Device-level certification is achieved by performing the self-test device certification via the Windows Hardware Lab Kit (HLK) and submitting the passing HLKX submission package to Microsoft. Optionally, partners will have the ability to submit a PTP device to the Windows Precision Touchpad Test Lab (WPTL) for development validation prior to a self-test submission.

PTP system certification is achieved by integrating a certified PTP device into a system or dock and then performing the self-test system certification and submitting the passing HLKX package.

**In this topic:**

-   [PTP device certification](#device)

-   [PTP device re-certification](#devicerecert)

-   [PTP system certification](#system)

-   [PTP certification FAQs](#faq)

## <span id="device"></span><span id="DEVICE"></span>PTP device certification


A PTP module is defined as the combination of a unique PTP controller IC and PTP sensor PCB. Each distinct PTP module must have a unique PID that is exposed to the host, and must be a separate device submission.

Multiple systems and docks may use the same certified PTP module with differing sensor covers, hinges and bus connectivity.

The IHV for the module typically undertakes its submission to Microsoft. Submission prerequisites are as follows:

-   Self-run all device level PTP certification tests in the Windows Hardware Lab Kit (HLK) and generate a fully passing HLKX package.

-   Complete [WPTL Touchpad Submission Workbook](http://download.microsoft.com/download/E/C/1/EC1F5246-DDD8-4609-AC39-EB2659CEF3FC/WPTL Touchpad Submission Workbook.xlsx) and submit passing HLKX package by using the Windows Dev Center – Hardware Dashboard.

Upon receipt of the passing submission, WPTL shall issue a 256-byte certified PTPHQA Binary Large Object (BLOB) (tied to the PTP module).

## <span id="devicerecert"></span><span id="DEVICERECERT"></span>PTP device re-certification


Any modifications to the physical components of the PTP module shall render the device ineligible for re-certification. This type of change requires a new PID be assigned to the device and a new PTP module submission must be made.

Firmware revisions of a previously certified PTP module are required to be re-certified by using the same PID.

Prerequisites and processes for the firmware recertification are the same as the initial certification process, with the following exceptions:

-   The module must contain its previously issued certified or exception level PTPHQA BLOB.

    A module that is being re-certified must not contain the sample BLOB.

-   A new PTPHQA BLOB shall not be issued for a device that passes re-certification.

## <span id="system"></span><span id="SYSTEM"></span>PTP system certification


When a certified PTP module is integrated into a system or a dock, various aspects can impact both the device’s performance and the previously certified behavior.

Unique integration aspects include, but are not limited to:

-   EMI/RF noise (i.e. charging circuitry, antenna placement, etc.)

-   Activation Force (hinge design and placement)

-   Sensor Cover (dielectric constant, smoothness, flex, etc.)

-   Bezel/Sensor Cover – Palm Deck Demarcation

-   Bus Connectivity (I²C or USB, use of a bridge chip)

-   Wake Capability

To make sure that the certified module performs after system integration, a subset of the device level Windows HLK tests must be passed in a system submission with the Windows HLK. After all applicable system Windows HLK tests successfully pass, the system builder may submit the passing HLKX log using the Dev Center – Hardware Dashboard to receive system certification.

## <span id="faq"></span><span id="FAQ"></span>PTP certification FAQs


**What are the permissible ways to integrate a PTP?**

A PTP module can be integrated in to any system (clamshell/convertible) or dock accessory that also has an integrated keyboard. Stand-alone external PTP modules are not currently permitted for device submission.

**As an OEM, I am building a dock accessory with an integrated PTP module, The dock is compatible with multiple systems. The IHV submitted the dock with one of the supported systems; do the other systems need to be submitted for certification?**

No, the other systems do not need to be submitted for device certification because each system is using the same module. It is strongly recommended that the system certification tests be performed on all systems that can interface with the dock accessory.

**As an IHV, I have received device certification for PTP module “X”. I have multiple customers for PTP module “X”, where each customer’s system requires different firmware. Do I need a separate device submission for each system into which it will be integrated?**

Yes, if your architecture requires unique firmware for each integration project, then the module must be certified with each firmware version. The module’s VID/PID shall remain the same; however, its revision ID is different for each project.

**As an IHV, I have received device certification for PTP module “Y”. I have two customers for PTP module “Y”, where one customer wants a slightly smaller PTP. Do I need a separate device submission for each customer?**

Yes, a change in sensor size (even if the controller and associated firmware remains constant), represents a new module and will require a new device submission.

**When I have re-certified the PTP module at the device level, do I need to recertify at the system level as well?**

Yes, the system level tests must be run with the re-certified module to ensure that the integration of the recertified module is successful and the passing system HLK results submitted.

**What are the rules for third-party drivers and OS Build?**

PTPs must function without any third party drivers, except for I²C devices that might require GPIO and I²C controller drivers to function. These drivers are permissible and, if needed for device certification, should be submitted together with the system because the operating system will be clean-installed upon receipt.

## <span id="related_topics"></span>Related topics


[Windows Precision Touchpad HLK Requirements](windows-precision-touchpad-hck-requirements.md)

[Windows Precision Touchpad Device Validation Guide](windows-precision-touchpad-device-validation-guide.md)

 

 







