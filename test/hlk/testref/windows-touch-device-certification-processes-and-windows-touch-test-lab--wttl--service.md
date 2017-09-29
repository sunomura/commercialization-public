---
title: Windows Touch Device Certification Processes and Windows Touch Test Lab (WTTL) Service
description: Windows Touch Device Certification Processes and Windows Touch Test Lab (WTTL) Service
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7484dfcc-0680-404e-a10a-fc109a573ce4
---

# Windows Touch Device Certification Processes and Windows Touch Test Lab (WTTL) Service


This article describes the Windows Touch device certification processes and the Microsoft Windows Touch Test Lab (WTTL) service for vendors and manufacturers of touch digitizers. It contains guidelines about how to use Microsoft testing facilities to certify the touch quality of a device to meet [Windows Hardware Compatibility Program](..\user\windows-hardware-compatibility-program-overview.md) (formerly known as the Windows Certification/Logo Program) requirements.

This information applies for computers that run on Windows 8 and Windows 8.1.

Microsoft introduced Windows Touch for Windows® 7 and extends Windows Touch in Windows 8 and Windows 8.1 to give users control of Windows and applications by using touch input. The WTTL is a Microsoft facility that is established to help partners ensure that their touch devices deliver high-quality touch experiences.

The **Windows 8 Hardware Certification Requirements** document defines Windows touch as a set of standards for devices and systems that support touch input. Because of the importance of the touch user experience, the [Windows Hardware Lab Kit (Windows HLK)](http://go.microsoft.com/fwlink/?LinkID=8705) includes automated tests for Windows touch in addition to a suite of manual tests that include tapping, gesturing, and drawing lines and arcs on the touch screen.

On January 1, 2014, Touch device certification changes from full-test to self-test model. Partners can submit Touch device for certification without sending hardware to WTTL for full-test validation. However, we highly recommend that you continue to utilize the WTTL service as part of development validation step to ensure consistency of testing touch quality. WTTL services remain free of charge.

>[!TIP]
>  
We recommend that you visit the [Windows Hardware Certification blog](http://go.microsoft.com/fwlink/?LinkID=285656) for up-to-date news about the Windows Hardware Certification Program.

 

## <span id="Windows_Touch_device_certification_overview_"></span><span id="windows_touch_device_certification_overview_"></span><span id="WINDOWS_TOUCH_DEVICE_CERTIFICATION_OVERVIEW_"></span>Windows Touch device certification overview


We provide two independent options for Touch device certification:

1.  **Self-Test Submission**. This submission option allows Touch hardware device to be tested at your testing facility, which is same process as other Windows Certification Programs. The expectation for the self-test submission is that the device is tested properly per testing guidance. Certification status is issued based on the Windows HLK submission package that you provide to Microsoft.

    ![self test certification steps](images/winb-hck-selfteststeps.png)

2.  **WTTL Full-Test Submission**. By using this option, you have opportunity to have Microsoft WTTL validate Touch device before obtaining the touch device certification. We highly recommend new partners or new technology use this option to ensure consistency of testing quality and to help you to discover potential issues.

    Before you can receive touch device certification for a device, you must generate a Windows HLK submission package by performing the touch tests in the Windows HLK. After you generate and submit a passing Windows HLK package, the WTTL runs a complete set of Windows touch tests by using the Windows HLK. During this testing, the WTTL uses high-precision assistant tools whenever possible to minimize human error. It tries each test item a maximum of two times.

    If the device passes all tests, the WTTL passes the submission for certification of the touch device. If any tests fail, the WTTL stops the Windows HLK test and issues a report that lists the failed tests. You can choose whether to leave the device at the WTTL for future submissions.

    WTTL sends an email receipt message when it receives a device. The Service Level Agreement is ten business days for WTTL to complete the certification on the condition that the submitted device does not have reliability or setup issues. Device issues that cause device setup or installation failures, or any unstable/unreliable device that prevents WTTL from completing certification tests, automatically results in a submission failure. We recommend that you reserve reasonable time in your product development cycle for both in-house touch testing and for the hardware certification process for devices and systems.

    Microsoft provides the WTTL testing and certification service free of any additional charge. Microsoft will not make any details of the hardware, drivers, test results, or any other information about the submission available to any other company without your prior written approval. Microsoft returns submitted hardware upon request.

    ![full submission certification steps](images/winb-hck-fullsubmissionsteps.png)

## <span id="Touch_device_hardware__submission_requirements"></span><span id="touch_device_hardware__submission_requirements"></span><span id="TOUCH_DEVICE_HARDWARE__SUBMISSION_REQUIREMENTS"></span>Touch device hardware submission requirements


Microsoft does not test devices outside of the requirements for device certification. To ensure that touch performance is properly tested on a submitted device, device submissions should meet the standards listed in the [WTTL Submission Workbook](http://download.microsoft.com/download/7/9/7/79783DA4-9CA3-4612-BB6E-C61310458DBC/WTTL Submission Readiness Checklist .xlsx). Prior to submission, validate all the items that are on the **Submission Readiness Checklist** tab of the **WTTL Submission Workbook**. You must also completely and accurately fill out the **WTTL Submission Template** tab of this workbook, and include it as part of the submission.

## <span id="How_to_submit_a_touch_device_for_certification"></span><span id="how_to_submit_a_touch_device_for_certification"></span><span id="HOW_TO_SUBMIT_A_TOUCH_DEVICE_FOR_CERTIFICATION"></span>How to submit a touch device for certification


Follow the process that is described on the **Directions** tab in the [WTTL Submission Workbook](http://download.microsoft.com/download/7/9/7/79783DA4-9CA3-4612-BB6E-C61310458DBC/WTTL Submission Readiness Checklist .xlsx).

## <span id="WTTL_full-test_validation_process"></span><span id="wttl_full-test_validation_process"></span><span id="WTTL_FULL-TEST_VALIDATION_PROCESS"></span>WTTL full-test validation process


The WTTL uses the following process to validate devices for Windows touch hardware certification qualification:

1.  Set up the device according to the submitted instructions.

2.  Perform a clean install of Windows 8 or Windows 8.1 together with all necessary drivers.

3.  Load the Windows HLK software.

4.  Run the touch tests that are listed for the touch device in the Windows HLK.

5.  Validate each test by following the instructions in [How to run the Windows HLK Tests for Touch and Pen Devices](how-to-run-the-windows-hck-tests-for-touch-and-pen-devices.md). Whenever possible, Microsoft applies high-precision assistant jigs and 9 mm diameter round styluses to minimize human error.

6.  Test each item a maximum of two times. If all tests in the same category are successful on any attempt, WTTL proceeds to the next category of tests. If all tests are not successful, WTTL fails the submission.

7.  For verification of panning latency, WTTL categorizes the devices into 3 different sizes, as follows:

    -   Small form factor (smaller than 12”): run one time at the center of the digitizer.

    -   Medium size device (12” ~ 17”): run two times on the digitizer (left and right, respectively).

    -   Large size device (18” and above): Dissect the screen into three even sections and run panning latency one time on each region respectively (left, center and right).

    This methodology is for WTTL verification only. We expect partners to follow the instructions in the [How to measure Touch Panning Latency](how-to-measure-touch-panning-latency-win81.md) test methodology, and adhere to the requirement that applies to all areas of the display. The latency requirement must be met at any location each time the test is run; that is, you cannot take an average of the test runs at a specific location.

    If the test result is above 15 ms but passes the Windows HLK test, WTTL reruns the test at the same location and if Windows HLK passes the second test pass also, WTTL passes the test.

## <span id="Touch_hardware_quality_assurance"></span><span id="touch_hardware_quality_assurance"></span><span id="TOUCH_HARDWARE_QUALITY_ASSURANCE"></span>Touch hardware quality assurance


Windows 8 and Windows 8.1 touch devices must pass all hardware certification requirements for touch input to function. After a device has passed all of the tests, a hardware signature is issued, which allows Windows 8 and Windows 8.1 to identify the device as certified.

Prior to submission, Microsoft requires that a test signature be placed in firmware in the same location as the final release signature. This requirement guarantees that space is reserved for the release signature after it is granted, and provides a check that the signature is in the right location and can be read as expected. This is an important validation to perform, because the inability to read the release signature causes the device to not function. The tool to validate this is called **GetTHQABlob.exe**. The detail of sample BLOB injection as well as the **GetTHQABlob.exe** location and validation process can be found in **Notes to the checklist** in the [WTTL Submission Workbook](http://download.microsoft.com/download/7/9/7/79783DA4-9CA3-4612-BB6E-C61310458DBC/WTTL Submission Readiness Checklist .xlsx)

## <span id="related_topics"></span>Related topics


[Learn About Windows Hardware Design and Development](http://go.microsoft.com/fwlink/?LinkID=286930)

[Windows Certification Program Policies and Processes](http://go.microsoft.com/fwlink/?LinkID=286928)

[Windows Touch Testing Prerequisites](windows-touch-testing-prerequisites.md)

[Windows Dev Center - Hardware Dashboard Services](http://go.microsoft.com/fwlink/?LinkID=286929)

[How to Use the Precision Touch Testing Tool](http://go.microsoft.com/fwlink/?LinkID=286931)

[Overview of Measuring Touch Down Hardware Latency](http://go.microsoft.com/fwlink/?LinkID=286932)

[Overview of Measuring Touch Panning Hardware Latency](http://go.microsoft.com/fwlink/?LinkID=286933)

[How to Measure Touch Panning Latency](http://go.microsoft.com/fwlink/?LinkID=286934)

[How to Measure Touch Down Latency](http://go.microsoft.com/fwlink/?LinkID=286935)

 

 







