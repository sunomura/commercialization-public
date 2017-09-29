---
title: IFilter.IsApplicable Method
description: IFilter.IsApplicable Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3f21e2df-bf39-4e44-b250-2616c2cca5fc
---

# IFilter.IsApplicable Method


This method determines whether the filter is applicable for the given taskResult.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IFilter`

`Dim constraintEvaluator As IFilterConstraintEvaluator`

`Dim returnValue As Boolean`

`returnValue = instance.IsApplicable(constraintEvaluator)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Function IsApplicable ( _`

          `constraintEvaluator As IFilterConstraintEvaluator _`

`) As Boolean`

**C#**

`bool IsApplicable (`

          `IFilterConstraintEvaluator constraintEvaluator`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*constraintEvaluator*

     The filter constraint evaluator.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the filter is applicable; othwerwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






