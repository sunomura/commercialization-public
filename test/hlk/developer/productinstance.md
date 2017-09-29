---
title: ProductInstance
description: ProductInstance
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: E3CA8B39-C7A4-417F-AE3F-5482F2284881
---

# ProductInstance


The **ProductInstance** class is a specific example of a product on a specific **OSPlatform**. Note that you can test multiple versions of a product type on multiple computers. However, each platform (that is, the combination of operating system and architecture) must be tested individually, in parallel with the other instances. Unlike the **DeviceFamily** and **TargetFamily** classes, **ProductInstance** is a collection of dissimilar devices, whereas **TargetFamily** is a collection of essentially identical devices.

Using the example of a printer, there would be a separate **ProductInstance** class for each printer for every **OSPlatform**. Each **ProductInstance** class might have a printer **Target** or **TargetFamily** class as a child, in addition to a scanner target and a memory card reader target.

Each **ProductInstance** class is named. The **Name** value must be unique to each project. Unlike a project, you can't rename a **ProductInstance** class. Each **ProductInstance** class is associated with a specific **MachinePool**. This **MachinePool** can be shared with other **ProductInstance** classes.

**ProductInstance** has several **FindTargetFrom\*** methods. Each method searches across computers in a machine pool and returns **TargetData** for each target that meets the filter criteria. The caller must verify that all the targets that it meant to return are returned.

**TargetData** is an abstract target (that is, it's what can be tested). **Target** is what you test. You select a **TargetData** object by using one of the **FindTarget\*** methods, and then call **CreateTarget()** to promote that **TargetData** to a **Target** class for testing.

 

 






