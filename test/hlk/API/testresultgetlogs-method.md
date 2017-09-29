---
title: TestResult.GetLogs Method
description: TestResult.GetLogs Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 27759314-3d40-48aa-a132-571dd4f02de9
---

# TestResult.GetLogs Method


This method retrieves all of the logs associated with this test result.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TestResult`

`Dim returnValue As ReadOnlyCollection(Of TestLog)`

`returnValue = instance.GetLogs`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetLogs As ReadOnlyCollection(Of TestLog)`

**C#**

`public abstract ReadOnlyCollection<TestLog> GetLogs ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a read-only list of all of the logs associated with this test result.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






