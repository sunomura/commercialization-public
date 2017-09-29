---
title: Select targets for distributed testing
description: Select targets for distributed testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a6b210df-8833-470c-8d75-cbe86974890d
---

# Select targets for distributed testing


By default, the HLK tries to enable distributed testing by combining similar, selected targets. This is accomplished by matching similar targets under the same target family.

When two or more targets are considered similar, the set of tests for all the targets is reduced by removing duplicate distributable tests. Tests that are marked as non-distributable must be run on each target.

Targets that are in the same target family (distributed) have the notation **\[Group – XX\]** in the machine column. Targets that are in their own target family (non-distributed) have the machine name where the target was located.

The rules for determining whether two targets are similar include:

-   Target type must match

-   Target platform must match

-   Targets must be in the same machine pool

-   Targets cannot be from the same machine

-   Targets must have the same hardware Id or be in the same device family. See **Device Families** for more information

-   Drivers must match

>[!NOTE]
>  
When there are multiple secondary matched targets on the same system, the target check box activation is retained from the previously displayed dialog for the same targets. This causes secondary targets to be grayed out. You can activate the grayed-out secondary targets by selecting and then de-selecting the checkbox for these targets.

 

## <span id="related_topics"></span>Related topics


[Configuration Page - Distributed and Multi-Device Options](configuration-page---distributed-and-multi-device-options.md)

 

 







