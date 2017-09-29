---
title: MachineSet.ApplyMachineDimensions Method
description: MachineSet.ApplyMachineDimensions Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 82f8851a-8079-4b45-937b-be60d08d136f
---

# MachineSet.ApplyMachineDimensions Method


This method applies the machine roles dimension to all of the machines in the roles.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As MachineSet`

`instance.ApplyMachineDimensions`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub ApplyMachineDimensions`

**C#**

`public void ApplyMachineDimensions ()`

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This method will first call the **Validate()** method. If **Validate()** fails, this will throw an exception and then it will attempt to set the machine dimensions for these roles.

An exception is thrown when there are validation errors.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






