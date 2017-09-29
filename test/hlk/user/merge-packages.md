---
title: Merge packages
description: Merge packages
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7a712c2e-5725-42fa-87d1-c4f34e883db7
---

# Merge packages


HLK Studio supports merging packages into a single package. This feature gives you the flexibility to distribute your tests across different projects, machine pools, and/or other HLK environments (other controllers).

For example, you want to create one submission for a system, filter, or device that applies to multiple versions of Windows and associated architectures. You can independently test against each version of Windows and later merge the packages into one submission package.

You can also test portions of a single-product (at the target family level) across different projects and later merge the packages into a single submission package. This concept of distributed feature and component testing is ideal for components that are expensive to setup and run. This is known as a deep merge. This merge support has the following limitations:

-   The targets must be for the same operating system and architecture.
-   The targets must be the same type (that is, System or Device).
-   You cannot deep merge software filter types.
-   The distinct set of features for all targets under a target family must match the distinct set of features in the target family from the merged package.
-   All distinct set of tests for all targets under a target family must match the distinct set of tests in the target family from the merged package.
-   (For device target types): the set of drivers must match.
-   (For device target types): the set of hardware Ids must match. (Note: this means that device families are not taken into consideration when matching hardware Ids)
-   When deep merging two packages, tests that are categorized as playlist tests in at least one package will also be categorized as playlist tests in the merged package.

When you open a package with an applied playlist in HLK Studio, only the playlist tests are shown in the UI.

>[!NOTE]
>  
To guarantee that none of the tests are missed, we recommend that you create a package for the source project before you divide testing into separate projects. This package does not necessarily hold any test results; its purpose is to hold all required tests for all family targets. Later, this package can be merged with other packages into a single submission package. In this way, the submission package holds all required tests, regardless of whether the test has been executed.

 

**Merging .hlkx packages**

1.  Open an existing project or package.

2.  Click the **Package** tab, and then click **Merge Package**.

3.  Click **Add** and, in the Open dialog box, select an .hlkx package that you want to merge.

    >[!NOTE]
    >  
    If you accidentally selected the wrong package, select the package in the data grid and click **Remove**.

    Packages that were previously selected and saved (by clicking **OK** in the dialog box) can only be removed by clicking **Reset** on the main **Package** tab. These packages have a lock icon next to them.

     

4.  Repeat **Steps 3** and **4** for each additional package that you want to merge. Note the **Open** dialog supports the selection of multiple packages at a time.

5.  Click **OK** to save your changes or **Cancel** to undo.

6.  Click **Create Package**.

## <span id="Merging_HLK_and_HCK_Packages"></span><span id="merging_hlk_and_hck_packages"></span><span id="MERGING_HLK_AND_HCK_PACKAGES"></span>Merging HLK and HCK Packages


HLK and HCK packages can be merged from the HLK OM or HLK Studio. When merging, ensure that the HLK package is opened first, and the HCK package(s) are merged into the HLK package.

 

 






