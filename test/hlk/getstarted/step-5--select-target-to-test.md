---
title: Step 5 Select target to test
description: Step 5 Select target to test
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 57C2D6C7-1578-41E2-80C5-ACCC409E1787
---

# Step 5: Select target to test


Windows HLK Studio detects all features that a device implements. An individually testable feature is called a *target*. A device may contain multiple targets, represented by one or more hardware IDs. On the **Selection** tab, you can filter what you want to test by using the following views:

-   **systems** - used to test a complete client or server system.

-   **devices and printers** - used to test an external device that's connected to a test system. This device typically appears in **Start** &gt; **Devices and Printers** on the test system.

-   **device manager** - used to test a component of a test system or external device, for example, a network card. This is the most detailed view.

-   **software device** - used to test filter drivers, firewalls, and antivirus software installed on the test system.

    >[!NOTE]
    >  Some software drivers are associated with a physical device. If you cannot find your driver listed in the **software device** view, use the search bar in the **device manager** view to find the device under which your software driver is associated.

     

The following image shows the Studio **Selection** tab.

![hlk studio selection tab](images/hlk-studio-selection-tab.png)

## <span id="Select_a_target_to_test"></span><span id="select_a_target_to_test"></span><span id="SELECT_A_TARGET_TO_TEST"></span>Select a target to test


1.  In Windows HLK Studio, choose the **Selection** tab. In the machine pool dropdown, choose the pool that contains the devices that you want to test.

2.  In the left pane, select the view based on the device you want to test: **systems, device and printers, device manager,** or **software device**.

    A list of available targets is displayed in the center pane. If you select the **device manager** view, you can choose to show inbox and hidden features.

3.  In the center pane, check the box next to each target that you want to test.

    >[!NOTE]
    >  You must select all of the features of a specific product type for a device to receive certification.

    >[!NOTE]
    >  If you're testing a Web Services on Devices (WSD) device, there may be a delay before the required WSD targets are listed.

     

The **show selected** view in the left pane displays the targets that you've selected across all views. This view allows you to see just the areas you're testing. You also can filter a machine pool by category by using the **category** list. You can search for specific targets and features by using the search box.

To learn more about the different options on this page see [HLK Studio - Selection Tab](..\user\hlk-studio---selection-tab.md).

 

 






