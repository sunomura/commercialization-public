---
title: TargetFamily.QueueTest Method (MachineSet)
description: TargetFamily.QueueTest Method (MachineSet)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6f068e2e-aaca-442e-94ad-e90fb8dd00b1
---

# TargetFamily.QueueTest Method (MachineSet)


This method schedules a test to be run against a target family. The test computer is always part of the machine set, this is only for additional test computers.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TargetFamily`

`Dim logicalMachineSet As MachineSet`

`Dim returnValue As IList(Of TestResult)`

`returnValue = instance.QueueTest(logicalMachineSet)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overridable Function QueueTest ( _`

          `logicalMachineSet As MachineSet _`

`) As IList(Of TestResult)`

**C#**

`public virtual IList<TestResult> QueueTest (`

          `MachineSet logicalMachineSet`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*logicalMachineSet*

     The list of test computers on which a test should run.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **IList**, which is a list of results for the jobs that were scheduled.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The machine associated with the selected target is automatically added to the set.

QueueTest will attempt to schedule all of the tests in the current or child objects. If there is a failure, the scheduling of tests is stopped immediatelyand an exception is thrown. As a result, some tests could be scheduled, while others are not.

This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






