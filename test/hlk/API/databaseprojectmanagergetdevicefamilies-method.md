---
title: DatabaseProjectManager.GetDeviceFamilies Method
description: DatabaseProjectManager.GetDeviceFamilies Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f011f0af-2f6e-4711-a505-94cd4f0c791a
---

# DatabaseProjectManager.GetDeviceFamilies Method


This method retrieves a list of available DeviceFamilies.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DatabaseProjectManager`

`Dim returnValue As ReadOnlyCollection(Of DeviceFamily)`

`returnValue = instance.GetDeviceFamilies`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function GetDeviceFamilies As ReadOnlyCollection(Of DeviceFamily)`

**C#**

`public override ReadOnlyCollection<DeviceFamily> GetDeviceFamilies ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a read-only list of DeviceFamily names.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






