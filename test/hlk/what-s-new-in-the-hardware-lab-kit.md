---
title: What's new in the Hardware Lab Kit
description: What's new in the Hardware Lab Kit
MS-HAID:
- 'p\_hlk.what\_s\_new\_in\_the\_hardware\_lab\_kit'
- 'wdknodes.what\_s\_new\_in\_the\_hardware\_lab\_kit'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
Search.SourceType: Video
ms.assetid: 8A9F73C6-030F-4A1D-A466-6A9ADDD06A51
---

# What's new in the Hardware Lab Kit


## <span id="What_s_new_in_this_release"></span><span id="what_s_new_in_this_release"></span><span id="WHAT_S_NEW_IN_THIS_RELEASE"></span>**What's new in this release**


### <span id="Breaking_changes"></span><span id="breaking_changes"></span><span id="BREAKING_CHANGES"></span>Breaking changes

>[!NOTE] 
>With each new release, anyone who builds tools that utilize the HLK object model should rebuild those tools to use the latest versions of the object model files. In addition, be sure to always use the same version of each object model file (i.e. do not mix object model files from different kit releases).

 

### <span id="Improved_playlist_support"></span><span id="improved_playlist_support"></span><span id="IMPROVED_PLAYLIST_SUPPORT"></span>Improved playlist support

The process for loading and using playlists has been improved and simplified. For more information, see [Step 6: Select and run tests](getstarted\step-6-select-and-run-tests.md) in the Getting Started guide

### <span id="Support_for_ARM64_desktop"></span><span id="support_for_arm64_desktop"></span><span id="SUPPORT_FOR_ARM64_DESKTOP"></span>Support for ARM64 desktop

HLK tests can now target ARM64 desktop machines.

### <span id="Nano_Server_testing"></span><span id="nano_server_testing"></span><span id="NANO_SERVER_TESTING"></span>Nano Server testing

HLK now includes tests for Nano Server.

## <span id="What_s_new_in_previous_releases"></span><span id="what_s_new_in_previous_releases"></span><span id="WHAT_S_NEW_IN_PREVIOUS_RELEASES"></span>**What's new in previous releases**


### <span id="Improved_diagnosability_of_failed_HLK_tests"></span><span id="improved_diagnosability_of_failed_hlk_tests"></span><span id="IMPROVED_DIAGNOSABILITY_OF_FAILED_HLK_TESTS"></span>Improved diagnosability of failed HLK tests

The Results tab now indicates when a test fails due to a system crash. The tab also shows information from the associated Bug Check along with a link to help documentation for further information.

See the following topics for more information:

