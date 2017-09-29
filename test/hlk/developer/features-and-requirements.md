---
title: Features and Requirements
description: Features and Requirements
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 73eeb2c4-13b9-4606-938f-f64113ed407e
---

# Features and Requirements


A feature can be a property (for example, a kernel mode device driver), a bus, an interface, or capability (for example, a device that prints) of a target. **Feature** objects contain a list of requirements that are children of the **Feature**. Use the **TargetType** property to determine whether a feature applies toward a specific target.

A requirement (for example, "all PCI devices must do *x*") maps to only one feature. Tests are mapped against requirements, so if a feature is found, you must run all the corresponding tests for its requirements.

A feature can apply to only a subset of operating system versions or platforms. For example, a requirement might apply to only Windows® 7 x86, or to it might apply to Windows 8 (x86) and Windows 8 (x64) (but not Windows Server® 2012).

 

 






