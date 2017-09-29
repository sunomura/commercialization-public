---
title: ProductInstance.SetCommonParameters Method
description: ProductInstance.SetCommonParameters Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5adf5de4-2202-44c3-bac4-dc5296316896
---

# ProductInstance.SetCommonParameters Method


This method sets all of the parameters with a given name to the same value for all child jobs

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

`Dim parameterName As String`

`Dim parameterValue As String`

`instance.SetCommonParameters(parameterName, parameterValue)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub SetCommonParameters ( _`

          `parameterName As String, _`

          `parameterValue As String _`

`) `

**C#**

`public void SetCommonParameters (`

          `string parameterName,`

          `string parameterValue`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*parameterName*

     The name of the parameter to set.

*parameterValue*

     The value to set the parameter to set it to.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs if the *parameterName* or *parameterValue* value is **null**, not valid, or empty.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






