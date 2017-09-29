---
title: IParameterResolver.ResolveParameter Method
description: IParameterResolver.ResolveParameter Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cc649476-a693-45f5-8dac-b919bb6b581f
---

# IParameterResolver.ResolveParameter Method


This method is called by the scheduler to resolve a parameter that should be resolved externally.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IParameterResolver`

`Dim inValue As String`

`Dim outValue As String`

`Dim returnValue As Boolean`

`returnValue = instance.ResolveParameter(inValue, outValue)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Function ResolveParameter ( _`

          `inValue As String, _`

          `ByRef outValue As String _`

`) As Boolean`

**C#**

`bool ResolveParameter (`

          `string inValue,`

          `ref string outValue`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*inValue*

     The resolver value to replace.

*outValue*

     The new value of the parameter. If the method returns **true**, this will be the new value.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns Boolean, which has a value of **true** if the parameter SHOULD be resolved, or returns **false** if the parameter should not be resolved.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This method will return **true** if the identifier was found indicating that this resolver was responsible for this parameter it does not ensure that any parameter value was actually found.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






