---
title: PackageManager.GetDeviceFamilies Method
description: PackageManager.GetDeviceFamilies Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: bb3b4832-1693-49d2-8a85-505f2d9fc472
---

# PackageManager.GetDeviceFamilies Method


This method retrieves a list of all of the device families used in this submission package.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageManager`

`Dim returnValue As ReadOnlyCollection(Of DeviceFamily)`

`returnValue = instance.GetDeviceFamilies`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function GetDeviceFamilies As ReadOnlyCollection(Of DeviceFamily)`

**C#**

`public override ReadOnlyCollection<DeviceFamily> GetDeviceFamilies ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






