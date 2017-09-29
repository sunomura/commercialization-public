---
title: IProxyRunTests.QueueTest Method (IEnumerable Test , IEnumerable Machine , TemplateParameters)
description: IProxyRunTests.QueueTest Method (IEnumerable Test , IEnumerable Machine , TemplateParameters)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 045B3D8E-3F73-4808-B7FB-F717816FF3BA
---

# IProxyRunTests.QueueTest Method (IEnumerable{Test}, IEnumerable{Machine}, TemplateParameters)


This method schedules the test for execution on a specific subset of machines.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

` IList<TestResult> QueueTest (`

          `IEnumerable<Test> testList,`

          `IEnumerable<Machine> machineList,`

          `TemplateParameters templateParameters`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*testList*

A list of tests to consolidate with the current test.

*machineList*

List of machines that can run the test.

*templateParameters*

Template parameters to use for running tests on a Proxy Client.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


*IList&lt;TestResult&gt;*

A list of results for the tests that were scheduled.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is useful to specify a subset of possible machines. For example in the case where manual tests would prefer to run on specific machines.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






