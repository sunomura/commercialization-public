---
title: PackageManager.CreateDeviceFamily Method
description: PackageManager.CreateDeviceFamily Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8aeea09c-8a79-4b13-8250-8061f6f3f62b
---

# PackageManager.CreateDeviceFamily Method


This method creates a new device family with the given name.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageManager`

`Dim name As String`

`Dim familyIds As IEnumerable(Of String)`

`Dim returnValue As DeviceFamily`

`returnValue = instance.CreateDeviceFamily(name, familyIds)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function CreateDeviceFamily ( _`

          `name As String, _`

          `familyIds As IEnumerable(Of String) _`

`) As DeviceFamily`

**C#**

`public override DeviceFamily CreateDeviceFamily (`

          `string name,`

          `IEnumerable<string> familyIds`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*name*

     The name to create the device family with.

*familyIds*

     The list of ID values to use for the device family.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns a [DeviceFamily Class](devicefamily-class.md).

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






