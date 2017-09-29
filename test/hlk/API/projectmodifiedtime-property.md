---
title: Project.ModifiedTime Property
description: Project.ModifiedTime Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: be5e7e8e-3eb6-413d-9a0e-8e74f222ae72
---

# Project.ModifiedTime Property


This property retrieves the last time that the project was modified.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Project`

`Dim value As DateTime = instance.ModifiedTime`

**C#**

`Project instance;`

`DateTime value = instance.ModifiedTime;`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Property ModifiedTime As DateTime`

`Public MustOverride Get`

`Friend MustOverride Set(ByVal value As DateTime)`

`End Property`

**C#**

`public abstract DateTime ModifiedTime { get; internal set; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **DateTime**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






