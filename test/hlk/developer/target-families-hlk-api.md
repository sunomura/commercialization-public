---
title: Target Families
description: Target Families
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: bf92a08d-1593-4838-9090-06d104601bae
---

# Target Families


A **TargetFamily** is a collection of targets on different computers where:

-   Each target's hardware ID matches an entry in the **DeviceFamily**.

-   The parent computer is in a common **ProductInstance**.

For example, if you're testing a mouse on several computers, a **TargetFamily** can represent all the common hardware IDs for a device node (devnode), one on each computer. You can use this representation to run many parallel tests on hardware collections.

It's important to note the difference between **TargetFamily** and **ProductInstance**. **ProductInstance** is a collection of dissimilar targets that are sold in one box to a customer. **TargetFamily** is a collection of hardware that (for testing) can be treated identically.

Not all the features that are found on one instance of a **Target** in a **TargetFamily** are available on all instances of targets within that **TargetFamily**.

The **TargetFamiley.GetTests()** method gets a list of all the tests that are required for a **TargetFamily**, but not all the features that are found on a **Target** will be found on all targets. For this reason, the **TargetFamily.GetFeatures()** method returns a list of all features that are found on any **Target**.

 

 






