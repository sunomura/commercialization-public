---
title: TargetFamily.QueueTest Method (IEnumerable Machine )
description: TargetFamily.QueueTest Method (IEnumerable Machine )
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b908dacc-4c6e-4d91-83c8-39870a7d0246
---

# TargetFamily.QueueTest Method (IEnumerable{Machine})


This method schedules a test to be run against a specified subset of machines.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overridable Function QueueTest ( _`

          `machineList As IEnumerable(Of Machine)) _`

`) As IList(Of TestResult)`

**C#**

`public virtual IList<TestResult> QueueTest (`

          `IEnumerable<Machine> machineList`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*machineList*

     The list of test computers on which a test should run.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **IList**, which is a list of results for the jobs that were scheduled.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






