---
title: Project.Info Property
description: Project.Info Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1141c155-6bd1-4c01-8b2f-79f04385f2c4
---

# Project.Info Property


This property retrieves project information.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Project`

`Dim value As ProjectInfo`

`value = instance.Info`

**C#**

`Project instance;`

`ProjectInfo value;`

`value = instance.Info;`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Property Info As ProjectInfo`

`Public MustOverride Get`

`Friend MustOverride Set(ByVal value As ProjectInfo)`

`End Property`

**C#**

`public abstract ProjectInfo Info { get; internal set; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **ProjectInfo**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






