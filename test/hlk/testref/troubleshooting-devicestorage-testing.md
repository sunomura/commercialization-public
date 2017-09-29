---
title: Troubleshooting Device.Storage Testing
description: Troubleshooting Device.Storage Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7b46b9ac-9da2-4422-87c6-98b7d04c1226
---

# Troubleshooting Device.Storage Testing


To troubleshoot issues that occur with Device.Storage tests, follow these steps:

1.  Review [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

2.  Review one of these Windows Hardware Lab Kit (Windows HLK) topics, depending on the type of storage device or configuration:

    -   [Hard Disk Drive Testing Prerequisites](hard-disk-drive-testing-prerequisites.md)

    -   [Hardware-based Raid Systems (Fibre Channel, SAS, SCSI, Serial ATA) Testing Prerequisites](hardware-based-raid-systems--fibre-channel-sas-scsi-serial-ata--testing-prerequisites.md)

    -   [Optical Disk Drive Testing Prerequisites](optical-disk-drive-testing-prerequisites.md)

    -   [Removable Storage Testing Prerequisites](removable-storage-testing-prerequisites.md)

    -   [Secure Digital Host Controller Storage Testing Prerequisites](secure-digital-host-controller-storage-testing-prerequisites.md)

    -   [Storage Adapter or Controller Testing Overview](storage-adapter-or-controller-testing-overview.md)

3.  Review the [Windows HLK release notes](http://go.microsoft.com/fwlink/p/?LinkID=236110) for current test issues.

4.  For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

5.  If you observe any failures while running the tests in the Windows HLK, look at the test logs that were generated. For example, for the Enumeration Test, the most relevant log is enumeratedrive.log.wtl. To view this log, go to the **Results** tab in the HLK studio and expand **Enumeration Test** &gt; **Test Run Date and Time** &gt; **Run Test** &gt; **Logs** &gt; **enumeratedrive.log.wtl**.

6.  To debug more, rerun the test manually from the Command Prompt (cmd), while setting the verbosity level to 4. This allows the test to log more information, such as data buffer, CDB information, and sense code. Documentation for each test contains details about the binary that is related to a particular test along with the binary location.

## <span id="Optical_Storage_Device"></span><span id="optical_storage_device"></span><span id="OPTICAL_STORAGE_DEVICE"></span>Optical Storage Device


These are common issues with optical disk drive tests:

-   Some controllers that use Serial Advanced Technology Attachment (SATA) Advanced Host Controller Interface (AHCI) mode might cause the CDBs to time out. This time-out occurs most frequently in the Start Stop Unit test, where the CDB after test unit ready times out without any sense code being returned. To resolve the issue, try a different controller or configuration.

-   Some drives intermittently can't delete data from a disk. This issue might be caused by rewritable media that has been used too many times. Try to use new rewritable media.

For more information about how to troubleshoot a test, see the troubleshooting section of a specific test in [Device.Storage Tests](device-storage-tests.md).

## <span id="Hybrid_Information_Device"></span><span id="hybrid_information_device"></span><span id="HYBRID_INFORMATION_DEVICE"></span>Hybrid Information Device


There are special steps that can be taken to reproduce a particular test case in a test, or if necessary, conduct a manual investigation of the device.

1.  Install hybridflt. These files(.inf, .sys, .cat) are found under the same folder as hybriddrive.exe

2.  Enable Storport Tracing

3.  Run hybriddrive.exe

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
<td><p><strong>Hybriddrive.exe –drive &lt;disk #&gt; -scenario &lt;scenario&gt; &lt;additional options&gt;</strong></p></td>
<td><p>Runs the test.</p></td>
</tr>
<tr class="even">
<td><p><strong>-Drive &lt;disk#&gt;</strong></p></td>
<td><p>The drive to be tested on. The behavior of boot drives or drives with a file system is not defined.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-Verbosity</strong></p></td>
<td><p>The logging level for this test.</p>
<p>Default value: 1</p></td>
</tr>
<tr class="even">
<td><p><strong>-?</strong></p></td>
<td><p>Displays help.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-Scenario logrw</strong></p></td>
<td><p>The scenario to run.</p></td>
</tr>
<tr class="even">
<td><p><strong>-case #</strong></p></td>
<td><p>The test case to run.</p></td>
</tr>
<tr class="odd">
<td><p>-length #(k|m|g)</p></td>
<td><p>Specifies the length of the operation.</p></td>
</tr>
<tr class="even">
<td><p>-offset #(k|m|g)</p></td>
<td><p>Specifies the offset of the operation from the start of the disk.</p></td>
</tr>
<tr class="odd">
<td><p>-tpriority #(|none)</p></td>
<td><p>Specifies the target priority of the operation. Specify <strong>none</strong> for no priority (this is different than a priority of 0).</p></td>
</tr>
<tr class="even">
<td><p>-spriority #</p></td>
<td><p>Specifies the source priority of the operation.</p></td>
</tr>
<tr class="odd">
<td><p>-thigh #</p></td>
<td><p>Specifies the high threshold.</p></td>
</tr>
<tr class="even">
<td><p>-tlow #</p></td>
<td><p>Specifies the low threshold.</p></td>
</tr>
<tr class="odd">
<td><p>-operation (r|w)</p></td>
<td><p>Specifies read or write.</p></td>
</tr>
</tbody>
</table>

 

**Test scenarios:**

-   Logverify

-   Logrw

-   Logcommand

-   Location

-   Tagperf

Manual operation:

-   Print

    -   Prints out the current state of the disk.

-   Changelba

    -   Sends down change lba by range command. Valid options for this command are length, offset, and tpriority.

-   Demote

    -   Sends down demote by size command. Valid options for this command are length, tpriority, and spriority.

-   Off

    -   Turns off the cache.

-   On

    -   Turns on the cache.

-   Evict

    -   Sends an evict command. Valid options for this command are length and offset.

-   Threshold

    -   Sets the dirty threshold. Valid options for this command are thigh and tlow.

-   Movedata

    -   Reads and writes data from the device. Valid options for this command are length, offset, tpriority, and operation. This will also set the priority for any future I/O.

-   Priority

    -   Set the priority for future reads and writes. Valid options for this command are tpriority.

>[!NOTE]
>  
Invalid parameters will be ignored.

Unspecified valid parameters are defaulted to a fixed value.

 

For more information about how to troubleshoot a test, see the troubleshooting section of a specific test in [Device.Storage Tests](device-storage-tests.md).

## <span id="related_topics"></span>Related topics


[Device.Storage Tests](device-storage-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







