---
title: Exporting Test Results
description: Exporting Test Results
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7A7A0619-F709-431A-BE32-478DC511F099
---

# Exporting Test Results


Use the [Export(string outputLocation)](..\API\irunexport-export-method.md) method to export a result that can be run standalone to the specified location on the local file system. Before calling Export(), check the value of CanExport to determine whether the test result can be exported.

When you call **Export()**, the Windows Hardware Lab Kit (Windows HLK) verifies these items:

-   A machine is still associated with the test result. If the machine association with the test result has been removed, the result may not be exportable.
-   Tests must have been executed and completed with a passed, failed, or cancelled status.
-   The test run must successfully return infrastructure logs from the client system. These files are necessary to export the test.
-   Only single machine tests can be exported. Tests that require multiple machines to execute are not exportable.
-   Tests must be run using the HLK desktop client. Test runs on OneCore or Proxy Mobile Client systems are not exportable.
-   Tests tagged as non-exportable due to known infrastructure issues or other reasons are not exportable.

If any of the preceding checks fail, a **TestException** is thrown. The **CanExport** method automatically verifies these items without throwing an exception and can be used to filter out non-exportable test results.

The output directory specified by the outputLocation parameter will be created if it doesn't exist. Under the directory specified by outputLocation, two directories and one file will be created:

-   The infrastructure directory contains an installer with an executable called setup(*architecture*).exe, where *architecture* is the architecture of the machine on which the test was originally run. Running setup(*architecture*).exe installs the components required to run the standalone test on a target system.
-   The test directory contains a batch file plus the binaries required to run the test. Copying the directory to the target system and running the run.cmd file from an elevated command prompt from within the directory containing run.cmd starts standalone test execution of the test on the target system. The directory must not contain any spaces, as this will cause some tests to fail.
-   Readme1st.txt contains instructions and notes on how to run the infrastructure installer and the test.

Exporting different tests to the same directory will succeed as long as the same test is not exported to the directory twice. The Infrastructure and readme1st directories will simply be overwritten if they already exist.

For more information, including how to export a failed HLK job from within the HLK, see [Exporting a Failed HLK Job](..\user\exporting-a-failed-hlk-job.md).

## <span id="related_topics"></span>Related topics


[IRunExport Interface](..\API\irunexport-interface.md)

 

 







