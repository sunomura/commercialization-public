---
title: DeviceFamily.GetDeviceFamilyFromId Method
description: DeviceFamily.GetDeviceFamilyFromId Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e1dffa37-597f-41e5-add5-d9ff7b124372
---

# DeviceFamily.GetDeviceFamilyFromId Method


This method gets a device family for the given hardware ID.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim idToFind As String`

`Dim manager As ProjectManager`

`Dim returnValue As DeviceFamily`

`returnValue = DeviceFamily.GetDeviceFamilyFromId(idToFind, manager)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Shared Function FindDeviceFamilyFromId ( _`

          `idToFind As String, _`

          `manager As ProjectManager _`

`) As DeviceFamily`

**C#**

`public static DeviceFamily FindDeviceFamilyFromId (`

          `string idToFind,`

          `ProjectManager manager`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*idToFind*

     The hardware ID to use to compare against.

*manager*

     The logoManager object against which to perform the search.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **DeviceFamily**, which is the **DeviceFamily** object, or **null** if no **DeviceFamily** object is associated with the *idToFind* parameter.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This function throws an exception if the correct device family could not be found. This can occur under the following conditions:

-   The *idToFind* parameter or the manager parameter is **null**

-   The *idToFind* parameter is blank.

-   The *idToFind* parameter is not associated with a **DeviceFamily** object.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






