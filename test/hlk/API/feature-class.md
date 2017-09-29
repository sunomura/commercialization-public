---
title: Feature Class
description: Feature Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 68ba9f55-2dbf-4982-b9a1-13be9bfb3223
---

# Feature Class


This class represents a feature that a device supports. For example, USB support is an example of a feature.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Feature`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<SerializableAttribute> _`

`Public MustInherit Class Feature`

**C#**

`[SerializableAttribute]`

`public abstract class Feature`

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

    **Microsoft.Windows.Kits.Hardware.ObjectModel.Feature**

        

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Features are related to Product Types and Requirements. Features can be mapped to different Product Types. Requirements can be mapped to only one Feature.

 

 






