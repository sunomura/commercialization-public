---
title: NVMe Deallocate Performance Test (LOGO)
description: NVMe Deallocate Performance Test (LOGO)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9fbf580f-4515-46ec-905f-b785d774fd87
---

# <span id="p_hlk_test.e3d5d17a-a0af-4ef2-9d8f-7c30ecea6e1a"></span>NVMe Deallocate Performance Test (LOGO)


This test evaluates the performance of the Deallocate command for Non-Volatile Memory Express (NVMe) controller drives.

## <span id="Test_details"></span><span id="test_details"></span><span id="TEST_DETAILS"></span>Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Specifications</strong></td>
<td><ul>
<li>Device.Storage.ControllerDrive.NVMe.BasicFunction</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
<li>Windows 10 for desktop editions (Home, Pro, Enterprise, and Education) x86</li>
<li>Windows 10 for desktop editions x64</li>
<li>Windows Server 2016 x64</li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>Supported Releases</strong></td>
<td><ul>
<li>Windows 10</li>
<li>Windows 10, version 1511</li>
<li>Windows 10, version 1607</li>
<li>Windows 10, version 1703</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Expected run time (in minutes)</strong></td>
<td>2</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Benchmark</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>120</td>
</tr>
<tr class="odd">
<td><strong>Requires reboot</strong></td>
<td>false</td>
</tr>
<tr class="even">
<td><strong>Requires special configuration</strong></td>
<td>false</td>
</tr>
<tr class="odd">
<td><strong>Type</strong></td>
<td>automatic</td>
</tr>
</tbody>
</table>

 

## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Storage additional documentation](device-storage-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Hard Disk Drive Testing Prerequisites](hard-disk-drive-testing-prerequisites.md).

The test requires that an NVMe controller drive is connected. The drive must also satisfy the following requirements:

-   The drive should be a non-boot drive. The test is destructive. It will prepare the disk with correct partition and formatting for the testing.

-   The drive must support Deallocate (Trim/Unmap/Discard) command. The test will send down Deallocate commands using DATA SET MANAGEMENT Trim command.

-   Ensure that there is a separate drive available to be used as a logger drive. The test will automatically pick the logging drive. It is important to minimize the amount of activity occurring on the drive outside of the logo test. Since this is a performance test, outside activity may affect the results.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For more troubleshooting information, see [Troubleshooting Device.Storage Testing](troubleshooting-devicestorage-testing.md).

-   Check WTT Trace

    -   View **Task Log** of **Run Trim Performance Test**.

    -   Open the log file **TrimPerf.wtl**.

    -   Check for messages that may solve the issue.

    -   Copy the .wtl log file. This is the WTT trace described in the WTT Trace section.

-   Check launched command results

    -   Browse Job Logs of Trim Performance Test (LOGO).

    -   Open the LaunchCommand.result.

    -   If the error is related to launching a process, determine why logman or tracerpt failed.

-   No metrics found

    -   The test depends on Storport ETW tracing being enabled in order to get the command completion metrics. See the ETW Trace section for more information about enabling this tracing.

    -   Ensure no other Storport ETW traces are currently logging. Only one Storport ETW trace can be active at a time.

-   If you get the error message “The test drive does not support trim”, try the following:

    -   Check the NVMe drive to make sure the VPD B2h page’s LBPU bit is set to one.

    -   Try to send a Deallocate command via DATA SET MANAGEMENT’s Trim command.

    -   Run the test again.

-   If the test failed because the read and write maximum latency exceeded 500 milliseconds, try the following:

    -   Check the IO latency without Deallocate. Try to lower the latency below 500 milliseconds.

    -   Check the IO latency with presence of Deallocate. Try to lower the latency below 500 milliseconds.

-   If you want to debug the failure by running particular test cases, you may try the following command line options:

    -   Display all the test cases with numbers: **TrimPerf.exe /DriveNumber \[StorageDriveNumber\] /LogDriveLetter \[LoggerDriveLetter\]: /DeviceType NVMe /Scenario Performance /PrintTestCaseName**

    -   Run particular test case by test case number: **TrimPerf.exe /DriveNumber \[StorageDriveNumber\] /LogDriveLetter \[LoggerDriveLetter\]: /DeviceType NVMe /Scenario Performance /Precondition F /TestCase \[TestCaseNumber\]**

-   If you want to debug the failure by running particular pure Trim scenario, you may try the following command line options:

    -   The binary has unit test options: **TrimPerf.exe /DriveNumber \[StorageDriveNumber\] /LogDriveLetter \[LoggerDriveLetter\]: /DeviceType NVMe /Scenario Performance /Precondition F /UnitTest T /RangeCount \[NumberOfRangesPerDeallocateCommand\] /SizeCount \[SizeOfEachRange\] /SizeUnit \[Slab | Sector\] /TrimCount \[NumberOfTrims\]**

    -   **/RangeCount**: The number of ranges per deallocate command

    -   **/SizeCount**: The size of each range in /SizeUnit

    -   **/SizeUnit**: The granularity of /SizeCount, options are Slab (optimal unmap granularity) and Sector (LBA).

    -   **/TrimCount**: The number of deallocate commands sent in the test case.

-   If you want to debug the failure faster, try disable the preconditioning (fill up the drive to 90% full, takes long time) by adding /Precondition F parameter as follows:

    -   **TrimPerf.exe /DriveNumber \[StorageDriveNumber\] /LogDriveLetter \[LoggerDriveLetter\]: /DeviceType NVMe /Scenario Performance /DiskSize 0 /Cooldown 2 /Precondition F**

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


The test does the following:

**Deallocate command**

-   All deallocate commands should be completed in less than 500 milliseconds.

**IO commands (withy deallocate sending at same time at different regions)**

-   All read and write commands complete in less than 500 milliseconds.

-   98.5% of I/O commands complete in less than 100 milliseconds.

### <span id="Command_syntax"></span><span id="command_syntax"></span><span id="COMMAND_SYNTAX"></span>Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Command</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>TrimPerf.exe /DriveNumber [StorageDriveNumber] /LogDriveLetter [LogDriveLetter]: /DeviceType [DeviceType] /Scenario [Scenario] /DiskSize [DiskSize] /Cooldown [Cooldown]</strong></p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Runs the test.</p></td>
<td></td>
</tr>
</tbody>
</table>

>[!NOTE]
>  
For command-line help for this test binary, type **/h**.

 

### <span id="File_list"></span><span id="file_list"></span><span id="FILE_LIST"></span>File list

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TrimPerf.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\driverstest\storage\wdk\</p></td>
</tr>
<tr class="even">
<td><p>Etwprocessor.dll</p></td>
<td><p><em>&lt;[taefbinroot]&gt;</em>\</p></td>
</tr>
<tr class="odd">
<td><p>Wex.common.dll</p></td>
<td><p><em>&lt;[taefbinroot]&gt;</em>\</p></td>
</tr>
<tr class="even">
<td><p>Wex.communication.dll</p></td>
<td><p><em>&lt;[taefbinroot]&gt;</em>\</p></td>
</tr>
</tbody>
</table>

 

### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name         | Parameter description                      |
|------------------------|--------------------------------------------|
| **WDKDeviceID**        | Instance path of device to test.           |
| **LLU\_NetAccessOnly** | User account for accessing test fileshare. |
| **LLU\_LclAdminUsr**   | User account for running the test.         |
| **Destructive**        | (0,1) 0=Passive, 1=Destructive             |
| **StorageDriveNumber** | Storage drive number                       |

 

 

 






