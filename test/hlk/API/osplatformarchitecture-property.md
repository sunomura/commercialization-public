---
title: OSPlatform.Architecture Property
description: OSPlatform.Architecture Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dda1c163-fec3-431d-97a8-d59aefb62d4f
---

# OSPlatform.Architecture Property


This property represents the CPU architecture (for example, x86, x64, or ARM).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As OSPlatform`

`Dim value As CpuArchitecture`

`value = instance.Architecture`

`instance.Architecture = value`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataMemberAttribute> _`

`Public Property Architecture As CpuArchitecture`

**C#**

`[DataMemberAttribute]`

`public CpuArchitecture Architecture { get; protected set; }`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **CpuArchitecture**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


See SYSTEM\_INFO.wProcessorArchitecture in Win32 documentation.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






