---
title: TestParameter.IsSame Method
description: TestParameter.IsSame Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3a298347-2955-48d4-95b5-e864a871b701
---

# TestParameter.IsSame Method


This method indicates whether the current instance and a specified TestParameter object are the same parameter.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function IsSame(ByVal other As TestParameter) As Boolean`

**C#**

`public bool IsSame(TestParameter other)`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **true** if the two objects are equal; otherwise, **false**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


When running multiple tests simultaneously, this function indicates if one parameter value can be applied to any of the other parameters in that same test list.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






