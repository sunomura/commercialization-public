---
title: PackageManager.GetPlatforms Method
description: PackageManager.GetPlatforms Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e75402e9-ccd7-44ea-9bcd-2da0b92ac96c
---

# PackageManager.GetPlatforms Method


Gets a collection of all platforms.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

` public override ReadOnlyCollection<OSPlatform> GetPlatforms()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns an empty collection; the Project Manager object is not connected to a Database.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Getting OS Platform objects is supported only when the Project Manager object is connected to a Database.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






