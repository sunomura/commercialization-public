---
title: Proximity Controller Testing Prerequisites
description: Proximity Controller Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b217c9c8-5fb9-494c-96dd-e1f8a872dada
---

# Proximity Controller Testing Prerequisites


This topic describes the tasks that you must complete before you test a proximity-compliant controller by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware Requirements](#bkmk-hardwarerequirements).

-   [Software Requirements](#bkmk-softwarerequirements).

-   [Test Computer Configuration](#bkmk-testcomputerconfiguration).

## <span id="BKMK_HardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware Requirements


The following hardware is required for testing a proximity-compliant controller. You might need more hardware if the controller includes more capabilities. See the test description for each test that the Windows HLK identifies to determine whether your controller requires more hardware.

-   Two test computers. These test computers must meet the Windows HLK prerequisites and must be included in the same machine pool. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md).

-   Two test proximity controllers.

-   One Near Field Communication (NFC) Forum Type 2 tag.

>[!NOTE]
>  
For more information about the NFC Forum Type 2 tag, see [Near Field Communication (NFC) Forum](http://go.microsoft.com/fwlink/?LinkID=236991).

 

## <span id="BKMK_SoftwareRequirements"></span><span id="bkmk-softwarerequirements"></span><span id="BKMK_SOFTWAREREQUIREMENTS"></span>Software Requirements


The following software is required to run the proximity tests:

-   The drivers for the test device.

-   The latest Windows HLK filters or updates.

## <span id="BKMK_TestComputerConfiguration"></span><span id="bkmk-testcomputerconfiguration"></span><span id="BKMK_TESTCOMPUTERCONFIGURATION"></span>Test Computer Configuration


For proximity controller tests, you must have two test computers in your machine pool so that you can test communication between the proximity controller and another proximity-compliant device. The primary test computer is Computer A. This test computer runs the proximity tests and generates test results. The second test computer is Computer B. This computer is required to test the sending and receiving of subscription messages.

To configure both test computers, follow these steps:

1.  Install the appropriate Windows® operating system on the test computers, and then configure the computers for your test network. The test network is the network that contains the Windows HLK Studio and Windows HLK Controller.

2.  Install the manufacturer-supplied device driver for the proximity controller on Computer A.

3.  Attach a proximity device (for example, a proximity-compliant mouse) to Computer B.

4.  Install the manufacturer-supplied device driver for the proximity device on Computer B.

5.  Verify that the proximity controller and the proximity-compliant device are enabled on Computer A and Computer B by reviewing their status in Device Manager.

6.  Install the Windows HLK client application on both test computers.

7.  Use Windows HLK Studio to create a machine pool, and then move the test computers to that pool.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set, a dialog box appears for that test. Review the specific test topic for more information about the parameters.

Manual Windows HLK tests require user intervention. When you run tests for a submission, it’s best to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting an automated test.

>[!IMPORTANT]
>  
On both Computer A and Computer B, switch to the Windows Desktop before you run your proximity tests.

 

 

 






