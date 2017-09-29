---
title: Windows Hardware Compatibility Program
description: Windows Hardware Compatibility Program
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6ab76249-c075-4995-a2be-61a73e6c3bbe
---

# Windows Hardware Compatibility Program


The new Windows Hardware Compatibility Program is an evolution of the Windows Logo Program and the Windows Hardware Certification Programs. It is designed to help your company deliver systems, software and hardware products that are compatible with Windows and run reliably on Windows 10 for desktop editions (Home, Pro, Enterprise, and Education), Windows 10 Mobile and the next version of Windows Server.

Like previous versions, the new Windows Hardware Compatibility Program leverages the tests in the new Hardware Lab Kit (formerly the Hardware Certification Kit) to test your product. After passing certain tests, the program allows you to use the Windows logo as part of your marketing. End users trust the Windows logo as a sign of compatibility. Enterprise and government customers also look for the logo, or consult the Microsoft Certified Products list or the server catalog to see what systems, components and peripherals have been tested to ensure interoperability and reliability.

The new hardware compatibility program provides you with:

-   Minimum engineering requirements that you can use to design your hardware.
-   A subset of the tests in the new Hardware Lab Kit (formerly the Hardware Certification Kit) that focus on compatibility, interoperability and reliability.
-   The opportunity to list your product on Microsoft’s Certified Products List after passing the compatibility and reliability tests.
-   Guidance for developing, testing and distributing drivers.
-   Access to the Windows Dev Center hardware dashboard to manage submissions, track the performance of your device or app, review telemetry and much more.

## <span id="Windows_Hardware_Compatibility_Program__Requirements"></span><span id="windows_hardware_compatibility_program__requirements"></span><span id="WINDOWS_HARDWARE_COMPATIBILITY_PROGRAM__REQUIREMENTS"></span>Windows Hardware Compatibility Program Requirements


The requirements define how to build Windows-compatible devices, systems, and filter drivers across all Windows Platforms. They were developed in collaboration with partners, and focus on ensuring compatibility, interoperability and reliability.

The requirements are validated by HLK tests and categorized as:

-   System requirements

-   Device and peripheral requirements for a stand-alone device

-   • Filter driver requirements Windows Filtering Platform drivers (WPF), file system filter drivers, antivirus, and Early Launch Anti-Malware (ELAM) filter drivers.

When products meet the minimum requirements it ensures that the application and device are compatible. Systems are required to use components which have also passed compatibility testing. Products submitted with passing results will continue to be included on the Certified Products List.

### <span id="New_IHV_Attested_Signing_Service"></span><span id="new_ihv_attested_signing_service"></span><span id="NEW_IHV_ATTESTED_SIGNING_SERVICE"></span>New IHV Attested Signing Service

For Windows 10, Microsoft is creating a new service for IHVs who just need to get a driver signed for production. IHVs can go to the Windows Dev Center – Hardware Dashboard and request a signed driver by attesting to the quality. This process does not require HLK test results. Under this process the IHV would affirm the following in order to get a Microsoft signed driver:

-   IHV attests that they have completely tested their driver
-   IHV attests that their product and driver will not break interoperability
-   IHV attests that they will monitor telemetry and remediate any issues (exact metrics to be determined at a later date)

When an IHV agrees to these terms, a signed driver will be returned. This signed driver can be distributed to end users, and eventually distributed via Windows Update. However, the driver cannot be used in a Compatibility Test System and the product will not be listed on the Certified Products List. The signature that is returned from this process is different than one that is returned after you submit HLK test results to Microsoft. However, functionally there is no difference between the two signatures.

This option is only available for Windows 10 Mobile and Windows 10 for desktop editions operating system. The IHV Attested Signing Service is not available for the next version of Windows Server.

For more details about building your system, see:

-   Minimum Hardware Specification - This specification defines the minimum hardware requirements necessary to:
    -   Boot and run Windows 10.
    -   Update and service Windows 10.
    -   Provide a baseline user experience that is comparable with similar devices and computers.
-   Windows Hardware Compatibility Specification - This specification defines the engineering requirements for passing the Windows Hardware Compatibility Program.
-   Windows Engineering Guidance – This document is focused on documenting guidance to build products that deliver the best in class user experience.

 

 






