---
title: OSPlatform.Equals Method (OSPlatform)
description: OSPlatform.Equals Method (OSPlatform)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: eaf4b869-c5ab-4374-87d3-a8312634627b
---

# OSPlatform.Equals Method (OSPlatform)


This method compares two **OSPlatform** instances.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As OSPlatform`

`Dim otherPlatform As OSPlatform`

`Dim returnValue As Boolean`

`returnValue = instance.Equals(otherPlatform)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function Equals ( _`

          `otherPlatform As OSPlatform _`

`) As Boolean`

**C#**

`public bool Equals (`

          `OSPlatform otherPlatform`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*otherMachineSet*

     The **OSPlatform** object to compare against.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the two objects are equal; otherwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






