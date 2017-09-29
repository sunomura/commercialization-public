---
title: IParameterResolverManager.ResolveParameter Method
description: IParameterResolverManager.ResolveParameter Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6121589b-43bf-4a6b-84a7-a7f21bebee5e
---

# IParameterResolverManager.ResolveParameter Method


This method resolves the parameter string.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IParameterResolverManager`

`Dim inputValue As String`

`Dim returnValue As String`

`returnValue = instance.ResolveParameter(inputValue)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Function ResolveParameter ( _`

          `inputValue As String _`

`) As String`

**C#**

`string ResolveParameter (`

          `string inputValue`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*inputValue*

     The input string to search for.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **String**, which is the final result of the parameter resolution process.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






