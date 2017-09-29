---
title: Troubleshooting Device Fundamentals Reliability Testing by using the Windows HLK
description: Troubleshooting Device Fundamentals Reliability Testing by using the Windows HLK
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ba92e34f-2425-466c-82b0-ac0cf9ecc681
---

# Troubleshooting Device Fundamentals Reliability Testing by using the Windows HLK


This article describes how to troubleshoot problems that can occur during Windows Hardware Lab Kit (Windows HLK) Device Fundamentals Reliability testing. See [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

Troubleshooting Device Fundamentals Reliability tests consists of the following primary steps:

1.  [Check the device configuration](#prereq)

2.  [Identify the type of test failures](#types)

3.  [Triage test failures](#triage)

The following sections provide additional detailed and important information that you can use to troubleshoot failed Device Fundamentals Reliability tests:

-   [Collect and View Windows Device Testing Framework (WDTF) Traces](collect-and-view-windows-device-testing-framework--wdtf--traces.md)

-   [Review common Device Fundamentals Reliability test failures](review-common-device-fundamentals-reliability-test-failures.md)

-   [Review Log Files](review-log-files-troubleshooting-device-fundamentals-reliability-tests.md)

-   [Reproduce the test failure by running the test from the command line](reproduce-the-test-failure-by-running-the-test-from-the-command-line.md)

-   [Troubleshoot WLAN SimpleIO plugin failures that are logged by Device Fundamentals tests](troubleshoot-wlan-simpleio-plugin-failures-that-are--logged-by-device-fundamentals-tests.md)

-   [Use kernel debugging to debug Device Fundamentals Reliability test failures](use-kernel-debugging-to-debug-device-fundamentals-reliability-test-failures.md)

-   [How to get help](#help)

-   [Additional resources](#addlts)

## <span id="prereq"></span><span id="PREREQ"></span>Check the device configuration


Device Fundamentals Reliability tests require test devices to be properly configured to test I/O. Before you start to test, make sure that the test configuration adheres to the testing prerequisites that are described in [Device.Fundamentals Reliability Testing Prerequisites](devicefundamentals-reliability-testing-prerequisites.md). Failure to meet these prerequisites can result in test failures.

## <span id="types"></span><span id="TYPES"></span>Identify the type of test failures


See [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md#cat) in Troubleshooting Windows HLK Test Failures to identify specific types of test failures.

### <span id="Test_logs_a_failure"></span><span id="test_logs_a_failure"></span><span id="TEST_LOGS_A_FAILURE"></span>Test logs a failure

The most common way for Device Fundamentals Reliability tests to fail in Windows HLK is for the test to log a failure. If your failed test logged a failure, we recommend that you proceed to the [Triage test failures](#triage) section of this topic.

### <span id="Test_system_bug_checks"></span><span id="test_system_bug_checks"></span><span id="TEST_SYSTEM_BUG_CHECKS"></span>Test system bug checks

System bug checks are commonly seen during Device Fundamentals Reliability tests because of the nature of the tests (stress, reliability, concurrency, etc.).

When you investigate failures that are caused by system bug checks, we highly recommend that you re-run the tests by having the test system connected to a kernel debugger. Running the tests by using the debugger causes the system to break into the debugger when the system bug-checks.

-   See [Setting Up Kernel-Mode Debugging Manually](http://go.microsoft.com/fwlink/?LinkID=299467) for information on how to setup a kernel debugger.

-   See [Use kernel debugging to debug Device Fundamentals Reliability test failures](use-kernel-debugging-to-debug-device-fundamentals-reliability-test-failures.md) for more information.

-   See [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md#sysx) in Troubleshooting Windows HLK Test Failures for general guidance on how to troubleshoot system bug checks during Windows HLK test runs.

### <span id="Test_hangs"></span><span id="test_hangs"></span><span id="TEST_HANGS"></span>Test hangs

Test hangs frequently occur during Device Fundamentals Reliability tests. Test hangs are typically seen when I/O request packets (IRPs) (typically, I/O and PNP IRPs) become stuck in drivers and prevent the tests from progressing.

>[!NOTE]
>  
Windows HLK will eventually cancel and fail a hung test so that the next scheduled test can proceed.

 

If a test hangs, we highly recommended that you re-run the tests by having the test system connected to a kernel debugger. This allows you to break into the debugger at the time when the test hangs, and to inspect stack traces of the test process (Device Fundamentals Reliability tests typically run as **te.processhost.exe** or **te.exe**).

-   See [Setting Up Kernel-Mode Debugging Manually](http://go.microsoft.com/fwlink/?LinkID=299467) for information on how to setup a kernel debugger.

-   See [Use kernel debugging to debug Device Fundamentals Reliability test failures](use-kernel-debugging-to-debug-device-fundamentals-reliability-test-failures.md) for more information.

-   See [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md#toolong) in Troubleshooting Windows HLK Test Failures for general guidance on how to troubleshoot test hangs during Windows HLK test runs.

## <span id="triage"></span><span id="TRIAGE"></span>Triage test failures


**Review test documentation**

Device Fundamentals Reliability tests generally test common user scenarios such as Sleep with I/O, PNP with I/O, Reboot with I/O, etc. We recommend that you completely understand the scenario under test for the failing test(s) by reviewing the appropriate test documentation at [Device.DevFund Tests](device-devfund-tests.md).

**Thoroughly review test logs**

You should thoroughly review log entries that precede the actual error message, to gain a clear understanding of the current test scenario and the previous test scenarios that ran. Sometimes previous test scenarios that ran (even if they passed) affect the next test scenario. For example, I/O failures can occur after a device is disabled and enabled. For more information about reviewing test logs, see [Review Log Files](review-log-files-troubleshooting-device-fundamentals-reliability-tests.md)

**Review additional log files that are copied back**

Device Fundamentals Reliability tests often copy back additional files that are useful for triaging test failures. For example, Reinstall and PNP tests copy back [SetupAPI](http://go.microsoft.com/fwlink/?LinkID=299472) logs from the test system. You should open and review all files under **Additional Files** on the **Results** tab in Windows HLK Studio. Right-click the test result and then select **Additional Files**.

**Collect and view WDTF traces**

It can be useful to collect and view WDTF traces when you troubleshoot certain test failures. See [Collect and View Windows Device Testing Framework (WDTF) Traces](collect-and-view-windows-device-testing-framework--wdtf--traces.md) for information about how to collect and view WDTF traces.

## <span id="help"></span><span id="HELP"></span>How to get help


Device Fundamentals Reliability test owners at Microsoft regularly review and respond to questions posted about Device Fundamentals Test failures at the [Windows Hardware Testing and Certification Forum](http://go.microsoft.com/fwlink/?LinkID=299688). We recommend that you use this forum to get needed support.

See [Windows HLK Support](..\user\windows-hlk-support.md) for information about how to open a support case for investigating test failures.

## <span id="addlts"></span><span id="ADDLTS"></span>Additional resources


The following table lists additional resources that can help you resolve problems you can encounter during device fundamentals testing.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Resource</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Troubleshooting the Windows HLK Environment](..\user\troubleshooting-the-windows-hlk-environment.md)</p></td>
<td><p>General triage and troubleshooting assistance for Windows HLK infrastructure failures.</p></td>
</tr>
<tr class="even">
<td><p>[Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md)</p></td>
<td><p>General triage and troubleshooting guidance to investigate test failures.</p></td>
</tr>
<tr class="odd">
<td><p>[Triaging WDTF-based tests](http://go.microsoft.com/fwlink/?LinkID=299602)</p></td>
<td><p>General guidance for troubleshooting failures that are logged by WDTF-based tests.</p></td>
</tr>
<tr class="even">
<td><p>[How to select and configure the Device Fundamentals tests](http://go.microsoft.com/fwlink/?LinkID=299603)</p></td>
<td><p>Device Fundamentals Reliability tests also ship in the [Windows Driver Kit (WDK)](http://go.microsoft.com/fwlink/?LinkID=256421). Driver developers might prefer to use WDK and Microsoft Visual Studio to run the failing tests to investigate test failures. This page describes how to run the tests by using the WDK.</p></td>
</tr>
<tr class="odd">
<td><p><strong>%ProgramFiles%\Windows Kits\8.1\Testing\Tests\Additional Tests\DeviceFundamentals.</strong>).</p></td>
<td><p>A subset of Device Fundamentals Reliability tests are written by using VBScript. You can open these script files by using Notepad. The scripts are located in the specified folder after you install the WDK.</p></td>
</tr>
<tr class="even">
<td><p>[Troubleshooting the Device Fundamentals tests using the WDK](http://go.microsoft.com/fwlink/?LinkID=313672)</p></td>
<td><p>Provides suggestions for fixing problems that you might encounter when you use the WDK to run the Device Fundamentals Tests.</p></td>
</tr>
</tbody>
</table>

 

## <span id="related_topics"></span>Related topics


[Device.DevFund Tests](device-devfund-tests.md)

 

 







