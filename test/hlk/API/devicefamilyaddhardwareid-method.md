---
title: DeviceFamily.AddHardwareId Method
description: DeviceFamily.AddHardwareId Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9db9ed12-1485-448a-8dbc-84669dba6aa9
---

# DeviceFamily.AddHardwareId Method


This method adds a new hardware ID to this **DeviceFamily** object.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DeviceFamily`

`Dim hardwareIdToAdd As String`

`instance.AddHardwareId(hardwareIdToAdd)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub AddHardwareId ( _`

          `hardwareIdToAdd As String _`

`)`

**C#**

`public abstract void AddHardwareId (`

          `string hardwareIdToAdd`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*hardwareIdToAdd*

     The hardware ID to add to the device family hardware ID list.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






