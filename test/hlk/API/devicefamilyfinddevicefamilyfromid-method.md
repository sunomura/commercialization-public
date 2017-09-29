---
title: DeviceFamily.FindDeviceFamilyFromId Method
description: DeviceFamily.FindDeviceFamilyFromId Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ecbafbaa-5978-4474-b8bb-52e84fc100fc
---

# DeviceFamily.FindDeviceFamilyFromId Method


This method retrieves a device family for the given hardware ID.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim idToFind As String`

`Dim manager As ProjectManager`

`Dim returnValue As DeviceFamily`

`returnValue = DeviceFamily.FindDeviceFamilyFromId(idToFind, manager)`

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


Returns **DeviceFamily**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs when the *idToFind* parameter or the *manager* parameter is **null** or the *idToFind* parameter is blank.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






