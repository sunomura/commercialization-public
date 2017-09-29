---
title: Machines and Machine Pools
description: Machines and Machine Pools
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 26483970-2bc8-4dcf-8967-537fe652d904
---

# Machines and Machine Pools


The **Machine** class represents a computer that can be used for testing and that contains devices to be tested. Computer properties represent Windows® Test Technology (WTT) dimensions. Dimensions can be added, removed, or reset based on the underlying WTT behavior.

The **Machine.Status** property indicates whether a computer is available for testing and if it's currently running tests.

The **MachinePool** class represents a logical grouping of zero or more computers, and it represents WTT **ResourcePool** objects that WTT uses natively for scheduling and testing. Machine pools are hierarchical (that is, a machine pool can have child machine pools). A machine pool doesn't represent any physical computers.

>[!NOTE]
>  
The **ProductInstance.MachinePool** property is **null** for product instances loaded via Package Manager (.

 

These common machine pools are in every controller:

-   Root ($), which contains all other machine pools. The root doesn't contain individual computers, it can't run jobs, and it has no special properties. Use the **RootPool** property to access the root machine pool.

-   System, which contains all controller components and is hidden. System is a reserved name.

-   Default, which newly detected computers are automatically added to. Computers in machine pools that are marked for deletion are moved to the default machine pool. Computers in the default machine pool can't be used or change status.

When you delete a machine pool, the deletion operates recursively. All computers in the affected pool are moved to the default pool. Deleting a machine pool doesn't affect results or logs. When you delete a computer, all corresponding test results and history are deleted, and logs are orphaned.

 

 






