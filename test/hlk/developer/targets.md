---
title: Targets
description: Targets
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 40aa7343-693f-432d-8611-129f8134c99f
---

# Targets


Any object that you can test by using the Windows Hardware Lab Kit (Windows HLK) is a *target*. Most devices have several hardware ID components (that is, targets) that must be tested. You can query any target for its properties. Targets can be any of these:

-   Devices (for example, a mouse or keyboard)

-   Systems (that is, a computer that you test as a unit)

-   Filter drivers (for example, antivirus drivers)

A typical certification submission has multiple targets that use hardware on several platforms.

A test target can provide data about how to run a test by dynamically resolving test parameters based on target data. So if a test must identify a device ID, that device ID can be resolved and specified when you schedule a test.

Each target has an associated .xml file. This data file is the collection of all applicable gatherer data for that target. It's used for detecting features, running tests, and reporting.

You can specify some tests to run on one target in a **TargetFamily** object. Other tests must run on each target in a **TargetFamily**.

 

 






