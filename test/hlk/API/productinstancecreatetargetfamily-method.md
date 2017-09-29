---
title: ProductInstance.CreateTargetFamily Method
description: ProductInstance.CreateTargetFamily Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 06633b3d-ce5c-4519-be2d-9e9b1b51f3b3
---

# ProductInstance.CreateTargetFamily Method


This method creates and adds a target family to the existing product instance, using the supplied **DeviceFamily**.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

`Dim deviceFamily As DeviceFamily`

`Dim returnValue As TargetFamily`

`returnValue = instance.CreateTargetFamily(deviceFamily)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function CreateTargetFamily ( _`

          `deviceFamily As DeviceFamily _`

`) As TargetFamily`

**C#**

`public abstract TargetFamily CreateTargetFamily (`

          `DeviceFamily deviceFamily`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*deviceFamily*

     The device family to use to create the **TargetFamily**.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **TargetFamily**, which is an initialized **TargetFamily** object.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






