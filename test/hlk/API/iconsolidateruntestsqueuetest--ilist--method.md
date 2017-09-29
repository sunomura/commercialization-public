---
title: IConsolidateRunTests.QueueTest (IList) Method
description: IConsolidateRunTests.QueueTest (IList) Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c1e410ee-fd1a-43a3-874a-22048df810aa
---

# IConsolidateRunTests.QueueTest (IList) Method


This method schedules all the tests for execution.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Function QueueTest(ByVal testList As IEnumerable(Of Test)) As IList(Of TestResult)`

**C#**

          `IList<TestResult> QueueTest(IEnumerable<Test> testList);`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*testList*

A list of tests to consolidate with the current test.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


A list of results for the tests that were scheduled.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


*QueueTest* will attempt to schedule all of the tests in the current or child objects. If there is a failure, the scheduling of tests is stopped immediately and the method returns. The function will leave some tests scheduled, and some that are incomplete. The list returned identifies the tests that were scheduled.

This is not supported when the project is connected to a package.

## <span id="Exception"></span><span id="exception"></span><span id="EXCEPTION"></span>Exception


*System.NotSupportedException* thrown when attempting to schedule tests when the data source connection is Submission or Update package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






