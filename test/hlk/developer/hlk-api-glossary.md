---
title: HLK API Glossary
description: HLK API Glossary
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f7450369-e9ba-4a52-838a-6140d2793bd7
---

# HLK API Glossary


This section provides definitions of commonly used words or terms in the Windows Hardware Lab Kit (Windows HLK) API.

## <span id="c"></span><span id="C"></span>c


**certification content**

Certification content is the set of tests to run for each requirement (that is, the collection of tests, test binaries, media files, and anything else that's associated with a test) for certification.

## <span id="d"></span><span id="D"></span>d


**device ID**

The device ID is a string value that uniquely identifies a device on a specific computer.

## <span id="f"></span><span id="F"></span>f


**feature**

A feature is a property, interface, or implementation of a target.

For devices, a feature can be, for example, a device that's connected via USB, or one that has a kernel-mode driver, or one that exposes a network interface.

For systems, a feature can be the number and type of processors, whether it has Bluetooth connectivity, or whether it supports suspended states.

**feature set**

A feature set is the collection of features that a specific target exposes.

## <span id="h"></span><span id="H"></span>h


**hardware ID**

The hardware ID is a collection of string values that should provide the information to verify whether a driver should be loaded for a device.

## <span id="l"></span><span id="L"></span>l


**logical machine set**

A logical machine set (LMS) is a collection of computers where each computer is assigned a specific role. You use an LMS when you're scheduling a job that runs across several computers.

## <span id="p"></span><span id="P"></span>p


**platform**

A platform is represented by the **OSPlatform** class. **OSPlatform** defines the specific operating system and architecture of a computer, and whether a computer is a client or server.

**product**

A product consists of all the targets that you include in a certification submission.

## <span id="t"></span><span id="T"></span>t


**target**

A target is a device, driver (or filter driver), system, or object that you can query for properties by using the Windows HLK API. The **Target** class represents a single target. The **TargetFamily** class represents a group of test targets.

Each target is unique to the computer that it's on. It's assumed that the target will persist on its computer between reboots.

A typical certification submission has multiple targets that use instances of hardware from several platforms.

**target data**

The **TargetData** class is a dynamic representation of what's available on a computer, and it can't be tested. **TargetData** elements can change as hardware is added or removed from the test computer, or in response to system events, power management, load conditions, and other conditions.

**TargetData** is enumerated by the computer under test. **TargetData** can change as hardware is added or removed from the test computer.

You select a **TargetData** object to test, and that object is passed to the **TargetFamiley.CreateTarget(TargetData)** method to create a **Target** object.

**target ID**

The target ID is a string key that identifies a target on a computer. If the target is a **DevNode**, the target ID can be the device instance ID. For an application, the target ID can be a .msi GUID.

**test set**

A test set consists of one or more tests.

 

 






