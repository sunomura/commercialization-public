---
title: Named Pipe State
description: Named Pipe State
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8b564842-be06-429c-9a23-2a2ce1228580
---

# <span id="p_hlk_test.5e9fd15a-7ffa-4caf-94eb-af2541ef2ede"></span>Named Pipe State


This automated test validates the behavior of all named-pipe operations for each distinct state of a pipe instance.

The test evaluates the following states:

-   **NO\_INSTANCE.** The instance does not exist.

-   **SERVER\_ONLY.** The server side of the instance has been created.

-   **CONNECTED.** The client side has been created and connects to server.

-   **CLIENT\_DISCONNECTED.** The client disconnects by closing its handle.

-   **SERVER\_DISCONNECTED.** The server disconnects by using the **DisconnectNamedPipe** API.

The named-pipe operations that the test evaluates include the following:

-   **Server CreateNP.** Server calls **CreateNamedPipe**.

-   **Server ConnectNP.** Server calls **ConnectNamedPipe**.

-   **Server DisconnectNP.** Server calls **DisconnectNamedPipe**.

-   **Server CloseHandle.** Server calls **CloseHandle**.

-   **Client CreateFile.** Client calls **CreateFile**.

-   **Client WaitNP.** Client calls **WaitNamedPipe**.

-   **Client CallNP.** Client calls **CallNamedPipe**.

-   **Client CloseHandle.** Client calls **CloseHandle**.

-   **Server Write.** Server calls **WriteFile**.

-   **Server Read.** Server calls **ReadFile**.

-   **Client Write.** Client calls **WriteFile**.

-   **Client Read.** Client calls **ReadFile**.

The test selects each state in random order and calls each action in random order. If any action moves the pipe away from the current state, the test brings it back to the current state.

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
<li>Filter.Driver.FileSystem.NamedPipeAndMailSlots</li>
<li>Filter.Driver.AntiVirus.NamedPipeAndMailSlots</li>
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
<td>30</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Development</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>1800</td>
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

To run this test, follow these steps:

1.  Copy the test binaries that are listed in the **File List** section locally.

2.  Run the following command: **npstate.exe regress**

3.  The expected Pass count is 600. Inspect the log file for the presence of +SEV error tags. If you do not find any instances of this tag, the test has passed.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting File System Testing](troubleshooting-file-system-testing.md).

This test returns Pass or Fail. To review test details, review the test log from Windows Hardware Lab Kit (Windows HLK) Studio.

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Command_syntax"></span><span id="command_syntax"></span><span id="COMMAND_SYNTAX"></span>Command syntax

This test accepts a single parameter that indicates the server host name.

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
<td><p>Npstate.exe</p></td>
<td><p>[WTT\TestBinRoot]\NTTEST\BASETEST\kernel\misc\npstate.exe</p></td>
</tr>
<tr class="even">
<td><p>Ntlog.dll</p></td>
<td><p>[WTT\OsBinRoot]\ddk_flat\DTM\tests\ntlog\ntlog.dll</p></td>
</tr>
<tr class="odd">
<td><p>Ntlogger.ini</p></td>
<td><p>[WTT\OsBinRoot]\ddk_flat\DTM\tests\ntlog\ntlogger.ini</p></td>
</tr>
</tbody>
</table>

 

### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name         | Parameter description |
|------------------------|-----------------------|
| **LLU\_LclAdminUser**  | LLU for Execute       |
| **LLU\_NetAccessOnly** | LLU for Copy          |

 

 

 






