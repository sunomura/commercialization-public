---
title: IRunTests.QueueTest Method (IEnumerable Machine )
description: IRunTests.QueueTest Method (IEnumerable Machine )
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f261d3b3-edcb-4c5e-a4b5-0ad35182d039
---

# IRunTests.QueueTest Method (IEnumerable{Machine})


This method schedules the test for execution on a specific subset of machines.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Function QueueTest( _`

          `ByVal machineList As IEnumerable(Of Machine) _`

`) As IList(Of TestResult)`

**C#**

`IList<TestResult> QueueTest (`

          `IEnumerable<Machine> machineList`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*machineList*

     The list of machines on which to run the test.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **IList**, which is a list of results for the tests that were scheduled.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






