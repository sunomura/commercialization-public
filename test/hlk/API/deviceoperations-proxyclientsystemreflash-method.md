---
title: DeviceOperations.ProxyClientSystemReflash Method
description: DeviceOperations.ProxyClientSystemReflash Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 02769753-5B5C-4ECE-AC75-C4A187A618BA
---

# DeviceOperations.ProxyClientSystemReflash Method


Schedules re-flash on phone devices connected via proxy client.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public TestResult ProxyClientSystemReflash (`

          `string flashImagePath,`

          `out bool isScheduled`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*flashImagePath*

Absolute Path of the flash image path.

*isScheduled*

Marks the Re-flash Job is scheduled successfully.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


If isScheduled==true, a [TestResult](testresult-class.md) object is returned. If "isScheduled"==false, then null is returned.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






