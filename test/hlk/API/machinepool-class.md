---
title: MachinePool Class
description: MachinePool Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ab4de372-c215-409f-bd14-1fa9b4ce7074
---

# MachinePool Class


This class represents an abstract pool of machines that are grouped together based on a user intention. It exposes functionality that enables machines to be regrouped among different machine pools and manage the resource pool hierarchy.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachinePool`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustInherit Class MachinePool`

**C#**

`public abstract class MachinePool`

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

     **Microsoft.Windows.Kits.Hardware.ObjectModel.MachinePool**

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


There are certain reserved or special Machine Pools that have specific purposes:

1.  Default Pool - any machine that has the Client side software installed initially appears in this pool. Tests cannot be executed on any machine in this pool.

2.  $ (Root Pool) - is the root machine pool. The root pool can be accessed through the ProjectManager object. Machines cannot be added or moved to this pool.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






