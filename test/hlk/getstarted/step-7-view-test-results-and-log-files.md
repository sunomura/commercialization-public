---
title: Step 7 View test results and log files
description: Step 7 View test results and log files
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e010ab9a-f231-4842-8b1c-9aa227610a96
---

# Step 7: View test results and log files


The **Results** tab displays detailed information about each test. As each test completes, the status column updates with the result—pass or fail.

The following image shows the Studio **Results** tab.

![hlk studio results tab](images/hlk-studio-results-tab.png)

## <span id="Troubleshooting_a_failed_test"></span><span id="troubleshooting_a_failed_test"></span><span id="TROUBLESHOOTING_A_FAILED_TEST"></span>Troubleshooting a failed test


If a test fails, you can expand the test details to review the associated log file.

1.  From the list, select a failed test, indicated by a red X or the system crash icon (![system crash icon](images/test-fail-bugcheck-icon.png)).

2.  Expand the **Test Name** node, expand the **Logs** node, and then double-click the log file.

    You can review these log files:

    -   **.log file.** Text dump.

    -   **.wtl file.** Open to view error reports.

    -   **.xml file.** Change file name extension to .wtl to view error reports.

Right-click any test to see additional test details, including:

-   [Bugcheck Summary information](..\user\hlk-studio---results-tab.md#sysx) for system crashes that occur during test runs

-   Task logs

-   Additional files

-   Applied filters

-   Errors

-   Infrastructure (gather and execution logs)

To learn more about the different options on this page, including distributed and multi-device support, see [HLK Studio - Results Tab](..\user\hlk-studio---results-tab.md).

## <span id="Exporting_failed_HLK_jobs"></span><span id="exporting_failed_hlk_jobs"></span><span id="EXPORTING_FAILED_HLK_JOBS"></span>Exporting failed HLK jobs


You can now export a failed job and re-run it on a machine that does not have the HLK Client installed. For more information, see [Exporting a Failed HLK Job](..\user\exporting-a-failed-hlk-job.md).

 

 






