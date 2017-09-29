---
title: MachinePool.SetConfiguration Method
description: MachinePool.SetConfiguration Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 11c1aa49-7c07-4f89-9228-ad725f5d6e2c
---

# MachinePool.SetConfiguration Method


Sets the crash dump configuration for all machines in the machine pool. The dump setting should be set across all machines in the immediate pool. The setting is not set on machines in child pools.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public abstract void SetConfiguration(MachinePoolCrashDumpCopyBackSetting configurationSetting);`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*configurationSetting*

[MachinePoolCrashDumpCopyBackSetting](machinepoolcrashdumpcopybacksetting-enumeration.md) value that defines the configuration setting.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






