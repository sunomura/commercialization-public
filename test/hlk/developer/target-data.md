---
title: Target Data
description: Target Data
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dd2d9d8e-4f47-4be7-be5b-33b69eccabf3
---

# Target Data


Both the **Target** object and the **TargetData** object represent an instance of a test target on a computer. Both are based on **Sysparse** data for the computer. However, **TargetData** is a dynamic representation of what's available on a computer at a particular time. **TargetData** elements can appear or disappear in response to system events, power management, load conditions, and other conditions.

After you select a **TargetData** object for testing, its data is copied to the **Target** list and a new object is created.

The read-only **Target.XmlData** property is used both for parameter resolution and feature detection. It contains the raw correlator data that has been returned for a device, and it's used for feature detection and parameter resolution during testing.

The required **Target.Name** property is a string that's used to identify the target to the user.

 

 






