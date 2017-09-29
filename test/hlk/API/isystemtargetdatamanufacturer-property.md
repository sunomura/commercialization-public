---
title: ISystemTargetData.Manufacturer Property
description: ISystemTargetData.Manufacturer Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 28bd3515-0c48-4877-a1bc-cc86d7e77447
---

# ISystemTargetData.Manufacturer Property


This property represents the manufacturer of the test target (test device).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ISystemTargetData`

`Dim value As String`

`value = instance.Manufacturer`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property Manufacturer As String`

          

**C#**

`string Manufacturer { get; }`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns String.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Returns null if a manufacturer cannot be found.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






