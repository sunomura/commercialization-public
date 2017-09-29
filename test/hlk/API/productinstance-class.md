---
title: ProductInstance Class
description: ProductInstance Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 489c6fb3-d0d4-499e-b056-73342bbd5bbc
---

# ProductInstance Class


This class represents a piece of hardware that has been detected on a test computer and identified by set of targets.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataContractAttribute> _`

`Public MustInherit Class ProductInstance`

          `Implements IRunTests`

**C#**

`[DataContractAttribute]`

`public abstract class ProductInstance : IRunTests`

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

     **Microsoft.Windows.Kits.Hardware.ObjectModel.NotificationBase**

          **Microsoft.Windows.Kits.Hardware.ObjectModel.ProductInstance**

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






