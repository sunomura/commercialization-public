---
title: PackageFilter.IsApplicable Method
description: PackageFilter.IsApplicable Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 48c18e95-0fcf-477c-96b7-5c41edaad608
---

# PackageFilter.IsApplicable Method


This method determines whether the filter is applicable for the given taskResult.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageFilter`

`Dim constraintEvaluator As IFilterConstraintEvaluator`

`Dim returnValue As Boolean`

`returnValue = instance.IsApplicable(constraintEvaluator)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function IsApplicable ( _`

          `constraintEvaluator As IFilterConstraintEvaluator`

`) As Boolean`

**C#**

`public bool IsApplicable (`

          `IFilterConstraintEvaluator constraintEvaluator`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*constraintEvaluator*

     The filter constraint evaluator.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if applicable; otherwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






