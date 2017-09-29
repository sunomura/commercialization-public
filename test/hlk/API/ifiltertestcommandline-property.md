---
title: IFilter.TestCommandLine Property
description: IFilter.TestCommandLine Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 074a5c14-bed2-4d66-a45c-682f3bf039eb
---

# IFilter.TestCommandLine Property


This property represents the command line for the test being filtered.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IFilter`

`Dim value As String`

`value = instance.TestCommandLine`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property TestCommandLine As String`

**C#**

`string TestCommandLine  { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **String**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Used for case-insensitive matching (equals or starts with) of the test command line.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






