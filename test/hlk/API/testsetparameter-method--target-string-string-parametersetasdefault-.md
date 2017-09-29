---
title: Test.SetParameter Method (Target, String, String, ParameterSetAsDefault)
description: Test.SetParameter Method (Target, String, String, ParameterSetAsDefault)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7e795150-adec-4571-85c2-cdac9b421210
---

# Test.SetParameter Method (Target, String, String, ParameterSetAsDefault)


This method updates a job parameter.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

`Dim target As Target`

`Dim parameterName As String`

`Dim parameterValue As String`

`Dim setAsDefault As ParameterSetAsDefault`

`Dim returnValue As String`

`returnValue = instance.SetParameter(target, parameterName, parameterValue, setAsDefault)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function SetParameter ( _`

          `target As Target, _`

          `parameterName As String, _`

          `parameterValue As String, _`

          `setAsDefault As ParameterSetAsDefault _`

`) As String`

**C#**

`public abstract string SetParameter (`

          `Target target,`

          `string parameterName,`

          `string parameterValue,`

          `ParameterSetAsDefault setAsDefault`

`) `

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*target*

          The test target (test computer) to use to set this parameter.

*parameterName*

          The name of the test parameter to set.

*parameterValue*

          The new value to set the test parameter to.

*setAsDefault*

          This value indicates that the test parameter is set as the default for all future job runs.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **String**, which is the updated value for the parameter.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






