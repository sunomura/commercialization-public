---
title: TargetFamily.SetCommonParameters Method
description: TargetFamily.SetCommonParameters Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 90ffd1dd-81ae-4ad4-95a5-da1b9da77235
---

# TargetFamily.SetCommonParameters Method


This method sets all of the parameters with a given name to the same value for all child jobs.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TargetFamily`

`Dim parameterName As String`

`Dim  parameterValue As String`

`instance.SetCommonParameters(parameterName, parameterValue)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub SetCommonParameters ( _`

          `parameterName As String, _`

          `parameterValue As String, _`

`) `

**C#**

`public void SetCommonParameters (`

          `string parameterName,`

          `string parameterValue,`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*parameterName*

     The name (string) of the parameter to set.

*parameterValue*

     The value to set the parameter to.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Setting a parameter value to empty is supported.

Setting a value to null is not supported.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






