---
title: HLK API Samples
description: HLK API Samples
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f02d9eee-0cd6-4921-9c33-fe67e4548cc5
---

# HLK API Samples


This section describes sample code that you can use to access the Windows Hardware Lab Kit (Windows HLK) API.

In this section:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Topic</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Hello World](hello-world.md)</p></td>
<td><p>This sample is a basic introduction to how to create a project, run tests, and create a package.</p></td>
</tr>
<tr class="even">
<td><p>[List Projects](list-projects.md)</p></td>
<td><p>This sample lists all projects in a controller and prints basic information about each.</p></td>
</tr>
<tr class="odd">
<td><p>[Target Families](target-families.md)</p></td>
<td><p>This sample shows how to create target families and run tests against them.</p></td>
</tr>
<tr class="even">
<td><p>[Advanced scheduling](advanced-scheduling.md)</p></td>
<td><p>These samples demonstrate advanced scheduling scenarios.</p></td>
</tr>
<tr class="odd">
<td><p>[Creating a Package](creating-a-package.md)</p></td>
<td><p>This sample describes the steps of creating a package from a project.</p></td>
</tr>
<tr class="even">
<td><p>[Diagnostic Bugcheck Summary](diagnostic-bugcheck-summary.md)</p></td>
<td><p>This sample shows how to retrieve and display a diagnostic bugcheck summary for a test that fails during a system crash.</p></td>
</tr>
<tr class="odd">
<td><p>[Exporting a Test Result](exporting-a-test-result.md)</p></td>
<td><p>This sample shows how to export a failed test result so that it can be run on a machine outside of the full HLK environment.</p></td>
</tr>
<tr class="even">
<td><p>[Extracting Log Files from a Package](extracting-log-files-from-a-package.md)</p></td>
<td><p>This sample shows you how to extract log files from a package.</p></td>
</tr>
<tr class="odd">
<td><p>[Filtering](filtering-code-sample.md)</p></td>
<td><p>This sample shows how to apply filters to a project and retrieve filters from a project.</p></td>
</tr>
<tr class="even">
<td><p>[Finding missing tests](finding-missing-tests.md)</p></td>
<td><p>This sample shows how to find tests that are missing from a package.</p></td>
</tr>
<tr class="odd">
<td><p>[Machine Pool Growth](machine-pool-growth.md)</p></td>
<td><p>This sample uses the Machine Pool Growth feature to add and automatically redistribute tests to targets after a test has been scheduled.</p></td>
</tr>
<tr class="even">
<td><p>[Machines in use](machines-in-use.md)</p></td>
<td><p>This sample shows how to retrieve the names of machines on which tests are currently running.</p></td>
</tr>
<tr class="odd">
<td><p>[Manage Machine State](manage-machine-state.md)</p></td>
<td><p>This sample shows how to manage machine stated.</p></td>
</tr>
<tr class="even">
<td><p>[Mobile Reflash Before a Test Run](mobile-reflash-before-a-test-run.md)</p></td>
<td><p>This sample shows how to flash an OS image onto a mobile device as part of a test run.</p></td>
</tr>
<tr class="odd">
<td><p>[Multi-Device Tests](multi-device-tests.md)</p></td>
<td><p>This sample shows how to run multi-device tests.</p></td>
</tr>
<tr class="even">
<td><p>[Project Definition File schema](project-definition-file-schema.md)</p></td>
<td><p>This sample defines the format of the Project Definition File.</p></td>
</tr>
<tr class="odd">
<td><p>[Schedule Information](schedule-information.md)</p></td>
<td><p>This sample shows the usage of the DistributionOption enumeration and the new test metadata flags.</p></td>
</tr>
<tr class="even">
<td><p>[Schedule test by Development Phase](schedule-test-by-development-phase.md)</p></td>
<td><p>This sample demonstrates a few ways to schedule tests.</p></td>
</tr>
<tr class="odd">
<td><p>[Test Collection File schema](test-collection-file-schema.md)</p></td>
<td><p>This sample defines the format of the Test Collection File.</p></td>
</tr>
</tbody>
</table>

 

## <span id="Resource_Files"></span><span id="resource_files"></span><span id="RESOURCE_FILES"></span>Resource Files


The samples in this section require the following resource files. Install the HLK to obtain these files. To use the DLLs in your Visual Studio project, click **Project**, click **Add Reference**, and then click **Browse** to navigate to each file.

-   microsoft.windows.kits.hardware.logging.dll

-   microsoft.windows.kits.hardware.objectmodel.dbconnection.dll

-   microsoft.windows.kits.hardware.objectmodel.dll

-   microsoft.windows.kits.hardware.objectmodel.submission.dll

-   Microsoft.WTT.Diagnostics.dll

-   WTTOMBase.dll

-   WTTOMDimension.dll

-   WTTOMFeature.dll

-   WTTOMIdentity.dll

-   WTTOMJobs.dll

-   WTTOMParameter.dll

-   WTTOMResource.dll

-   WTTOMSQLProvider.dll

 

 






