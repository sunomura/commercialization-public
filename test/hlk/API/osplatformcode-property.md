---
title: OSPlatform.Code Property
description: OSPlatform.Code Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a0c35d02-d2c5-433c-bcc4-ae286465438e
---

# OSPlatform.Code Property


This property represents the Portal ID for this platform.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As OSPlatform`

`Dim value As String`

`value = instance.Code`

`instance.Code = value`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataMemberAttribute> _`

`Public Property Code As String`

**C#**

`[DataMemberAttribute]`

`public string Code { get; protected set; }`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **String**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Code is an identifier used by submission processing.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






