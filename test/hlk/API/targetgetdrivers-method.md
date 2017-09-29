---
title: Target.GetDrivers Method
description: Target.GetDrivers Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d24bd0f1-8657-4a57-a736-df0c7c74348f
---

# Target.GetDrivers Method


Gets a list of drivers.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

` public abstract IEnumerable<Driver> GetDrivers()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns a list of drivers associated with this target.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This function will return drivers only when connected to a package. If not connected to a package, an empty list is returned.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






