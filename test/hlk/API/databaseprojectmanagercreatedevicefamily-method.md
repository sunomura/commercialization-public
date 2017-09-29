---
title: DatabaseProjectManager.CreateDeviceFamily Method
description: DatabaseProjectManager.CreateDeviceFamily Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 585b80c9-c21c-413b-a4f4-a7566531a62a
---

# DatabaseProjectManager.CreateDeviceFamily Method


This method creates a new device family with the given name.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DatabaseProjectManager`

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

     The ID values to use when creating the new device family.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns [DeviceFamily Class](devicefamily-class.md).

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs when the *familyIds* parameter is **null**, empty, or invalid.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






