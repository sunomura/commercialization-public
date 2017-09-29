---
title: Target Class
description: Target Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 747b3961-22b2-4722-8588-d2af1b98a71f
---

# Target Class


This class represents a single test target that can be detected on a system (a piece of hardware, a driver, and so on).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Target`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataContractAttribute> _`

`Public MustInherit Class Target`

          `Implements ITargetInformation`

**C#**

`[DataContractAttribute]`

`public abstract class Target : ITargetInformation`

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


A Target contains information that is in XML format. Features have an XPATH query that can return specific nodes from the XML data. All Feature objects in the system are detected for the Target. Since a Feature object is associated with Requirement objects which are associated with Test objects, you can generate a test list.

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

     **Microsoft.Windows.Kits.Hardware.ObjectModel.Target**

          **Microsoft.Windows.Kits.Hardware.ObjectModel.Submission.PackageTarget**

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






