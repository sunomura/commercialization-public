---
title: IFilterConstraintEvaluator.IsMatch Method
description: IFilterConstraintEvaluator.IsMatch Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 256d05d4-5946-4fcf-baed-7046902f6654
---

# IFilterConstraintEvaluator.IsMatch Method


This method evaluates a filter constraint and returns **true** if the constraint matches.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IFilterConstraintEvaluator`

`Dim constraint As IFilterConstraint`

`Dim returnValue As Boolean`

`returnValue = instance.IsMatch(constraint)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Function IsMatch ( _`

          `constraint As IFilterConstraint _`

`) As Boolean`

**C#**

`bool IsMatch (`

          `IFilterConstraint constraint`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*constraint*

     The filter constraint to match.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the constraint matches; otherwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






