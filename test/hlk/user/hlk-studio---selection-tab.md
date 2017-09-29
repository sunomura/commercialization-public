---
title: HLK Studio - Selection Tab
description: HLK Studio - Selection Tab
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 467720D9-134B-4990-833B-38DEBEA374E7
---

# HLK Studio - Selection Tab


![hlk studio selection tab](images/p-hlk-studio-selection-tab.png)

The **Selection** tab displays all features that a device implements. Before you can see any features, you must first select a machine pool (drop-down list in the upper left corner). You can also search for specific features using the combination search drop-down list and search field.

The specific testable device is called the *target*. A device may contain multiple targets, represented by one or more hardware IDs. You can filter what you want to test by:

-   **show selected** - this option displays the targets that you’ve selected. This view allows you to see just the areas you're testing. You also can filter a machine pool by category by using the **category** list. You can search for specific targets/features by using the search box.

-   **systems** - test a complete client or server computer.

-   **devices and printers** - test an external device that's connected to a test computer. This device typically appears in **Start** &gt; **Devices and Printers** on the test computer. This usually represents a collection of devices found on the Device Manager tab.

-   **device manager** - test a component of a test computer or external device, for example, a network card. This is the most detailed view.

-   **software device** - test filter drivers, firewalls, and antivirus software that's installed on the test computer.

    >[!NOTE]
    >  
    Some software drivers are associated with a physical device. If you cannot find your driver under **software device**, use the search bar on **device manager** to find the device under which your software driver is associated.

     

On this tab, you can do the following tasks:

-   [Select targets to test](..\getstarted\step-5--select-target-to-test.md)

-   [Select targets for distributed testing](select-targets-for-distributed-testing.md)

-   [Manually add features](manually-add-features.md)

 

 






