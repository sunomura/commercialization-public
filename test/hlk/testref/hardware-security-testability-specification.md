---
title: Hardware Security Testability Specification
description: Hardware Security Testability Specification
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 206FC620-177D-4435-A7F2-18959E5E208B
---

# Hardware Security Testability Specification


## <span id="Introduction"></span><span id="introduction"></span><span id="INTRODUCTION"></span>Introduction


Version 1.1a

This document details the following sub-requirement of Windows Hardware Certification Requirement:

[System.Fundamentals.Firmware.CS.UEFISecureBoot.Provisioning](p_compat_program.system_fundamentals_firmware_cs_uefisecureboot#system-fundamentals-firmware-cs-uefisecureboot-provisioning)

**Mandatory:  **The platform is required to implement a hardware interface and share documentation and tools as specified in this topic.

>[!NOTE]
>  The reader is expected to know the fundamentals of UEFI and have a basic understanding of Secure Boot (Chapter 27 of the UEFI specification).

 

### <span id="Motivation"></span><span id="motivation"></span><span id="MOTIVATION"></span>Motivation

HSTI protects against misconfiguration of security features on Windows devices. For customers, HSTI provides best effort assurance that the machine they have purchased is secure by default. For IHVs and IBVs, HSTI makes sure your security promises are kept. For OEMs and ODMs easily ensure that the systems you ship are configured securely out of the box and will stay secure, without having to develop proprietary solutions.

The results of HSTI tests will be consumed by Windows Compatibility Tests and can be used to verify that devices have been properly configured to enable supported security features. These testsmay be used to identify unsecured engineering devices in the field, for example, engineering devices which may contain insecure test keys. The results of these tests may be used by the Windows OS to display a watermark (or similar indicator) on insecure devices.

### <span id="Background"></span><span id="background"></span><span id="BACKGROUND"></span>Background

The reader is expected to know the fundamentals of UEFI and have an understanding of Secure Boot technologies including Section 27 “Security” of the UEFI specification and NIST SP 800-147.

This requirement has three aspects:

-   Platform independent interfaces for querying hardware and firmware security states
-   Design and optional code review of the above interface implementations
-   Sharing of documentation and tools

### <span id="High_Level_Implementation"></span><span id="high_level_implementation"></span><span id="HIGH_LEVEL_IMPLEMENTATION"></span>High Level Implementation

### <span id="The_Bitfield"></span><span id="the_bitfield"></span><span id="THE_BITFIELD"></span>The Bitfield

The IHV defines a bitfield representing the testable security features of the platform. This bitfield fully covers all defineable bits available for the HSTI objects returned by any IHV, IBV or OEM HSTI tests. The IHV implementor has to design the definition of the bitfield and provide appropriate documentation in order for IBVs to correctly return the results of their HSTI tests.

### <span id="SecurityFeaturesRequired"></span><span id="securityfeaturesrequired"></span><span id="SECURITYFEATURESREQUIRED"></span>SecurityFeaturesRequired

The SecurityFeaturesRequired field is only used in processing when a field in an IHV HSTI object and is the method by which the IHV defines the bitfield of required security features.

### <span id="SecurityFeaturesImplemented"></span><span id="securityfeaturesimplemented"></span><span id="SECURITYFEATURESIMPLEMENTED"></span>SecurityFeaturesImplemented

This is a bitfield of the security features implemented by the tests returning the HSTI object.

### <span id="SecurityFeaturesVerified"></span><span id="securityfeaturesverified"></span><span id="SECURITYFEATURESVERIFIED"></span>SecurityFeaturesVerified

This is a bitfield of the security features which have been verified by the tests returning the HSTI object.

### <span id="Implementation_Guidelines"></span><span id="implementation_guidelines"></span><span id="IMPLEMENTATION_GUIDELINES"></span>Implementation Guidelines

The IHV will develop reference security designs for their platforms that comply with the Windows Compatibility Requirements. In addition, IHVs and IBVs will also implement programmatic tests that verify proper enablement of the reference security implementations and report the results via the Hardware Security Test Interface. These tests are delivered to OEMs & ODMs as compiled modules (not source) and should work without modification. If an OEM/ODM deviates from reference security designs, these test modules may report failures, and the OEM/ODM will need to contact Microsoft to review the modifications and implement an additional HSTI instance that reports these exceptions. OEMs should be able to leverage these security modules with no modification required by following the reference design and documentation. OEMs who wish to add additional security modules, or modify the behavior of any security module, must undergo a design review with Microsoft.

As part of their implementation of tests module implementors will include a struct. A prototype of this struct is included below in the “Prototype section”. The IHV will define the meaning of each bit in the security reference checklist. The IHV will further define the meaning of each bit in the bitfields. Finally, the IHV includes a “Required” bitfield in the OEM struct, and for all requirements they are able to test programmatically they will set a bit in the “Implemented” bitfield.

IBVs and OEMs may set bits in the “Implemented” field if they have presented a design to progamatically check for the presence of the security features represented by those bits to Microsoft. If those tests pass they may set the “Verified” field in their respective structs.

The test modules for IHV, IBV and OEM shall be run if present. A true value set at a bit in the SecurityFeaturesEnabled field indicates a passing test result. If a test is not run, or does not pass, a value of 0 shall be set for the representative bit.

### <span id="Result_Processing_Logic_Example"></span><span id="result_processing_logic_example"></span><span id="RESULT_PROCESSING_LOGIC_EXAMPLE"></span>Result Processing Logic Example

This example is representative of the logic that will be used by the results processing. Implemented bitfields must follow the format that a 1 means implemented and a 0 means not implemented. If something is implemented it is required. Results bitfields must follow the format that a 0 means failed or test not present and a 1 means affirmatively passed only.

After all results have been calculated, the IHV Results bitfield will be NXORd with their Required bitfield. All non-IHV Results bitfields are ANDed with their respective Implemented bitfields. The resulting bitfields are all ORd together to get the overall results. A passing result of this operation will be a bitfield consisting of entirely 1s.

## <span id="Deliverables_and_Ownership"></span><span id="deliverables_and_ownership"></span><span id="DELIVERABLES_AND_OWNERSHIP"></span>Deliverables and Ownership


### <span id="Independent_Hardware_Vendors__IHVs__and_Independent_BIOS_Vendors__IBVs_"></span><span id="independent_hardware_vendors__ihvs__and_independent_bios_vendors__ibvs_"></span><span id="INDEPENDENT_HARDWARE_VENDORS__IHVS__AND_INDEPENDENT_BIOS_VENDORS__IBVS_"></span>Independent Hardware Vendors (IHVs) and Independent BIOS Vendors (IBVs)

Silicon Suppliers and IBVs who support Connected Standby systems must implement the platform independent interfaces for querying the respective hardware and firmware security states of their reference platforms. These implementations must be delivered as compiled modules. It is preferred that these modules be signed, and a signature check is performed when they are run. The purpose is to query the hardware and firmware designs & states to report proper security provisioning of the platform.

### <span id="OEMs_and_ODMs"></span><span id="oems_and_odms"></span><span id="OEMS_AND_ODMS"></span>OEMs and ODMs

OEMs and ODMs must not modify or tamper with the HSTI tests which have been provided to them by vendors. OEMs and ODMs are required to guarantee that their systems will pass the HSTI tests as a component of the Windows Certification requirements:

Windows Hardware Certification Requirement – [Windows 8.1 WHCR](http://msdn.microsoft.com/en-us/library/windows/hardware/jj128256.aspx)

-   System.Fundamentals.Firmware.UEFISecureBoot
-   System.Fundamentals.Firmware.CS.UEFISecureBoot.ConnectedStandby

Instead of modification, if an OEM requires a method to provide an alternate method to provide the same or better security, that OEM may provide additional security checks. OEM security checks must at least fully cover one IHV or IBV security test. Before use, OEMs must submit to a design review by Microsoft and are subject to the same Documentation and Tool disclosure requirements as other HSTI test providers. Upon approval from Microsoft, the OEM may include security tests which extend upon the IHV and IBV tests.

Note that OEM attestation is not required as part of the HSTI design. HSTI is not a list of requirements for OEMs, it is an interface to guarantee effective programmatic security testing of firmware, hardware and configuration parameters.

## <span id="Security_State_Interfaces"></span><span id="security_state_interfaces"></span><span id="SECURITY_STATE_INTERFACES"></span>Security State Interfaces


The interfaces are built on the EFI Adapter Information Protocol defined in UEFI version 2.4.

### <span id="Platform_Security_State_Interface"></span><span id="platform_security_state_interface"></span><span id="PLATFORM_SECURITY_STATE_INTERFACE"></span>Platform Security State Interface

### <span id="Summary"></span><span id="summary"></span><span id="SUMMARY"></span>Summary

**Platform Security Information** – Returns information about the platform’s conformance with Windows Hardware Certification Requirement System.Fundamentals.Firmware.CS.UEFISecureBoot, System.Fundamentals.Firmware.CS.UEFISecureBoot.ConnectedStandby and System.Fundamentals.Firmware.CS.UEFISecureBoot.Provisioning.

### <span id="Prototype"></span><span id="prototype"></span><span id="PROTOTYPE"></span>Prototype

InformationType

``` syntax
#define ADAPTER_INFO_PLATFORM_SECURITY_GUID \
     {0x6be272c7, 0x1320, 0x4ccd, { 0x90, 0x17, 0xd4, 0x61, 0x2c, 0x01, 0x2b, 0x25 }}

#define PLATFORM_SECURITY_VERSION_VNEXTCS   0x00000003

#define PLATFORM_SECURITY_ROLE_PLATFORM_REFERENCE   0x00000001  // IHV
#define PLATFORM_SECURITY_ROLE_PLATFORM_IBV 0x00000002
#define PLATFORM_SECURITY_ROLE_IMPLEMENTOR_OEM 0x00000003 
#define PLATFORM_SECURITY_ROLE_IMPLEMENTOR_ODM  0x00000004  
                        
```

Corresponding InformationBlock:

``` syntax
typedef struct { 
    UINT32  Version,
    UINT32  Role,
    CHAR16  ImplementationID[256],
    UINT32  SecurityFeaturesSize,
    UINT8   SecurityFeaturesRequired[],     //Ignored for non-IHV
    UINT8   SecurityFeaturesImplemented[],
    UINT8   SecurityFeaturesVerified[],
    // CHAR16   ErrorString[];
} ADAPTER_INFO_PLATFORM_SECURITY;
                        
```

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Term</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span id="Version"></span><span id="version"></span><span id="VERSION"></span>Version</p></td>
<td><p>Return PLATFORM_SECURITY_VERSION_VNEXTCS</p></td>
</tr>
<tr class="even">
<td><p><span id="Role"></span><span id="role"></span><span id="ROLE"></span>Role</p></td>
<td><p>The role of the publisher of this interface. Reference platform designers such as IHVs and IBVs are expected to return PLATFORM_SECURITY_ROLE_PLATFORM_REFERENCE and PLATFORM_SECURITY_ROLE_PLATFORM_IBV respectively. If the test modules from the designers are unable to fully verify all security features, then the platform implementers, OEMs and ODMs, will need to publish this interface with a role of Implementer.</p></td>
</tr>
<tr class="odd">
<td><p><span id="ImplementationID"></span><span id="implementationid"></span><span id="IMPLEMENTATIONID"></span>ImplementationID</p></td>
<td><p>Human readable vendor, model, &amp; version of this implementation. For example “SiliconVendorX Chip1234 v1” and “BIOSvendorY BIOSz v2”.</p></td>
</tr>
<tr class="even">
<td><p><span id="SecurityFeaturesSize"></span><span id="securityfeaturessize"></span><span id="SECURITYFEATURESSIZE"></span>SecurityFeaturesSize</p></td>
<td><p>The size in bytes of the SecurityFeaturesRequired and SecurityFeaturesEnabled arrays. The arrays must be the same size.</p></td>
</tr>
<tr class="odd">
<td><p><span id="SecurityFeaturesRequired"></span><span id="securityfeaturesrequired"></span><span id="SECURITYFEATURESREQUIRED"></span>SecurityFeaturesRequired</p></td>
<td><p>IHV-defined bitfield corresponding to all security features which must be implemented to meet the security requirements defined by PLATFORM_SECURITY_VERSION Version. For example, 7 features may be required to be implemented to satisfy Version, a value of 0b01111111 might be reported.</p></td>
</tr>
<tr class="even">
<td><p><span id="SecurityFeaturesImplemented"></span><span id="securityfeaturesimplemented"></span><span id="SECURITYFEATURESIMPLEMENTED"></span>SecurityFeaturesImplemented</p></td>
<td><p>Publisher-defined bitfield corresponding to all security features which have implemented programmatic tests in this module.</p></td>
</tr>
<tr class="odd">
<td><p><span id="SecurityFeaturesVerified"></span><span id="securityfeaturesverified"></span><span id="SECURITYFEATURESVERIFIED"></span>SecurityFeaturesVerified</p></td>
<td><p>Publisher-defined bitfield corresponding to all security features which have been verified implemented by this implementation.</p></td>
</tr>
<tr class="even">
<td><p><span id="ErrorString"></span><span id="errorstring"></span><span id="ERRORSTRING"></span>ErrorString</p></td>
<td><p>A Null-terminated string, one failure per line (CR/LF terminated), with a unique identifier that the OEM/ODM can use to locate the documentation which will describe the steps to remediate the failure – a URL to the documentation is recommended. For example, “0x4827 JTAG not disabled http://somewhere.net/docs/remediate4827.html \r\n0x2744 Platform Secure Boot key not provisioned http://somewhere.net/docs/remediate2744.html”</p></td>
</tr>
</tbody>
</table>

 

### <span id="Memory_Management_Considerations"></span><span id="memory_management_considerations"></span><span id="MEMORY_MANAGEMENT_CONSIDERATIONS"></span>Memory Management Considerations

For compatibility purposes between HSTI modules, implementors shall use AllocatePool() and not AllocatePages().

## <span id="Design_review_of_HSTI_Implementation"></span><span id="design_review_of_hsti_implementation"></span><span id="DESIGN_REVIEW_OF_HSTI_IMPLEMENTATION"></span>Design review of HSTI Implementation


Microsoft shall conduct preliminary design reviews of all test interface implementations. Examples of the questions that may be asked in a design review are provided in the HSTI Design Considerations section.

## <span id="Optional_Code_Reviews"></span><span id="optional_code_reviews"></span><span id="OPTIONAL_CODE_REVIEWS"></span>Optional Code Reviews


HSTI implementers may request code reviews performed by Microsoft. Code reviews may be provided based on the priority and availability of resources and are not guaranteed. Code reviews will take place subject to a Non Disclosure Agreement.

## <span id="Documentation_and_Tools_sharing"></span><span id="documentation_and_tools_sharing"></span><span id="DOCUMENTATION_AND_TOOLS_SHARING"></span>Documentation and Tools sharing


Silicon and firmware suppliers should make available to Microsoft all necessary security-related reference documentation and tools that they provide to OEMs. This documentation and tools should be made available no later than they are provided to Windows OEMs. This should include, but is not limited to, all documentation and tools related to fusing, installing and updating firmware, firmware and boot recovery, hardware diagnostics, firmware diagnostics, & boot diagnostics. This documentation and tools provided should be fully sufficient to perform HSTI checks in a lab environment.

## <span id="HSTI_Design_Considerations"></span><span id="hsti_design_considerations"></span><span id="HSTI_DESIGN_CONSIDERATIONS"></span>HSTI Design Considerations


The following is an illustrative list of design considerations that an HSTI implementor must consider for their HSTI implementation. This is not a strict list of requirements, nor is it an exhaustive list of considerations. As an HSTI implementor you will be writing tests to validate the security features you have working towards as comprehensive coverage as possible. Before your design review with Microsoft we recommend you review this list for inspiration, and consider that Microsoft is likely to desire that if you implement these features you test them as extensively as possible.

### <span id="Silicon_Suppliers_Vendor__IHV__HSTI_Checks"></span><span id="silicon_suppliers_vendor__ihv__hsti_checks"></span><span id="SILICON_SUPPLIERS_VENDOR__IHV__HSTI_CHECKS"></span>Silicon Suppliers/Vendor (IHV) HSTI Checks

1.  Do you use RSA 2048 and SHA256 only (or similar crypto strength)
2.  Firmware Code must be present in protected storage
    1.  Do you protect spiflash?
    2.  Do you implement read-only till reset for eMMC partitions
    3.  Do you support Signed Firmware Check – Firmware that is installed by OEM is either read-only or protected by secure firmware update process.
3.  Secure firmware update process
    1.  Is secure firmware update process on by default with test keys? (RECOMMENDED)
    2.  Do you check if test keys are used in production?
    3.  Do you allow rollback to insecure firmware version? If yes then what is the protection mechanism? Do you clear TPM when rollback happens?
4.  Do you have backdoors to override SecureBoot
    1.  Does your system support inline prompting to bypass Secureboot? If yes then is it disabled while SecureBoot is enabled?
    2.  Do you have manufacturing backdoors? Do you check for them to be disabled while SecureBoot is enabled and always disabled in production system?
5.  \[CS\]Boot Integrity Support
    1.  Do you support Boot Integrity and is it enabled by default?
    2.  Platform uses on-die ROM or One-Time Programmable (OTP) memory for storing initial boot code and provides power-on reset logic to execute from on-die ROM or secure on-die SRAM.
6.  \[CS\]Protection from internal and external DMA
    1.  Do you keep internal DMA on only for components required during boot? And is disabled for all other components.
    2.  Do you keep external DMA on only for components required during boot? And is disabled for all other components.
    3.  If firmware has an option to enable and disable DMA protection, shipping configuration must have DMA protection enabled by default
    4.  What buses/devices (fuses, security engines, TZ, video, caches, IMEM, kernel memory) are capable of DMA access to different NV and volatile storage regions and how are they protected?
    5.  Do you support MOR bit implementation
7.  Protection against external hardware debugger
    1.  Do you support JTAG? Is JTAG OFF when SecureBoot is ON
    2.  Do you provide manufacturing backdoor to disable JTAG protection? Do you check if this backdoor is not present in production systems?
    3.  Do you clear TPM when JTAG is enabled?
    4.  Do you support any other hardware debugger? And do the same checks for it.
8.  Have you provisioned per device unique secret correctly?
9.  What are the security fuses you have (vendor specific)
    1.  SOC SecureBoot fuse
    2.  Per-device-unique secrets such as endorsement or encypherment fuses
    3.  JTAG fuses
    4.  SOC Apps Processor SecureBoot fuse
    5.  SOC MBA Processor SecureBoot fuse
    6.  SOC Modern Processor SecureBoot fuse
    7.  Any other SOC specific fuses for your platform

### <span id="IBV_HSTI_Checks"></span><span id="ibv_hsti_checks"></span><span id="IBV_HSTI_CHECKS"></span>IBV HSTI Checks

1.  Do you use RSA 2048 and SHA256 only (or higher but not lower than this)
2.  Compatibility Support Modules (CSM)
    1.  Do you provide option to enable CSM
    2.  Do you check blocking of loading CSM when SecureBoot is enabled
    3.  \[CS\]Do you check if CSM is not present on CS systems permanently
3.  Firmware Code must be present in protected storage
    1.  Do you protect spiflash?
    2.  Do you implement read-only till reset for eMMC partitions
    3.  Do you support Signed Firmware Check – Firmware that is installed by OEM is either read-only or protected by secure firmware update process.
4.  Secure firmware update process
    1.  Is secure firmware update process on by default with test keys?
    2.  Do you check if test keys are used in production?
    3.  Do you allow rollback to insecure firmware version? If yes then what is the protection mechanism? Do you clear TPM when rollback happens?
    4.  Are test keys being used?
5.  Do you have backdoors to override SecureBoot
    1.  Does your system support inline prompting to bypass Secureboot? If yes then is it disabled while SecureBoot is enabled?
    2.  Do you have manufacturing backdoors? Do you check for them to be disabled while SecureBoot is enabled and always disabled in production system?
6.  \[CS\]Protection from internal and external DMA
    1.  Do you keep internal DMA on only for components required during boot? And is disabled for all other components.
    2.  Do you keep external DMA on only for components required during boot? And is disabled for all other components.
    3.  If firmware has an option to enable and disable DMA protection, shipping configuration must have DMA protection enabled by default
    4.  What buses/devices (fuses, security engines, TZ, video, caches, IMEM, kernel memory) are capable of DMA access to different NV and volatile storage regions and how are they protected?
    5.  Do you support MOR bit implementation

 

 






