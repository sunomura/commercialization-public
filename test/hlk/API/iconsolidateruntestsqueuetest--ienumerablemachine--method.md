---
title: IConsolidateRunTests.QueueTest (IEnumerable Machine ) Method
description: IConsolidateRunTests.QueueTest (IEnumerable Machine ) Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 707a4bc8-cd08-4e6f-8de3-f84e02422fdf
---

# IConsolidateRunTests.QueueTest (IEnumerable&lt;Machine&gt;) Method


This method schedules the test for execution on a specific subset of machines.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Function QueueTest(ByVal testList As IEnumerable(Of Test), ByVal machineList As IEnumerable(Of Machine)) As IList(Of TestResult)`

**C#**

          `IList<TestResult> QueueTest(IEnumerable<Test> testList, IEnumerable<Machine> machineList);`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*testList*

A list of tests to consolidate with the current test.

*machinelist*

List of machines that can run the test.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


A list of results for the tests that were scheduled.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is useful to specify a subset of possible machines. For example in the case where manual tests would prefer to run on specific machines

This is not supported when the project is connected to a package.

## <span id="Exception"></span><span id="exception"></span><span id="EXCEPTION"></span>Exception


*ScheduleException* thrown when there is a failure submitting a test to the scheduler.

*NotSupportedException* thrown when attempting to queue tests when the data source connection is Submission or Update package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






