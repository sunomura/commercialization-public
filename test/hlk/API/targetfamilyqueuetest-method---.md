---
title: TargetFamily.QueueTest Method ()
description: TargetFamily.QueueTest Method ()
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7ff43fe9-8f50-4c13-bc13-e57b84b6df5e
---

# TargetFamily.QueueTest Method ()


This method schedules this object to run.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TargetFamily`

`Dim returnValue As IList(Of TestResult)`

`returnValue = instance.QueueTest`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overridable Function QueueTest As IList(Of TestResult)`

**C#**

`public virtual IList<TestResult> QueueTest ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **IList**, which is a list of results for the jobs that were scheduled.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


QueueTest attempts to schedule all of the tests in the current or child objects. If there is a failure, the scheduling of tests is stopped immediately and the method returns. The function will leave some tests scheduled and some that are incomplete. The returned list identifies the tests that were scheduled.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






