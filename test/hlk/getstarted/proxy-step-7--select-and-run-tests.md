---
title: Step 7 Select and run tests
description: Step 7 Select and run tests
MS-HAID:
- 'p\_sxs\_hlk.step\_4\_\_running\_tests'
- 'p\_sxs\_hlk.proxy\_step\_7\_\_running\_tests'
- 'p\_sxs\_hlk.proxy\_step\_7\_\_select\_and\_run\_tests'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
Search.SourceType: Video
ms.assetid: 2088B4A0-F83A-4BB0-AD81-AE5E398BF24D
---

# Step 7: Select and run tests


The **Tests** tab displays all of the tests that are associated with the features found on your device. You can filter and sort the listed tests in the following ways:

-   Test Phase Categorization
    -   Bring Up
    -   Development and Integration
    -   Reliability
    -   Tuning and Validation
    -   Manufacturing
    -   Support

        >[!NOTE]
        >  In the HLK, test categories replace the level classifications previously used with the HCK. The HLK can be used throughout the product life cycle to test and measure quality at each stage of development.

         
-   Status
-   Test Name
-   Type (manual, non-distributed, special configuration, multiple machine)

    >[!NOTE]
    >  You can hover over the test type icons with your mouse for more information about the test types.

     

-   Length
-   Target
-   Machine(s)

>[!NOTE]
>  Manual tests that require user input can interrupt the test process. We recommend that you run manual tests separately from automated tests.

>[!NOTE]
>  Some tests require additional input before running. Windows HLK Studio prompts you for more info as needed.

 

The following image shows the Studio **Tests** tab.

![hlk studio tests tab](images/hlk-studio-tests-tab.png)

## <span id="Playlists"></span><span id="playlists"></span><span id="PLAYLISTS"></span>Playlists


Playlists are collections of tests that you can use to define various scenarios in which to test your device. The Windows Hardware Compatibility Program uses an official playlist to determine which devices meet the requirements for compatibility with Windows 10.

<iframe src="https://hubs-video.ssl.catalog.video.msn.com/embed/afc1a262-6147-448f-910c-dbb1bcb18d07/IA?csid=ux-en-us&MsnPlayerLeadsWith=html&PlaybackMode=Inline&MsnPlayerDisplayShareBar=false&MsnPlayerDisplayInfoButton=false&iframe=true&QualityOverride=HD" width="720" height="405" allowFullScreen="true" frameBorder="0" scrolling="no">Windows Hardware Lab Kit playlists</iframe>

You can load a playlist by choosing **Load Playlist** from within the **Tests** tab. You can load only one playlist at a time. To choose a different playlist, you must first unload the current playlist by choosing **Unload Playlist** from the **Tests** tab.

The following image shows the **Load Playlist File** dialog.

![load playlist dialog](images/hlk-studio-load-playlist-file-dialog.png)

Once a playlist is loaded, only tests that are applicable to each target are shown in the UI.

Test results against all playlists for a specific target are kept until the target is removed from the project. When a playlist is loaded, any previous test results against that playlist are also loaded.

You can save an existing collection of tests as a playlist by choosing **Save Selected As Playlist**.

## <span id="Running_a_test"></span><span id="running_a_test"></span><span id="RUNNING_A_TEST"></span>Running a test

>[!NOTE]
>  If you want to re-flash the device before running the test, set the ForceReflash\_KitsTemplate parameter in HLK Studio to 1 and specifying the location of the ffu to flash to the device using the ImagePath\_KitsTemplate parameter.

>[!NOTE]
>  If using a playlist, be sure to load it before following these steps.

 

1.  Filter the test results by using the **View By** dropdown list.

2.  Check the box next to each test that you want to run.

3.  Run the selected tests by choosing **Run Selected**.

    If any additional input is needed, Windows HLK Studio will prompt you.

    A progress bar appears. A slight delay occurs when you run a test.

>[!NOTE]
>  To learn more about any test, select the test from the list and press **F1** key or right-click and select **Test Description**. To cancel any running test, right-click it and select **Cancel**.

 

As tests complete, the results are displayed in the **Status** column. A green checkmark means that it passed, while a red X means that it failed. The pane on the right displays project summary information, including target(s) selected, operating systems being tested, product types you qualify for, and status of all tests.

To learn more about the different options on this page, see [HLK Studio - Tests Tab](..\user\hlk-studio---tests-tab.md).

 

 






