---
title: Test.SetParameter Method (String, String, ParameterSetAsDefault)
description: Test.SetParameter Method (String, String, ParameterSetAsDefault)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a04e419d-5841-4dda-9636-606e7501b223
---

# Test.SetParameter Method (String, String, ParameterSetAsDefault)


This method updates a job parameter. This will set the parameter for all applicable targets for this job

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

`Dim parameterName As String`

`Dim parameterValue As String`

`Dim setAsDefault As ParameterSetAsDefault`

`Dim returnValue As String`

`returnValue = instance.SetParameter(parameterName, parameterValue, setAsDefault)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function SetParameter ( _`

          `parameterName As String, _`

          `parameterValue As String, _`

          `setAsDefault As ParameterSetAsDefault _`

`) As String`

**C#**

`public abstract string SetParameter (`

          `string parameterName,`

          `string parameterValue,`

          `ParameterSetAsDefault setAsDefault`

`) `

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*parameterName*

          The name of the test parameter to set.

*parameterValue*

          The new value to set the test parameter to.

*setAsDefault*

          This value indicates that the test parameter is set as the default for all future job runs.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **String**, which is the updated value for the parameter.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


All targets where this property can be set are updated.

This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






