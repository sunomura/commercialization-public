---
title: Machine.RemoveProperty Method
description: Machine.RemoveProperty Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 945de558-13b8-4b3a-8bb3-b34a4f513080
---

# Machine.RemoveProperty Method


This method removes a property (dimension) by name from this machine.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Machine`

`Dim nameOfPropertyToRemove As String`

`instance.RemoveProperty(nameOfPropertyToRemove)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub RemoveProperty ( _`

          `nameOfPropertyToRemove As String _`

`) `

**C#**

`public abstract void RemoveProperty (`

          `string nameOfPropertyToRemove`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*nameOfPropertyToRemove*

     The name of the property to remove.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is not supported when the project is connected to a package.

 

 






