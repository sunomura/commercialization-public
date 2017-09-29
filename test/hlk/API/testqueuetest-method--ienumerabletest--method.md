---
title: Test.QueueTest Method (IEnumerable Test ) Method
description: Test.QueueTest Method (IEnumerable Test ) Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fb9650ff-f7b0-4c2d-b727-fa2d7be831a9
---

# Test.QueueTest Method (IEnumerable&lt;Test&gt;) Method


This method schedules tests to be run and consolidating the test run with additional compatible tests that are flagged to run as a set as an optimization

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overridable Function QueueTest(ByVal testList As IEnumerable(Of Test)) As IList(Of TestResult)`

**C#**

`This method schedules tests to be run and consolidating the test run with additional compatible tests that are flagged to run as a set as an optimization`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*testList*

     The list of tests to consolidate the test run with.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns IList, a list of results for the jobs that were scheduled.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown if:

-   The *ScheduleOptions* member of the test is not *ConsolidateScheduleAcrossTargets*.

-   The tests differ by their Id fields and are therefore not the same test running against different targets.

-   The tests validate different product instances.

-   All of the tests cannot run on a least one machine.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






