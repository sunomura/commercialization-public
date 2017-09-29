---
title: HLK Testing Concepts
description: HLK Testing Concepts
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 15d6d8d8-71ad-4f2a-99b0-1c9d704d2adf
---

# HLK Testing Concepts


Windows HLK testing is based on feature detection. Windows HLK determines what a part of a device needs to be tested by detecting the functionality of the device or system.

## <span id="Terminology"></span><span id="terminology"></span><span id="TERMINOLOGY"></span>Terminology


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Term</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Feature</p></td>
<td><p>A feature is a Windows capability exposed by a device. When you connect a device to a Windows HLK environment, the kit searches for features on the device using a mechanism called gatherers. Features are organized using a namespace style, for example, Device.Graphics.WDDM12, System.Client.BluetoothController.Base, and Filter.Driver.Network.LWF. A target device or system can detect many features.</p></td>
</tr>
<tr class="even">
<td><p>Requirement</p></td>
<td><p>A requirement is the official specification that defines what a feature must do to qualify for the Windows hardware compatibility list. Requirements are organized using a namespace style. For example Device.Imaging.Scanner.Base.RawFileFormat is a requirement for the Device.Imaging.Scanner.Basefeature. There can be many requirements associated with a single feature.</p></td>
</tr>
<tr class="odd">
<td><p>Test</p></td>
<td><p>Tests validate that features are implemented on a device or system in accordance with requirements. Each test has a pointer to the requirement(s) it validates.</p></td>
</tr>
<tr class="even">
<td><p>Product type</p></td>
<td><p>A product that contains a predefined list of testable features. To be listed on the Windows Hardware Compatibility list, a product must implement all of the features of at least one product type.</p></td>
</tr>
<tr class="odd">
<td><p>Project</p></td>
<td><p>A project is a submission that is sent to Microsoft that encompasses all of the architectures and platforms for the certification request. You can combine different projects into a larger project for submission through the process of creating a package.</p></td>
</tr>
<tr class="even">
<td><p>Product Instance</p></td>
<td><p>A product instance is collection of devices on a single platform. Unlike a target family, which is a collection of effectively identical devices, devices in the product instance can be similar or dissimilar. Each platform must be tested individually, though you can use multiple machines to test in parallel with other product instances.</p></td>
</tr>
<tr class="odd">
<td><p>Device Family</p></td>
<td><p>A device family is a collection of hardware IDs that are cached in the datastore under a common name. A device family is used to define a family of similar devices that may have different hardware IDs. A device family is one of the criteria used to identify similar targets in a target family.</p></td>
</tr>
<tr class="even">
<td><p>Target Family</p></td>
<td><p>A target family is a collection of targets within a single device family. For the purposes of testing, targets in a target family are treated as identical, allowing jobs to run in parallel across all targets in the target family. Unlike a product instance, which is a collection of dissimilar devices, a target family is a collection of effectively identical devices.</p></td>
</tr>
<tr class="odd">
<td><p>Target</p></td>
<td><p>A target is any hardware, software driver, or system that can be individually addressed and tested.</p></td>
</tr>
</tbody>
</table>

 

## <span id="How_it_works"></span><span id="how_it_works"></span><span id="HOW_IT_WORKS"></span>How it works


In the following example, a multi-function printer device contains several features: It's a scanner, an Ethernet network port, a storage reader, and a printer. Windows HLK detects each feature, determines the associated requirements for it, and then runs a corresponding test to verify that the requirements are implemented correctly.

![windows hck feature detection process](images/hck-win8-feature-detection-process.gif)

## <span id="Best_Practices"></span><span id="best_practices"></span><span id="BEST_PRACTICES"></span>Best Practices


In addition to understanding the terminology and logic, consider these best practices:

-   Design your hardware using the **Windows Hardware Requirements**.

-   Review the [test reference](..\testref\hardware-lab-kit-test-reference.md) for your device before testing. Any Windows HLK test may require a specific configuration. The more complex the device, the more complex the test configuration.

-   Manual tests require more time and preparation. You should run manual steps separately from automated tests. When you connect a device to Windows HLK, you can sort detected test by automated and manual. To learn more about any test, select the test from Windows HLK Studio and press F1 for Help.

-   Ensure that your test server contains the latest QFE and filters. We periodically release updated tests. For more info, see [Windows Hardware Certification](http://go.microsoft.com/fwlink/p/?LinkID=236110) in the Windows Dev Center.

-   Use the test levels to test basic, functional, reliability and certification tests in that order as the different levels provide testing from basics to functionally complete devices.

## <span id="Testing_Strategy"></span><span id="testing_strategy"></span><span id="TESTING_STRATEGY"></span>Testing Strategy


The complexity of a device determines the complexity of a test. It can be as simple as connecting the device and running the test, or it can require additional hardware resources, extensive configuration, and/or active use. Considering your knowledge of the device and previous versions of this kit, you can approach testing two ways:

-   Connect the device to a Windows HLK environment. Let the kit detect features and the corresponding tests to run against the device. Press F1 on each identified test to review any prerequisites for it.

-   Review the Windows HLK Users Guide in advance. Review the Test Reference section for the specific technologies implemented in your device, specifically the "Prerequisite" topic for each area.

-   Take advantage of multi-device and distributed testing features to reduce overall test time. For more information, see [Configuration Page - Machine Management](configuration-page---machine-management.md).

## <span id="Test_Automation_Support"></span><span id="test_automation_support"></span><span id="TEST_AUTOMATION_SUPPORT"></span>Test Automation Support


For partners interested in automating their test environment, Windows HLK provides scripting and application programming interface (API) support.

-   [HLK Automation Tool](hlk-automation-tool.md) – a scripting solution based on Windows PowerShell® that enables you to automate a test pass.

-   [HLK Developer Guide](..\developer\hlk-developer-guide.md) – a collection of Windows HLK API that enables you to automate any part of the certification test process. The API exposes all functionality of Windows HLK Studio, so you can use both Windows HLK Studio and automation in your certification test workflow.

## <span id="Test_taxonomy_"></span><span id="test_taxonomy_"></span><span id="TEST_TAXONOMY_"></span>Test taxonomy


The Windows HLK introduces a new set of test types.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Test type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Development tests</p></td>
<td><p>Tests that assist in the bring up and development process. These BVT-like functional tests provide basic functionality and compliance checks and rich debug information. Additionally, this type of test may perform code quality testing.</p></td>
</tr>
<tr class="even">
<td><p>Compatibility tests</p></td>
<td><p>These are tests required for the Hardware Compatibility program.</p>
<p>These tests validate compliance with Windows feature implementation and compatibility with Windows. When all of these tests pass for a given device/driver/system, the target under test can be said to be feature complete and Windows compatible.</p>
<p>At this stage, you are ready to submit your drivers/devices/systems to be included on the Windows Compatibility list.</p></td>
</tr>
<tr class="odd">
<td><p>Scenario tests</p></td>
<td><p>These tests assess the behavior of a device or system, focusing on validating end-to-end experiences. These experiences can serve very specific purposes – such as lab readiness testing for a specific device stack, or may be broad end-user experiences that touches various hardware components in a system.</p></td>
</tr>
<tr class="even">
<td><p>Benchmark tests</p></td>
<td><p>AThese tests provide power and performance measurement.</p></td>
</tr>
</tbody>
</table>

 

## <span id="related_topics"></span>Related topics


[What's New in Windows Hardware Certification Kit](http://go.microsoft.com/fwlink/?LinkId=302048)

 

 







