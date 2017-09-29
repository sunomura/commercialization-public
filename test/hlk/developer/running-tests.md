---
title: Running Tests
description: Running Tests
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 51ca9ba0-097c-4b29-bc4d-3b90256c92ee
---

# Running Tests


Use the **QueueTest()** method to run all tests that are children of this object.

When you call **QueueTest()**, the Windows Hardware Lab Kit (Windows HLK) verifies these items:

-   The target is present.

-   The target computer is running the correct operating system.

-   The computer is in the correct machine pool and hasn't moved.

-   The target computer is in the "ready" or "running" state.

If any of the preceding checks fail, a **ScheduleException** occurs.

If the instance of **QueueTest()** is used for a test that takes a logical machine set and no logical machine set is used to schedule, a **ScheduleException** occurs. Similarly, if the logical machine set that is used is incompatible with the one that's required for a test, a **ScheduleConstraintException** occurs.

 

 






