---
title: Project.DeleteProductInstance Method
description: Project.DeleteProductInstance Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1f227ea5-bb7b-4c59-84ae-385aef41cacb
---

# Project.DeleteProductInstance Method


This method deletes **ProductInstance** object.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Project`

`Dim nameOfProductInstanceToDelete As String`

`instance.DeleteProductInstance(nameOfProductInstanceToDelete)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub DeleteProductInstance ( _`

          `nameOfProductInstanceToDelete As String _`

`) `

**C#**

`public abstract void DeleteProductInstance (`

          `string nameOfProductInstanceToDelete`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*nameOfProductInstanceToDelete*

     The name of the **ProductInstance** object to delete.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An error occurs if *nameOfProductInstanceToDelete* is **null** or empty.

This method is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






