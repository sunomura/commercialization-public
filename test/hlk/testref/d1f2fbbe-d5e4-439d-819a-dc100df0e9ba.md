---
title: SCSI Compliance Test 2.0 (LOGO)
description: SCSI Compliance Test 2.0 (LOGO)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 412f6b71-5081-4b75-abdf-07f7cf04ceef
---

# <span id="p_hlk_test.d1f2fbbe-d5e4-439d-819a-dc100df0e9ba"></span>SCSI Compliance Test 2.0 (LOGO)


This automated test verifies that a block storage device (RAID adapter or disk target) that is supported by the operating system fully complies with the Small Computer System Interface (SCSI) standards described in the SCSI-3 Primary Commands-3 (SPC-3) or later, and SCSI Block Commands-2 (SBC-2) or later specifications. To see these specifications, go to [Technical Committee T10 SCSI Storage Interfaces](http://go.microsoft.com/fwlink/?LinkId=237712).

Ensuring that the block device and the operating system maintain compliance with these standards results in a more robust and reliable system. Although some block devices might not be using a SCSI transport, the operating system communicates with them using SCSI commands (except for individual ATA disk drives that are not part of a RAID set).

The test uses SCSI pass-through requests (IOCTL\_SCSI\_PASS\_THROUGH) to construct and send SCSI command descriptor blocks (CDBs) to the device. The test evaluates the results of the commands to verify compliance.

>[!NOTE]
>  
If you are running this test as a part of a Storage RAID Hardware-based RAID (Storage Array) submission, and your storage array supports Multipath I/O (MPIO), you must configure your MPIO to use Fail-Over Only policy, and set the target storage disk to use the same active path for all MPIO-capable disks.

If you are running this test as a part of a Storage RAID Hardware-based RAID (Storage Array) submission, make sure that LUN0 is configured as the largest size non-boot LUN.

 

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
<li>Device.Storage.Hd.ScsiProtocol.SpcCompliance</li>
<li>Device.Storage.Controller.Raid.BasicFunction</li>
<li>Device.Storage.Hd.ScsiProtocol.ReferenceSpec</li>
<li>Device.Storage.Hd.ScsiProtocol.SamCompliance</li>
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
<td>5</td>
</tr>
<tr class="odd">
<td><strong>Category</strong></td>
<td>Compatibility</td>
</tr>
<tr class="even">
<td><strong>Timeout (in minutes)</strong></td>
<td>300</td>
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


Before you run the test, complete the test setup as described in the test requirements for the type of storage controller that you are testing. See [Hard Disk Drive Testing Prerequisites](hard-disk-drive-testing-prerequisites.md) for more information.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For general troubleshooting information, see [Troubleshooting Device.Storage Testing](troubleshooting-devicestorage-testing.md).

Also, the test writes the results to the log files Scsicompliance.wtl and Scsicompliance.wtl.txt. You can use the results to determine:

-   If a device is compliant with the SCSI specification

-   The optional SCSI commands that are supported by a device

To pass, the SCSI device must support every mandatory command and must be fully compliant with those commands. Each command has a different threshold for pass or fail, and the expectations are specified explicitly in the test and in the log file.

Optional commands are also tested. If a device supports the optional commands and the commands are found to be non-compliant, the test fails. If the device does not support optional commands, the test passes.

>[!NOTE]
>  
Errors from this test occur via issues identified in the log file and in stop errors produced through stressing the driver under test.

 

During the test, if you are having trouble removing a LUN that is failing or are unable to create a LUN from the storage controller, follow these steps:

1.  Prior to running this test, verify that the storage device works properly. Open diskmgmt.msc, select the disk, and make sure that you can put the device Online and Initialized.

2.  Restart the Windows HLK test computer.

3.  Select and rerun the SCSI Compliance Test 2.0. Do not run any test before it.

4.  Run the SCSI Compliance Test (not the SCSI Compliance Test 2.0 (LOGO)) on the same test client and same test storage device. If the test fails again, verify that the storage device is working properly. If the test fails during steps 3 and 4, run the individual failing command data blocks (cdbs) one at a time with the logging verbosity level set to 4 (the highest level of test logging). This will show what data was sent and what data was returned. A test can fail after several cdbs are completed but pass standalone. If this occurs, there is a problem in the firmware or the test.

If you have a device reset that results in the device falling off the bus and subsequent commands to fail, follow these steps:

1.  Copy the test binary (Scsicompliance.exe) from the Windows HLK controller. This file is located at \\\\controllername\\tests\\\[processorarchitectureofyourclient\]\\NTTEST\\DriversTest\\storage\\wdk\\

2.  Copy the wttlog.dll file from the Windows HLK controller. This file is located at \\\\&lt;controllername&gt;\\Tests\\&lt;processorarchitectureofyourclient &gt;\\wtt

3.  Place both of these files on the test computer in a separate folder.

4.  From a command prompt, from the directory containing the test binary, type the following command: Scsicompliance.exe /device &lt;deviceID&gt; /verbosity 4 /operation test /scenario &lt;scenario&gt; /CDB &lt;failingcdbname&gt;

    >[!NOTE]
    >  
    DeviceID and scenario values can be found by checking the repro line within the test log. The failingcdbname can be found by running the test binary with the /?option (scsicompliance.exe /?).

     

5.  Go back to the same directory and review the results to see if you can determine the reason for the test failure.

6.  If you need additional help, collect the txt and wtl logs and share the logs with Microsoft Customer Support.

If you are running this test against Windows Server 2003, make sure the disks or LUNs are not MPIO pseudo-LUNs. MPIO on Windows Server 2003 is not supported.

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


The following commands are validated:

>[!NOTE]
>  
For more information about **Reference**, visit the [Technical Committee T10 SCSI Storage Interfaces](http://go.microsoft.com/fwlink/?LinkId=237712) website.

 

**Command**: Test Unit Ready

**Title**: TEST UNIT READY Basic Verification Test

**Description**: The TEST UNIT READY command provides a means to check if thelogical unit is ready. This is not a request for a self-test. If the logicalunit is able to accept an appropriate medium-access command without returningCHECK CONDITION status, this command shall return a GOOD status.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.33

**Expectation**: The device must return GOOD (0x0) SCSI status

**Rationale**: This is a mandatory SPC-3/SPC-4 command.

**Command**: Request Sense

**Title**: REQUEST SENSE (6) Support Test

**Description**: Checking to see if Request Sense Command is supported and returns GOOD status.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.27

**Expectation**: The device must return GOOD (0x0) SCSI status

**Rationale**: This command is mandatory in SPC-3/SPC-4 and is used by the initiator to retrieve error sense data for failed commands.

**Title**: REQUEST SENSE (6) RESPONSE CODE Test

**Description**: Verify that RESPONSE CODE is either 0x70 or 0x71 or 0x72 or 0x73

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.27

**Expectation**: RESPONSE CODE == 0x70 or RESPONSE CODE == 0x71 or RESPONSE CODE == 0x72 or RESPONSE CODE == 0x73

**Title**: REQUEST SENSE (6) Sense Data Length Test

**Description**: Verify that length of SENSE data is correct (data transferred matches data length reported by the command response).

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.27

**Expectation**: Additional Sense Length &lt;= Sense data size - 8.

**Command**: Read 6

**Title**: READ (6) Basic Verification Test

**Description**: The device must return GOOD (0x0) SCSI status and the first two blocks of data correctly. This test sends two READ commands reading two different but overlapped blocks of data. Then, it compares the overlapped data. It returns true if the overlapped data is the same between the read operations (implying that the two commands read the same data correctly).

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.5

**Expectation**: ScsiStatus == 0x0.

**Rationale**: Some of the applications still use Read 6 and haven't transitioned into Read 10. Therefore we check if this command is implemented and proceed with testing.

**Title**: READ (6) Sequential Read Test

**Description**: The device must read 1000 sequential blocks of data correctly. This test sends the command 1000 times, reading 1024 bytes of data sequentially starting at a random block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.5

**Expectation**: All READ (6) commands succeed.

**Title**: READ (6) Random Read Test

**Description**: The device must read 1000 random blocks of data correctly. This test sends the command 1000 times, reading data at random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.5

**Expectation**: All READ (6) commands succeed.

**Title**: READ (6) Read-With-Disk-Cache-Cleared Test

**Description**: The device must return data correctly after clearing 12MB disk cache. This test first reads 12 MB sequential data for later verification. Then, it clears the disk cache by reading 12 MB random data. Finally, it reads the same 12 MB sequential data to see if the data is same as the one in first read.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.5

**Expectation**: The 12 MB data read after cache cleared is correct.

**Command**: Write 6

**Title**: WRITE (6) Basic Functionality Test

**Description**: The command writes one block of data to device correctly.This test compares the data we want to write and the one returned by the READ after the write operation. If the data is the same, this implies that the WRITE command writes the data to disk correctly.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.24

**Expectation**: ScsiStatus == 0x0.

**Rationale**: Some of the applications still use Write 6 and haven't transitioned into Write 10. Therefore we check if this command is implemented and proceed with testing.

**Title**: WRITE (6) Sequential Write Test

**Description**: The command writes 1000 sequential blocks of data correctly.This test sends the command 1000 times, writing data sequentially starting at a random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.24

**Expectation**: All WRITE (6) commands succeed.

**Title**: WRITE (6) Random Write Test

**Description**: The command writes 1000 random blocks of data correctly.This test sends the WRITE command 1000 times, writing data at random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.24

**Expectation**: All WRITE (6) commands succeed.

**Title**: WRITE (6) Write-With-Disk-Cache-Disabled Test

**Description**: The command writes 12 MB of data correctly with cache disabled.This test writes 12 MB of data to disk. Then, it reads the same 12 MB data that has just been written to verify that the data we just write are correct.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.24

**Expectation**: The 12 MB data are written correctly.

**Title**: WRITE (6) Write-With-Disk-Cache-Enabled Test

**Description**: The command writes 12 MB of data correctly with cache enabled.This test writes 12 MB of data to disk. Then, it sends a SYNCHRONIZE CACHE (10) command to synchronize the logical block address in cache with the ones in disk. Finally, it will read the same 12 MB data that has just been written to verify that the data we just write are correct.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.24

**Expectation**: The 12 MB data are written correctly.

**Command**: Inquiry

**Title**: INQUIRY Basic Verification Test

**Description**: The device must return GOOD (0x0) SCSI status and data of size smaller than or equal to 255 bytes in response to the INQUIRY command with ALLOCATION LENGTH field set to 255 (0xFF) bytes. The ALLOCATION LENGTH field specifies the maximum number of bytes that an application client has allocated for returned data.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: The device must return GOOD (0x0) SCSI status and data of size smaller than or equal to 255 bytes.

**Title**: INQUIRY Test for error when PAGE CODE field is nonzero and EVPD=0.

**Description**: Checking that an error is returned when PAGE CODE field isnonzero and EVPD=0. Checking that an error is returned when PAGE CODE field isnonzero and EVPD=0.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: ScsiStatus == 0x2, CHECK CONDITION. ScsiStatus == 0x2, CHECK CONDITION.

**Title**: INQUIRY Retrieving standard inquiry data.

**Description**: Checking if we can retrieve standard inquiry data. Checking if we can retrieve standard inquiry data.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: ScsiStatus == 0x0, GOOD.

**Title**: INQUIRY Checking size of standard inquiry data.

**Description**: Standard INQUIRY data shall contain at least 36 bytes.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: Data Transfer Length &gt;= 36 bytes.

**Title**: INQUIRY Testing device type field

**Description**: Checking device type field to ensure it is a direct access device.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: Device Type == 0x0, Direct-access device.

**Title**: INQUIRY Testing peripheral qualifier field.

**Description**: Checking Peripheral Qualifier field.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: Peripheral qualifier field == 0

**Title**: INQUIRY VERSION Field Test

**Description**: The device must return a valid VERSION field of 0x4, 0x5 or 0x6

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: VERSION is 0x4 (SPC-2) or later for non-SCSI bus type and VERSION is 0x3 (SPC)or later for SCSI bus type.

**Title**: INQUIRY Checking RESPONSE DATA FORMAT.

**Description**: Checking that RESPONSE DATA FORMAT == 2.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: RESPONSE DATA FORMAT == 2.

**Title**: INQUIRY Checking additional length.

**Description**: Checking additional length field is correct.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: Additional Length field == Total Data size - 5

**Title**: INQUIRY Checking VENDOR IDENTIFICATION field.

**Description**: Checking that VENDOR IDENTIFICATION field contains valid ASCII.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: VENDOR IDENTIFICATION field contains valid ASCII.

**Title**: INQUIRY Checking PRODUCT IDENTIFICATION field.

**Description**: Checking that PRODUCT IDENTIFICATION field contains valid ASCII.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: PRODUCT IDENTIFICATION field contains valid ASCII.

**Title**: INQUIRY Checking PRODUCT REVISION LEVEL field.

**Description**: Checking that PRODUCT REVISION LEVEL field contains valid ASCII.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: PRODUCT REVISION LEVEL field contains valid ASCII.

**Title**: INQUIRY Command Support Data Test.

**Description**: The device must set the HiSup bit in the Standard Inquiry Data.

**Reference**: SCSI Architecture Model - 3 (SAM-3) Revision 14 (or later) specification Section 4.9.2

**Expectation**: HiSup bit is set in Standard Inquiry Data.

**Title**: INQUIRY Checking for Supported Vital Product Pages.

**Description**: Checking to see if Vital Product Pages are supported.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4.4

**Expectation**: List of Supported Vital Product Data Pages is returned.

**Title**: INQUIRY Testing access to each supported Vital Product Data Page.

**Description**: Attempting to access each supported Vital Product Data Page.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4.4

**Expectation**: Each supported page is accessible (up to 255 bytes).

**Title**: INQUIRY Attempting Unit Serial Number Page 0x80.

**Description**: Checking if Unit Serial Number Page 0x80 is supported, and is valid ASCII.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 7.6.10

**Expectation**: ScsiStatus == 0x0, and result is valid ASCII.

**Title**: INQUIRY Attempting Device identification Page 0x83.

**Description**: Checking if Device identification Page 0x83 is supported.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 7.6.3

**Expectation**: ScsiStatus == 0x0.

**Title**: INQUIRY Checking Identification Descriptors in VPD page 0x83.

**Description**: Checking that Identification Descriptors contain meaningful data.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 7.6.3

**Expectation**: All descriptors are compliant, and contain meaningful data.

**Title**: INQUIRY Checking Version Descriptors.

**Description**: Checking to see if Version Descriptors are compliant.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.4

**Expectation**: Version descriptors exist.

**Command**: Mode Select 6

**Title**: MODE SELECT (6) Basic Test

**Description**: Checking to see if a simple MODE SELECT command, with PF and SP == 0, passes

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: The device must return GOOD (0x0) SCSI status

**Rationale**: Our Storage stack uses Caching Mode Page to turn on/off the device caching. Therefore the ability to write to mode pages using Mode Select commands is required.

**Title**: MODE SELECT 6: MODE SENSE (6) Attempting to get Caching mode page.

**Description**: Checking to see if a simple MODE SENSE command on Page 0x08 will return GOOD status.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 6: MODE SENSE (6) Checking Parameters Savable (PS bit).

**Description**: Checking to see if Parameters Savable bit for the Caching Mode Page is 1.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: PS == 1.

**Title**: MODE SELECT 6: MODE SENSE (6) Checking Mode Parameter Header

**Description**: Verify that MediumType == 0 and BlockDescriptorLength == 0.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: MediumType == 0x0 and BlockDescriptorLength == 0x0

**Title**: MODE SELECT 6: MODE SENSE (6) Checking Caching Mode Page Length.

**Description**: Checking the Caching Mode Page is 20 bytes.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: cachePageLength == 20 bytes.

**Title**: MODE SELECT 6: MODE SENSE (6) Getting Changeable values.

**Description**: Saving away Changeable Values for Caching Mode Page

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 6: MODE SENSE (6) Getting default values.

**Description**: Saving away Default Values for Caching Mode Page.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT (6) Changing WCE.

**Description**: Applying MODE SELECT to WCE=0 for the device.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 6: MODE SENSE (6) Checking that WCE has been cleared.

**Description**: Checking that the previous MODE SELECT command actually changed the current mode parameters.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: WCE is clear.

**Title**: MODE SELECT 6: MODE SENSE (6) Checking that Saved Values have changed.

**Description**: Checking that the previous MODE SELECT command actually changed the saved mode parameters.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: Saved values have changed.

**Title**: MODE SELECT (6) setting WCE

**Description**: Applying MODE SELECT to set WCE.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 6: MODE SENSE (6) Checking that WCE has been set.

**Description**: Checking that the previous MODE SELECT command actually set WCE.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: Current values have been set.

**Title**: MODE SELECT (6) Attempting to restore original values.

**Description**: Testing MODE SELECT can return the Caching Mode Page values to their original values.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 6: MODE SENSE (6) Verifying values were restored.

**Description**: Checking that the values were restored in the Caching Mode Page.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.7

**Expectation**: Current values equal default values.

**Command**: Mode Sense 6

**Title**: MODE SENSE (6) Basic Test

**Description**: Checking to see if a simple MODE SENSE command on Page 0x3f will return GOOD status

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: The device must return GOOD (0x0) SCSI status

**Rationale**: Storage stack uses Caching Mode Page to turn on/off the device caching. Therefore the ability to read to mode pages using Mode Sense commands is required.

**Title**: MODE SENSE (6) Checking size of returned data.

**Description**: Checking that we receive a minimum amount of data (i.e. at least the MODE PARAMETER HEADER).

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Data Transfer Length &gt;= 4 bytes

**Title**: MODE SENSE (6) Checking MODE PARAMETER HEADER

**Description**: Checking that the MODE PARAMETER HEADER length information is valid.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: ModeDataLength = Data Transfer Length - 1 = -1 bytes.

**Title**: MODE SENSE (6) Test DBD (disable block descriptors) bit.

**Description**: Testing to make sure that, when DBD bit is set, no block descriptors are returned.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Block Descriptor Length = 0

**Title**: MODE SENSE (6) Testing new data length when DBD bit is set.

**Description**: : Testing that new data length should equal old data length minus block descriptor length.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: New Data Length = Old Data Length

**Title**: MODE SENSE (6) Comparing MODE PAGE data before and after DBD bit is set

**Description**: Testing that page data is the same before and after DBD bit is set.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Page data will match

**Title**: MODE SENSE (6) Testing Page Control Field

**Description**: Testing different values of the Page control field, and enforcing the size of the data returned.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Data length for each value of PC is correct.

**Title**: MODE SENSE (6) Scanning All Mode Pages.

**Description**: Checking Mode Page 0x3f data to examine supported mode pages.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: To find supported mode pages: Information exception control mode page and Caching mode page.

**Title**: MODE SENSE (6) Ensuring mandatory mode pages are supported

**Description**: Checking that required mode pages are present in MODE PAGE 0x3f

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Caching and Informational Exception pages are supported, at a minimum.

**Title**: MODE SENSE (6) Checking Individual Mode Pages

**Description**: Testing to ensure we can access each individual mode page, and that the paremeters are correct

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Pages should be returned and the headers should be compliant

**Title**: MODE SENSE (6) Checking Informational Exception Mode Page

**Description**: Ensuring Informational Exception Mode Page is compliant

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Power Condition Mode Page is supported

**Title**: MODE SENSE (6) Checking Informational Exception Mode Page

**Description**: Ensuring Informational Exception Mode Page is compliant

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Power Condition Mode Page is supported

**Title**: MODE SENSE (6) Checking Power Condition Mode Page.

**Description**: Ensuring Power Condition Mode Page is compliant

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Informational Exception Mode Page is supported

**Title**: MODE SENSE (6) Checking Caching Mode Page.

**Description**: Ensuring Caching Mode Page is compliant.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Caching Mode Page is supported.

**Title**: MODE SENSE (6) Checking Device Specific Parameters

**Description**: This tests to see if the Device specific parameters are supported.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.9

**Expectation**: Nothing.

**Command**: Read Capacity 10

**Title**: READ CAPACITY (10) Basic Verification Test

**Description**: The device must return GOOD (0x0) SCSI status and 8 bytes of parameter data describing the capacity and medium format of the block device to the data-in buffer.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.10

**Expectation**: The device must return GOOD (0x0) SCSI status

**Rationale**: This command is required for formatting operations and initialization.

**Command**: Read 10

**Title**: READ (10) Basic Functionality Test

**Description**: The command reads the first two blocks of data correctly.This test sends two READ commands reading two different but overlapped blocks of data. Then, it compares the overlapped data. It returns true if the overlapped data is the same between the read operations (implying that the two commands read the same data correctly).

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.6

**Expectation**: Scsi Status == 0x0.

**Rationale**: Used to Read data from device.

**Title**: READ (10) Sequential Read Test

**Description**: The command reads 1000 sequential blocks of data correctly.This test sends the command 1000 times, reading data sequentially starting at a random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.6

**Expectation**: All READ (10) commands succeed.

**Title**: READ (10) Random Read Test

**Description**: The command reads 1000 random blocks of data correctly.This test sends the command 1000 times, reading data at random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.6

**Expectation**: All READ (10) commands succeed.

**Title**: READ (10) Read-With-Disk-Cache-Cleared Test

**Description**: The command reads 12 MB of data correctly with disk cache cleared.This test first reads 12 MB sequential data for later verification. Then, it clears the disk cache by reading 12 MB random data. Finally, it reads the same 12 MB sequential data to see if the data is same as the one in first read.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.6

**Expectation**: The 12 MB data read after cache cleared is correct.

**Command**: Write 10

**Title**: WRITE (10) Basic Functionality Test

**Description**: The command writes one block of data to device correctly.This test compares the data we want to write and the one returned by the READ after the write operation. If the data is the same, this implies that the WRITE command writes the data to disk correctly.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.25

**Expectation**: ScsiStatus == 0x0.

**Rationale**: Used to write data to device.

**Title**: WRITE (10) Sequential Write Test

**Description**: The command writes 1000 sequential blocks of data correctly.This test sends the command 1000 times, writing data sequentially starting at a random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.25

**Expectation**: All WRITE (10) commands succeed.

**Title**: WRITE (10) Random Write Test

**Description**: The command writes 1000 random blocks of data correctly.This test sends the WRITE command 1000 times, writing data at random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.25

**Expectation**: All WRITE (10) commands succeed.

**Title**: WRITE (10) Write-With-Disk-Cache-Disabled Test

**Description**: The command writes 12 MB of data correctly with cache disabled.This test writes 12 MB of data to disk. Then, it reads the same 12 MB data that has just been written to verify that the data we just write are correct.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.25

**Expectation**: The 12 MB data are written correctly

**Title**: WRITE (10) Write-With-Disk-Cache-Enabled Test

**Description**: The command writes 12 MB of data correctly with cache enabled.This test writes 12 MB of data to disk. Then, it sends a SYNCHRONIZE CACHE (10) command to synchronize the logical block address in cache with the ones in disk. Finally, it will read the same 12 MB data that has just been written to verify that the data we just write are correct.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.25

**Expectation**: The 12 MB data are written correctly.

**Title**: WRITE (10) FUA Test

**Description**: The command writes data to disk correctly with cache and FUA (Force Unit Access) on.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.25.

**Expectation**: Data is written correctly to disk with FUA on. Checksums of all WRITE (10) are correct.

**Title**: VERIFY (10) Support Test

**Description**: Verify that the device supports the VERIFY (10) command. This test issues a simple VERIFY (10) command and checks whether the return code is 0x2 (meaning not supported).

**Reference**: SCSI Block Commands - 3 (SBC-3) Revision 27 (or published) specification Section 5.28.

**Expectation**: Scsi Status is 0x0 (GOOD).

**Title**: VERIFY (10) Zero Length Test

**Description**: The test sends VERIFY (10) command with both LOGICAL BLOCK ADDRESS and VERIFICATION LENGTH set to 0. Based on the spec, VERIFICATION LENGTH field set to zero specifies that no logical blocks shall be verified. This condition shall not be considered as an error.

**Reference**: SCSI Block Commands - 3 (SBC-3) Revision 27 (or published) specification Section 5.28.

**Expectation**: Scsi Status is 0x0 (GOOD).

**Title**: VERIFY (10) Random LBA Test

**Description**: The test sends VEIRFY (10) command with VERIFICATION LENGTH = 1 and randomized LOGICAL BLOCK ADDRESS (random between 0 and last LBA).

**Reference**: SCSI Block Commands - 3 (SBC-3) Revision 27 (or published) specification Section 5.28.

**Expectation**: Scsi Status is 0x0 (GOOD).

**Title**: VERIFY (10) Exceed Capacity Test

**Description**: The test sends VEIRFY (10) command with VERIFICATION LENGTH = 2 and LOGICAL BLOCK ADDRESS set to the last LBA.

**Reference**: SCSI Block Commands - 3 (SBC-3) Revision 27 (or published) specification Section 5.28.

**Expectation**: Scsi Status is 0x2 (CHECK CONDITION).

**Command**: Mode Select 10

**Title**: MODE SELECT (10) Basic Test

**Description**: Checking to see if a simple MODE SELECT command, with PF and SP == 0, passes

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: The device must return GOOD (0x0) SCSI status

**Rationale**: Mode Select 6 is mandatory and Mode Select 10 is Optional and would be tested if-implemented.

**Title**: MODE SELECT 10: MODE SENSE (10) Attempting to get Caching mode page.

**Description**: Checking to see if a simple MODE SENSE command on Page 0x08 will return GOOD status.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 10: MODE SENSE (10) Checking Parameters Savable (PS bit).

**Description**: Checking to see if Parameters Savable bit for the Caching Mode Page is 1.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: PS == 1.

**Title**: MODE SELECT 10: MODE SENSE (10) Checking Mode Parameter Header

**Description**: Verify that MediumType == 0 and BlockDescriptorLength == 0.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: MediumType == 0x0 and BlockDescriptorLength == 0x0

**Title**: MODE SELECT 10: MODE SENSE (10) Checking Caching Mode Page Length.

**Description**: Checking the Caching Mode Page is 20 bytes.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: cachePageLength == 20 bytes.

**Title**: MODE SELECT 10: MODE SENSE (10) Getting Changeable values.

**Description**: Saving away Changeable Values for Caching Mode Page

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 10: MODE SENSE (10) Getting default values.

**Description**: Saving away Default Values for Caching Mode Page.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: The device must return GOOD (0x0) SCSI statu

**Title**: MODE SELECT (10) Changing WCE.

**Description**: Applying MODE SELECT to WCE=0 for the device.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 10: MODE SENSE (10) Checking that WCE has been cleared.

**Description**: Checking that the previous MODE SELECT command actually changed the current mode parameters.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: : WCE is clear.

**Title**: MODE SELECT 10: MODE SENSE (10) Checking that Saved Values have changed.

**Description**: Checking that the previous MODE SELECT command actually changed the saved mode parameters.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: Saved values have changed.

**Title**: MODE SELECT (10) setting WCE

**Description**: Applying MODE SELECT to set WCE.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 10: MODE SENSE (10) Checking that WCE has been set.

**Description**: Checking that the previous MODE SELECT command actually set WCE.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: Current values have been set.

**Title**: MODE SELECT (10) Attempting to restore original values.

**Description**: Testing MODE SELECT can return the Caching Mode Page values to their original values

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: MODE SELECT 10: MODE SENSE (10) Verifying values were restored.

**Description**: Checking that the values were restored in the Caching Mode Page.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.8

**Expectation**: Current values equal default values.

**Command**: Mode Sense 10

**Title**: MODE SENSE (10) Basic Test

**Description**: Checking to see if a simple MODE SENSE10 command on Page 0x3f will return GOOD status

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.10

**Expectation**: The device must return GOOD (0x0) SCSI status

**Rationale**: Mode Sense 6 is mandatory and Mode Sense 10 is Optional and would be tested if-implemented.

**Title**: MODE SENSE (10) Checking size of returned data.

**Description**: Checking that we receive a minimum amount of data (i.e. at least the MODE PARAMETER HEADER).

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.10

**Expectation**: Data Transfer Length &gt;= 8 bytes

**Title**: MODE SENSE (10) Checking MODE PARAMETER HEADER

**Description**: Checking that the MODE PARAMETER HEADER length information is valid.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.10

**Expectation**: ModeDataLength = Data Transfer Length - 2 = -2 bytes.

**Title**: MODE SENSE (10) Test DBD (disable block descriptors) bit.

**Description**: Testing to make sure that, when DBD bit is set, no block descriptors are returned.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.10

**Expectation**: Block Descriptor Length = 0

**Title**: MODE SENSE (10) Comparing MODE PAGE data before and after DBD bit is set

**Description**: Testing that page data is the same before and after DBD bit is set.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.10

**Expectation**: Page data will match

**Title**: MODE SENSE (10) Testing Page Control Field

**Description**: Testing different values of the Page control field, and enforcing the size of the data returned.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.10

**Expectation**: Data length for each value of PC is correct and PC=0 and PC=2 return good status.

**Command**: Read 16

**Title**: READ (16) Support Test

**Description**: Verify that the device supports the READ (16) command.This test issues a simple READ (16) command and checks whether the return code is 0x2 (meaning not supported).

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.8

**Expectation**: Scsi Status is 0x0.

**Title**: READ (16) Basic Functionality Test

**Description**: The command reads the first two blocks of data correctly.This test sends two READ commands reading two different but overlapped blocks of data. Then, it compares the overlapped data. It returns true if the overlapped data is the same between the read operations (implying that the two commands read the same data correctly).

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.8

**Expectation**: Scsi Status is 0x0.

**Rationale**: If device is 64-bit LBA, Read 16 is Mandatory to read entire disk. Else its if-implemented.

**Title**: READ (16) Sequential Read Test

**Description**: The device must read 1000 sequential blocks of data correctly. This test sends the command 1000 times, reading data sequentially starting at a random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.8

**Expectation**: All READ (16) commands succeed.

**Title**: READ (16) Random Read Test

**Description**: The command reads 1000 random blocks of data correctly.This test sends READ (16) command 1000 times, reading data at random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.8

**Expectation**: All READ (16) commands succeed.

**Title**: READ (16) Read-With-Disk-Cache-Cleared Test

**Description**: The command reads 12 MB of data correctly with disk cache cleared.This test first reads 12 MB sequential data for later verification. Then, it clears the disk cache by reading 12 MB random data. Finally, it reads the same 12 MB sequential data to see if the data is same as the one in first read.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.8

**Expectation**: The 12 MB data read after cache cleared is correct.

**Command**: Write 16

**Title**: WRITE (16) Support Test

**Description**: Verify that the device supports the command.This test issues a simple WRITE (16) command and checks whether the return code is 0x2 (Check Condition).

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.27

**Expectation**: ScsiStatus == 0x0.

**Title**: WRITE (16) Basic Functionality Test

**Description**: The command writes one block of data to device correctly.This test compares the data we want to write and the one returned by the READ after the write operation. If the data is the same, this implies that the WRITE command writes the data to disk correctly.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.27

**Expectation**: : ScsiStatus == 0x0.

**Rationale**: If device is 64-bit LBA, Write 16 is Mandatory to write entire disk. Else its if-implemented.

**Title**: WRITE (16) Sequential Write Test

**Description**: The command writes 1000 sequential blocks of data correctly.This test sends the command 1000 times, writing data sequentially starting at a random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.27

**Expectation**: All WRITE (16) commands succeed.

**Title**: WRITE (16) Random Write Test

**Description**: The command writes 1000 random blocks of data correctly.This test sends the WRITE command 1000 times, writing data at random logical block address.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.27

**Expectation**: All WRITE (16) commands succeed.

**Title**: WRITE (16) Write-With-Disk-Cache-Disabled Test

**Description**: The command writes 12 MB of data correctly with cache disabled.This test writes 12 MB of data to disk. Then, it reads the same 12 MB data that has just been written to verify that the data we just write are correct.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.27

**Expectation**: The 12 MB data are written correctly.

**Title**: WRITE (16) Write-With-Disk-Cache-Enabled Test

**Description**: The command writes 12 MB of data correctly with cache enabled.This test writes 12 MB of data to disk. Then, it sends a SYNCHRONIZE CACHE (10) command to synchronize the logical block address in cache with the ones in disk. Finally, it will read the same 12 MB data that has just been written to verify that the data we just write are correct.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.27

**Expectation**: The 12 MB data returned by the WRITEs is correct.

**Title**: VERIFY (16) Support Test

**Description**: Verify that the device supports the VERIFY (16) command. This test issues a simple VERIFY (16) command and checks whether the return code is 0x2 (meaning not supported).

**Reference**: SCSI Block Commands - 3 (SBC-3) Revision 27 (or published) specification Section 5.30.

**Expectation**: Scsi Status is 0x0 (GOOD).

**Title**: VERIFY (16) Zero Length Test

**Description**: The test sends VERIFY (16) command with both LOGICAL BLOCK ADDRESS and VERIFICATION LENGTH set to 0. Based on the spec, VERIFICATION LENGTH field set to zero specifies that no logical blocks shall be verified. This condition shall not be considered as an error.

**Reference**: SCSI Block Commands - 3 (SBC-3) Revision 27 (or published) specification Section 5.30.

**Expectation**: Scsi Status is 0x0 (GOOD).

**Title**: VERIFY (16) Random LBA Test

**Description**: The test sends VERIFY (16) command with VERIFICATION LENGTH = 1 and randomized LOGICAL BLOCK ADDRESS (random between 0 and last LBA).

**Reference**: SCSI Block Commands - 3 (SBC-3) Revision 27 (or published) specification Section 5.30.

**Expectation**: Scsi Status is 0x0 (GOOD).

**Title**: VERIFY (16) Exceed Capacity Test

**Description**: The test sends VEIRFY (16) command with VERIFICATION LENGTH = 2 and LOGICAL BLOCK ADDRESS set to the last LBA.

**Reference**: SCSI Block Commands - 3 (SBC-3) Revision 27 (or published) specification Section 5.30.

Expectation: Scsi Status is 0x2 (CHECK CONDITION).

**Command**: Report LUNS

**Title**: REPORT LUNS Basic Verification Test

**Description**: Attempts to find the LUN 0 corresponding to D.U.T. and execute the REPORT LUNS command. This test will only send REPORT LUNS to LUN 0 at the current target address per SAM-3. This test will only issue a request with SELECT REPORT set to zero per SPC-3.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.21

**Expectation**: The device must return GOOD (0x0) SCSI status and data of size smaller than or equal to 255 bytes.

**Rationale**: Report LUNS is used to discover LUNs present on the device. It is Mandatory for UAS. BOT uses the GetMaxLun USB class-specific command instead. So this is optional for BOT devices. Although we check for implementation of this CDB and test this command if implemented.

**Title**: REPORT LUNS LUN0 Test

**Description**: This test will only send REPORT LUNS to LUN 0 at the current target address per SAM-3.This test will only issue a request with SELECT REPORT set to zero per SPC-3.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.21

**Expectation**: The device must return GOOD (0x0) SCSI status and data of size smaller than or equal to 255 bytes.

**Title**: REPORT LUNS Data valid Test

**Description**: This test will only send REPORT LUNS to LUN 0 at the current target address per SAM-3.This test will only issue a request with SELECT REPORT set to zero per SPC-3.

**Reference**: SCSI Primary Commands - 3 (SPC-3) Revision 23 (or published) specification Section 6.21

**Expectation**: Each reported LUN uses single level numbers restricted to &lt;= 255.

**Command**: Read Capacity 16

**Title**: READ CAPACITY (16) Allocation length test

**Description**: The device must return GOOD (0x0) SCSI status even though allocation lengthis set to 0 value

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.11

**Expectation**: The device must return GOOD (0x0) SCSI status

**Rationale**: This command is required for formatting operations and initialization.

**Title**: READ CAPACITY (16) Basic Verification Test

**Description**: The device must return GOOD (0x0) SCSI status and 8 bytes of parameter data describing the capacity and medium format of the block device to the data-in buffer.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.11

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: READ CAPACITY (16) Capacity Test

**Description**: Send a READ CAPACITY command to check the reported block address. If the block address is greater than the READ CAPACITY 10 limit, ensure READ CAPACITY 10 block address is set to 0xFFFF\_FFFF.

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.11

**Expectation**: For block addresses greater than READ CAPACITY 10 can describe, the READ CAPACITY 10 block address is set to 0xFFFF\_FFFF.

**Command**: Start Stop Unit

**Title**: START STOP UNIT Basic Test 1

**Description**: Sending StartStopUnit with IMMED=0, LOEJ=0, START=0, spin down drive

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.17

**Expectation**: The device must return GOOD (0x0) SCSI status

**Rationale**: This command is required to ensure data integrity in the face of power state changes and disconnection from the bus.

**Title**: START STOP UNIT Basic Test 2

**Description**: Sending StartStopUnit with IMMED=0, LOEJ=0, START=1, spin up drive

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.17

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: START STOP UNIT Basic Test 3

**Description**: Sending StartStopUnit with IMMED=1, LOEJ=0, START=0, spin down drive

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.17

**Expectation**: The device must return GOOD (0x0) SCSI status

**Title**: START STOP UNIT Basic Test 4

**Description**: Sending StartStopUnit with IMMED=1, LOEJ=0, START=1, spin up drive

**Reference**: SCSI Block Commands - 2 (SBC-2) Revision 16 (or published) specification Section 5.17

**Expectation**: The device must return GOOD (0x0) SCSI status

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
<td><p><strong>Scsicompliance.exe</strong></p></td>
<td><p>The options for the test are listed below</p></td>
</tr>
<tr class="even">
<td><p><strong>/device</strong></p></td>
<td><p>The device which test is to run on</p>
<p>Example: /Device &lt;physical device path&gt;</p></td>
</tr>
<tr class="odd">
<td><p><strong>/operation</strong></p></td>
<td><p>The operation to run.</p>
<p>Example: /Operation Test</p></td>
</tr>
<tr class="even">
<td><p><strong>/scenario</strong></p></td>
<td><p>The feature to be tested for.</p>
<p>Example: /Scenario Common</p></td>
</tr>
<tr class="odd">
<td><p><strong>/verbosity</strong></p></td>
<td><p>The level of logging verbosity. Larger values cause more verbose output.</p>
<p>Example: /Verbosity 4</p></td>
</tr>
</tbody>
</table>

>[!NOTE]
>  
For command-line help for this test binary, type **/?**.

 

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
<td><p>Scsicompliance.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\driverstest\storage\wdk\nttest\</p></td>
</tr>
</tbody>
</table>

 

### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name         | Parameter description                                                                                                                                                                                          |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **DiskDeviceObjLink**  | Device path of disk to test EX: \\\\.\\disk0                                                                                                                                                                   |
| **WDKDeviceID**        | Instance path of device to test                                                                                                                                                                                |
| **LoggingVerbosity**   | LoggingVerbosity: Detail of logging. Levels are cumulative. 0 = Assertions and results. 1 = Details (default). 2 = CDBs , data, and sense info. 3 = Debug and detailed Mode page information. 4 = Memory usage |
| **ScenarioId**         | Scenario test name.                                                                                                                                                                                            |
| **LLU\_NetAccessOnly** | User account for accessing test fileshare.                                                                                                                                                                     |
| **LLU\_LclAdminUsr**   | User account for running the test.                                                                                                                                                                             |
| **OperationId**        |                                                                                                                                                                                                                |
| **Destructive**        | (0,1) 0=Passive, 1=Destructive                                                                                                                                                                                 |

 

 

 






