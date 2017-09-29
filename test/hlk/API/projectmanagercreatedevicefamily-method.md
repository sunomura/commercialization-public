---
title: ProjectManager.CreateDeviceFamily Method
description: ProjectManager.CreateDeviceFamily Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7299ff08-5c17-464f-be91-7a0f4fd59fc4
---

# ProjectManager.CreateDeviceFamily Method


This method creates a new device family with the given name.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProjectManager`

`Dim name As String`

`Dim familyIds As IEnumerable(Of String)`

`Dim returnValue As DeviceFamily`

`returnValue = instance.CreateDeviceFamily(name, familyIds)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function CreateDeviceFamily ( _`

          `name As String, _`

          `familyIds As IEnumerable(Of String) _`

          `platform As OSPlatform _`

`) As DeviceFamily`

**C#**

`public abstract DeviceFamily CreateDeviceFamily (`

          `string name,`

          `IEnumerable<string> familyIds`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*name*

     The name to create the device family with.

*familyIds*

     The Ids to use when creating the device family.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns a [DeviceFamily Class](devicefamily-class.md)

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