-   [Step 7: View test results and log files (Getting started guide)](getstarted\step-7-view-test-results-and-log-files.md)
-   [HLK Studio - Results Tab](user\hlk-studio---results-tab.md)
-   [Troubleshooting Windows HLK Test Failures (system crashes)](user\troubleshooting-windows-hlk-test-failures.md#sysx)

### <span id="Exporting_failed_HLK_jobs"></span><span id="exporting_failed_hlk_jobs"></span><span id="EXPORTING_FAILED_HLK_JOBS"></span>Exporting failed HLK jobs

You can now export a failed job and re-run it on a machine that does not have the HLK Client installed. For more information, see [Exporting a Failed HLK Job](user\exporting-a-failed-hlk-job.md).

### <span id="Support_for_Mobile_testing"></span><span id="support_for_mobile_testing"></span><span id="SUPPORT_FOR_MOBILE_TESTING"></span>Support for Mobile testing

Mobile devices running Test and Health images are now supported for testing with the HLK. For more information, see [HLK Proxy Client Getting Started Guide](getstarted\hlk-proxy-client-getting-started-guide.md).

### <span id="SQL_Server_2012_Express_SP2"></span><span id="sql_server_2012_express_sp2"></span><span id="SQL_SERVER_2012_EXPRESS_SP2"></span>SQL Server 2012 Express SP2

The HLK setup process now installs SQL Server 2012 Express SP2 if no other SQL installation is present on the controller at the time of installation.

### <span id="Scenario_Testing"></span><span id="scenario_testing"></span><span id="SCENARIO_TESTING"></span>Scenario Testing

Test levels have been replaced by Development Phases to better align with the hardware and system development cycle. Tests are organized by their applicability during Bring Up, Development and Integration, Reliability, and Tuning and Validation.

### <span id="Playlists"></span><span id="playlists"></span><span id="PLAYLISTS"></span>Playlists

Playlists describe a collection of tests and can be created from the HLK Studio and [Object Model](API\microsoftwindowskitshardwareobjectmodel.md) to define custom test passes.


<iframe src="https://hubs-video.ssl.catalog.video.msn.com/embed/afc1a262-6147-448f-910c-dbb1bcb18d07/IA?csid=ux-en-us&MsnPlayerLeadsWith=html&PlaybackMode=Inline&MsnPlayerDisplayShareBar=false&MsnPlayerDisplayInfoButton=false&iframe=true&QualityOverride=HD" width="720" height="405" allowFullScreen="true" frameBorder="0" scrolling="no">Windows Hardware Lab Kit playlists</iframe>


Learn more about playlists in the [Getting Started Guide](getstarted\step-6-select-and-run-tests.md).

### <span id="Windows_Hardware_Compatibility_Program"></span><span id="windows_hardware_compatibility_program"></span><span id="WINDOWS_HARDWARE_COMPATIBILITY_PROGRAM"></span>Windows Hardware Compatibility Program

Hardware certification is no longer required. Instead, the Windows Hardware Compatibility Program is an optional program in which you can participate. For more information, see [Windows Hardware Compatibility Program](\user\windows_hardware_compatibility_program_overview).

-   Compatibility Playlist - Levels are no longer used to identify tests required for the Compatibility Program. To create a Compatibility Program test pass, download the official [Hardware Compatibility Program Playlist](https://sysdev.microsoft.com/en-US/Hardware/compatibilityplaylists/) and apply to your HLK project.
-   [Windows Hardware Certification blog](http://blogs.msdn.com/b/windows_hardware_certification) –This blog provides up-to-date news about the Windows Compatibility Program. Including Compatibility Playlist update announcements.

### <span id="OS_Support"></span><span id="os_support"></span><span id="OS_SUPPORT"></span>OS Support

The Hardware Lab Kit supports Windows 10 testing only. Use the Hardware Certification Kit for testing downlevel operating systems.

### <span id="Merge_.hckx_Packages"></span><span id="merge_.hckx_packages"></span><span id="MERGE_.HCKX_PACKAGES"></span>Merge .hckx Packages

To support unified driver submissions, results from HCK and HLK projects can be merged together using HLK Studio. When merging, open the HLK project or package first, and then merge in the HCK package(s).

### <span id="Virtual_machine_support"></span><span id="virtual_machine_support"></span><span id="VIRTUAL_MACHINE_SUPPORT"></span>Virtual machine support

The HLK Controller now supports installation and execution in a virtual machine. When configuring your virtual machines, ensure the virtual machine meets the [minimum requirements](getstarted\windows-hlk-prerequisites.md) for the HLK Controller.

### <span id="Partial_packaging"></span><span id="partial_packaging"></span><span id="PARTIAL_PACKAGING"></span>Partial packaging

You can now package a subset of test results within an HLK project, tailoring the packaging experience to key scenarios. This allows you to capture, share, and diagnose test failures without having to run tests individually in a new project.

To use this feature, select one or more tests from the **Test** tab, right-click the selection, and choose **Create Partial Package of Highlighted Tests**. Note that this package will be saved as a partial package (.hlkp). This extension will be deprecated in future HLK releases.

### <span id="Rate_this_Test"></span><span id="rate_this_test"></span><span id="RATE_THIS_TEST"></span>Rate this Test

You can now provide feedback on tests in the HLK. To rate tests, you must opt-in to CEIP. To rate a test, right-click on the desired test in the Results Pane, and select Rate This Test.

### <span id="Preview_pane"></span><span id="preview_pane"></span><span id="PREVIEW_PANE"></span>Preview pane

The **Preview pane** in File Explorer provides project and package information including Name, Creation Date, Targets, and Type.

To use the Preview pane in File Explorer, choose the **View** menu group, and then choose **Preview pane**. You can then choose any .hlkx file to view details of the package.

### <span id="Server_support"></span><span id="server_support"></span><span id="SERVER_SUPPORT"></span>Server support

The HLK Controller can now be installed on Windows Server 2012 R2.

### <span id="64-bit_SQL"></span><span id="64-bit_sql"></span><span id="64-BIT_SQL"></span>64-bit SQL

The HLK now supports 64-bit SQL editions exclusively. Previously, the HCK supported only 32-bit SQL editions exclusively.

 

 






