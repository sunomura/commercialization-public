---
title: OSPlatform.MajorVersion Property
description: OSPlatform.MajorVersion Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 01338750-fb75-4f9c-ad08-fd58748f058a
---

# OSPlatform.MajorVersion Property


This property represents the major version of this platform.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As OSPlatform`

`Dim value As Integer`

`value = instance.MajorVersion`

`instance.MajorVersion = value`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataMemberAttribute> _`

`Public Property MajorVersion As Integer`

**C#**

`[DataMemberAttribute]`

`public int MajorVersion { get; protected set; }`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **Int32**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


See OSVERSIONINFOEX.dwMajorVersion in Win32 documentation.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






