---
title: Test.ExecutionState Property
description: Test.ExecutionState Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 87a87b01-248d-48e1-acd8-840e06f82422
---

# Test.ExecutionState Property


Indicates whether there is an instance of this test that is queued, waiting to be run, or not running.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public virtual ExecutionState ExecutionState`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns an [ExecutionState Enumeration](executionstate-enumeration.md).

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


If there is an instance of this test running, and another in the queue, this will return ExecutionState.Running.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






