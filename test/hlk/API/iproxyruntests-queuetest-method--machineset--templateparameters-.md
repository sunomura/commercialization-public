---
title: IProxyRunTests.QueueTest Method (MachineSet, TemplateParameters)
description: IProxyRunTests.QueueTest Method (MachineSet, TemplateParameters)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3D74BDE9-DE3E-4CFC-92D2-2549201A4D08
---

# IProxyRunTests.QueueTest Method (MachineSet, TemplateParameters)


This method schedules all the tests for execution on a specified [MachineSet](machineset-class.md).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

` IList<TestResult> QueueTest (`

          `MachineSet logicalMachineSet,`

          `TemplateParameters templateParameters`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*logicalMachineSet*

Machine set to run the tests.

*templateParameters*

Template parameters to use for running tests on a Proxy Client.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


*IList&lt;TestResult&gt;*

A list of results for the tests that were scheduled.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The machine associated with the target (that was selected) is automatically added to the set.

QueueTest will attempt to schedule all of the tests in the current or child objects. If there is a failure, the scheduling of tests is stopped immediately and an exception is thrown. As a result, some tests could have been scheduled.

This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






