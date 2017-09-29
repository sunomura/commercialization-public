---
title: HMFT Testing Prerequisites
description: HMFT Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b4a88365-9960-4f12-a70f-27c63d946b86
---

# HMFT Testing Prerequisites


This section describes the tasks that you must complete before you test a Hardware Media Foundation Transform (HMFT)–compliant device by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware requirements](#bkmk-hck-hmft-hr)

-   [Software requirements](#bkmk-hck-hmft-sr)

-   [Test computer configuration](#bkmk-hck-hmft-tc)

An HMFT-compliant device is a video card or chipset that supports hardware-based encoding or decoding of digital content.

>[!NOTE]
>  
If the video card is a not a stand-alone product (for example, a video chipset on a system board), these tests run as part of system certification.

 

## <span id="BKMK_HCK_HMFT_hR"></span><span id="bkmk-hck-hmft-hr"></span><span id="BKMK_HCK_HMFT_HR"></span>Hardware requirements


The following hardware is required for testing an HMFT-compliant device:

-   A test computer.

    >[!NOTE]
    >  
    The test computer must meet the [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md). It also must have at least 75 GB free on the drive used as the HLK working directory.

     

-   An HMFT-compliant video card (the test device), unless the HMFT feature is included in a video chipset on the system board.

You might need additional hardware if the test device includes audio, networking, or other features. To determine whether additional hardware requirements apply, see the description for each test that's identified for your video card or chipset in Windows HLK Studio.

## <span id="BKMK_HCK_HMFT_sR"></span><span id="bkmk-hck-hmft-sr"></span><span id="BKMK_HCK_HMFT_SR"></span>Software requirements


The following software is required for testing an HMFT-compliant device:

-   The latest Windows HLK filters or updates.

-   Standard video files that are used during decoding or encoding tests.

    >[!NOTE]
    >  
    During installation of the Windows HLK, standard video files are downloaded to Windows HLK Studio.

     

Before running the HMFT encoding and decoding tests, you must download the [Windows Hardware Lab Kit (HLK) Supplemental Test Content for HMFT Multimedia Tests](http://msdn.microsoft.com/en-us/windows/hardware/hh852358) from the Windows Dev Center. After downloading the supplemental test content, you must store this content in one of the following ways:

-   On the HLK controller, under the path %DTMBIN%..\\Tests\\HMFTContent, the default value for the ContentSource parameter must be used when scheduling the tests. This causes each test to copy over the input content that it requires only for that single test, and then delete the content after the test has completed. This is useful for computers with less than 75GB free space available.

-   In a different location than %DTMBIN%..\\Tests\\HMFTContent or on a network share accessible to the client computers. You must configure the ContentSource parameter to the location you copied the files to when scheduling the tests. This has the same behavior as the first item in this list, but allows you to specify where the content is located.

-   Copy the content locally on each client computer before running the tests. You must configure the ContentSource parameter to be the path to the content on the client computer. For example, if you use an external drive with letter d: and place the content in d:\\HMFTContent, the ContentSource parameter must be configured to d:\\HMFTContent. This will cause the test to use the local content and not copy each file for each test. This option requires at least 75 GB of free space on the client computers but will speed up the test run because the content will not have to be copied for each test.

    >[!NOTE]
    >  
    The ContentSource parameter is passed to all client computers that the tests are scheduled against so ensure that content location is identical on all client computers.

     

-   Copy the content locally on each client computer before running the tests and add the content location to the %PATH% environment variable. Leave the default value for the ContentSource parameter. This will cause the tests to behave similarly to the third item in this list. This option does not require that the content is in the same location on every client computer.

## <span id="BKMK_HCK_HMFT_tC"></span><span id="bkmk-hck-hmft-tc"></span><span id="BKMK_HCK_HMFT_TC"></span>Test computer configuration


To configure the test computer for testing a HMFT-compliant device:

1.  Install the appropriate Windows operating system on the test computer, and then configure the computer for your test network (the network that contains Windows HLK Studio and Windows HLK Controller).

    >[!NOTE]
    >  
    If you are testing on Windows Server 2008 R2, Windows Server 2012, or Windows Server 2012 R2, you must install the Desktop Experience package. From a command prompt, type:

    **Dism.exe /online /enable-feature /featurename:DesktopExperience /all**

    If the computer does not restart, you must restart it manually.

     

2.  Install the manufacturer-supplied device driver, if necessary, on the test computer.

3.  For a stand-alone video card, install the card in the test computer.

4.  Install the Windows HLK client application on the test computer.

5.  By using Windows HLK Studio, create a computer pool and move the test computer to that pool.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it's run, a dialog box is displayed for that test. Review the specific test topic for more information.

Manual Windows HLK tests require user intervention. When running tests for a submission, it's best to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of automated tests.

 

 






