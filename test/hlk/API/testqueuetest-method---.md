---
title: Test.QueueTest Method ()
description: Test.QueueTest Method ()
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6ac5c87a-2d72-44d1-8e2a-edd124c62695
---

# Test.QueueTest Method ()


This method schedules this object for execution.

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

`Dim returnValue As IList(Of TestResult)`

`returnValue = instance.QueueTest`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overridable Function QueueTest As IList(Of TestResult)`

**C#**

`public virtual IList<TestResult> QueueTest ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **IList**, which is a list of results for the jobs that were scheduled.

>[!TIP]
>  
If you use the **QueueTest** method to add a computer to a test queue and that computer configuration subsequently changes, **QueueTest** can throw an exception. If an exception occurs, immediately retry **QueueTest**.

 

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






