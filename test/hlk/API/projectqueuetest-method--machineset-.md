---
title: Project.QueueTest Method (MachineSet)
description: Project.QueueTest Method (MachineSet)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: db95cd03-bb96-461e-b73e-6381728b5dbb
---

# Project.QueueTest Method (MachineSet)


This method schedules a test. This method schedules this object for to be run. The machine under test (the test computer) is always part of the machine set, this is only for additional test computers.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Project`

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

          `logicalMachineSet As MachineSet _`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*logicalMachineSet*

          The list of machines to run this on.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **IList**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The machine associated with the target (that was selected) is automatically added to the set.

QueueTest attempts to schedule all of the tests in the current or child objects. If a failure occurs, the scheduling is stopped immediately, and an exception is thrown. As a result, some of the tests might have been scheduled.

This method is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






