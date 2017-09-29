---
title: File IO 2 Tests
description: File IO 2 Tests
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 92a67bf2-8c99-48c0-91c5-cea9075dd332
---

# <span id="p_hlk_test.a1fb1fda-1fc1-41de-9626-bf88defeb746"></span>File IO 2 Tests


This automated test verifies basic file I/O on the driver stack.

You can use the test to verify the following information:

-   The context in which the test or variation ran (for example, x86, file system, local/remote, language, build number)

-   Pass, fail, and variation count numbers

-   If failed, information that can help determine the cause of failure

The File IO 2 tests are based on TAEF:

-   To list the tests, run the following:

    ``` syntax
    te FileIOTestA.dll /list
    ```

-   To run all tests with priority zero (the highest priority, which is the default priority in RunFileIo2.cmd) on a particular test volume, run the following:

    ``` syntax
    TE.exe FileIOTestA.dll /select:@Priority=0  /p:Volume=%DRIVE_LETTER%
    ```

For more information about the behavior of file systems, see [File System Behavior in the Microsoft Windows Environment](http://go.microsoft.com/fwlink/?LinkId=236047).

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
<li>Filter.Driver.FileSystem.MiniFilter</li>
<li>Filter.Driver.AntiVirus.MiniFilter</li>
<li>Filter.Driver.FileSystem.Functionality</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Platforms</strong></td>
<td><ul>
<li>Windows 10 Mobile ARM</li>
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
<td>300</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Development</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>18000</td>
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

-   [Filter.Driver additional documentation](filter-driver-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


For more information about requirements, see [File System Testing Prerequisites](file-system-testing-prerequisites.md).

In addition, this test requires extra hard drive space for four simple 2,048-megabyte (MB) partitions and two simple 1,024-MB partitions.

Before you run the test, you must add the following partitions to the test computer.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Label</th>
<th>File system</th>
<th>Size</th>
<th>Expected drive letter</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NTFS</p></td>
<td><p>NTFS</p></td>
<td><p>2,048 MB</p></td>
<td><p>g:</p></td>
</tr>
<tr class="even">
<td><p>CNTFS</p></td>
<td><p>NTFS (compressed)</p></td>
<td><p>2,048 MB</p></td>
<td><p>i:</p></td>
</tr>
<tr class="odd">
<td><p>FAT</p></td>
<td><p>FAT16</p></td>
<td><p>1,024 MB</p></td>
<td><p>k:</p></td>
</tr>
<tr class="even">
<td><p>FAT32</p></td>
<td><p>FAT32</p></td>
<td><p>1,024 MB</p></td>
<td><p>l:</p></td>
</tr>
<tr class="odd">
<td><p>ExFAT</p></td>
<td><p>ExFAT</p></td>
<td><p>2,048 MB</p></td>
<td><p>m:</p></td>
</tr>
<tr class="even">
<td><p>UDF</p></td>
<td><p>UDF</p></td>
<td><p>2,048 MB</p></td>
<td><p>n:</p></td>
</tr>
<tr class="odd">
<td><p>REFS</p></td>
<td><p>REFS</p></td>
<td><p>10240mb</p></td>
<td><p>o:</p></td>
</tr>
</tbody>
</table>

 

RunFileIO.cmd contains references to environment variables that you can change to allow for skipping of certain file systems.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For general troubleshooting information, see [Troubleshooting File System Testing](troubleshooting-file-system-testing.md).

This test returns Pass or Fail. To review test details, review the test log from Windows Hardware Lab Kit (Windows HLK) Studio.

The test uses Ntlog for logging the test results. Any failure is logged with the Win32® **GetLastError()** code.

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Command_syntax"></span><span id="command_syntax"></span><span id="COMMAND_SYNTAX"></span>Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Command option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>te FileIOTestA.dll /select:@Priority=0 /p:Volume=%DRIVE_LETTER%</strong></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

### <span id="File_list"></span><span id="file_list"></span><span id="FILE_LIST"></span>File list

| File                | Location                                                                                                       |
|---------------------|----------------------------------------------------------------------------------------------------------------|
| AttachFilter.cmd    | \[WTT\\TestBinRoot\]\\NTTest\\BASETEST\\Core\_File\_Services\\FilterManager\\TestSuite\\Scripts\\FileSystems\\ |
| IsREFSSupported.vbs | \[WTT\\TestBinRoot\]\\NTTest\\BASETEST\\Core\_File\_Services\\FilterManager\\TestSuite\\Scripts\\FileSystems\\ |
| FioChild.exe        | \[WTT\\TestBinRoot\]\\base\\fs\\test\\Shared\_Tests\\FileIO2\\                                                 |
| FioDetours.dll      | \[WTT\\TestBinRoot\]\\base\\fs\\test\\Shared\_Tests\\FileIO2\\                                                 |
| FileIOTestA.dll     | \[WTT\\TestBinRoot\]\\base\\fs\\test\\Shared\_Tests\\FileIO2\\                                                 |
| FileIOTestW.dll     | \[WTT\\TestBinRoot\]\\base\\fs\\test\\Shared\_Tests\\FileIO2\\                                                 |
| ReadAsync.exe       | \[WTT\\TestBinRoot\]\\base\\fs\\test\\Shared\_Tests\\FileIO2\\                                                 |
| WriteAsync.exe      | \[WTT\\TestBinRoot\]\\base\\fs\\test\\Shared\_Tests\\FileIO2\\                                                 |
| RunFileIo2.cmd      | \[WTT\\TestBinRoot\]\\base\\fs\\test\\Core\_File\_Services\\FilterManager\\TestSuite\\Scripts\\FileSystems\\   |
| WrapFileIO2.cmd     | \[WTT\\TestBinRoot\]\\base\\fs\\test\\Core\_File\_Services\\FilterManager\\TestSuite\\Scripts\\FileSystems\\   |

 

### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name           | Parameter description                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------|
| **NTFS\_DRIVE\_LETTER**  | The drive letter for the NTFS volume that the File IO 2 test will run on.                            |
| **CNTFS\_DRIVE\_LETTER** | The drive letter for the Compressed NTFS volume that the File IO 2 test will run on.                 |
| **FAT\_DRIVE\_LETTER**   | The drive letter for the FAT volume that the File IO 2 test will run on.                             |
| **FAT32\_DRIVE\_LETTER** | The drive letter for the FAT32 volume that the FileIO 2 test will run on.                            |
| **EXFAT\_DRIVE\_LETTER** | The drive letter for the ExFat volume that the File IO 2 test will run on.                           |
| **UDF\_DRIVE\_LETTER**   | The drive letter for the UDF volume that the File IO 2 test will run on.                             |
| **RUN\_MODE**            | Leave this on BVT.                                                                                   |
| **LLU\_LclAdminUser**    | LLU for execute                                                                                      |
| **LLU\_NetAccessOnly**   | LLU for copy                                                                                         |
| **REFS\_DRIVE\_LETTER**  | The drive letter for the ReFS volume that the test will run on. Enter NONE if not &gt;= Win8 Server. |

 

 

 






