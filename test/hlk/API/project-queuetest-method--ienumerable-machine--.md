---
title: Project.QueueTest Method (IEnumerable Machine )
description: Project.QueueTest Method (IEnumerable Machine )
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 65C90CD1-858E-4917-8A49-E67DAA5DE557
---

# Project.QueueTest Method (IEnumerable{Machine})


This method schedules the test for execution on a specific subset of machines.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public virtual IList<TestResult> QueueTest (`

          `IEnumerable<Machine> machineList`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*machineList*

List of machines that can run the test.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is useful to specify a subset of possible machines. For example in the case where manual tests would prefer to run on specific machines.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






