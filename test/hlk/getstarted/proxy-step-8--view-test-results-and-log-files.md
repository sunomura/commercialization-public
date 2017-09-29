---
title: Step 8 View test results and log files
description: Step 8 View test results and log files
MS-HAID:
- 'p\_sxs\_hlk.step\_8\_\_view\_test\_results\_and\_log\_files'
- 'p\_sxs\_hlk.proxy\_step\_8\_\_view\_test\_results\_and\_log\_files'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 66CE72D2-E871-48A7-88B8-6A9386E2EE05
---

# Step 8: View test results and log files


The **Results** tab displays detailed information about each test. As each test completes, the status column updates with the result—pass or fail.

The following image shows the Studio **Results** tab.

![hlk studio results tab](images/hlk-studio-results-tab.png)

## <span id="To_troubleshoot_a_failed_test"></span><span id="to_troubleshoot_a_failed_test"></span><span id="TO_TROUBLESHOOT_A_FAILED_TEST"></span>To troubleshoot a failed test


If a test fails, you can expand the test details to review the associated log file.

1.  From the list, select a failed test, indicated by a red X.

2.  Expand the **Test Name** node, expand the **Logs** node, and then double-click the log file.

    You can review these log files:

    -   **.log file.** Text dump.

    -   **.wtl file.** Open to view error reports.

    -   **.xml file.** Change file name extension to .wtl to view error reports.

Right-click any test to see additional test details, including:

-   Task logs

-   Additional files

-   Applied filters

-   Errors

-   Infrastructure (gather and execution logs)

To learn more about the different options on this page including distributed and multi-device support, see [HLK Studio - Results Tab](..\user\hlk-studio---results-tab.md).

 

 






