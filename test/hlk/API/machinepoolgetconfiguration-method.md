---
title: GetConfiguration Method
description: GetConfiguration Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: C3C32BBC-D912-49EA-859B-813253916A3E
---

# GetConfiguration Method


Retrieves the crash dump configuration for all machines in the machine pool. The dump setting should be retrieved across all machines in the immediate pool. The setting is not retrieved from machines in child pools.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public abstract void GetConfiguration(out MachinePoolCrashDumpCopyBackSetting configurationSetting);`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*configurationSetting (out)*

[MachinePoolCrashDumpCopyBackSetting](machinepoolcrashdumpcopybacksetting-enumeration.md) value that holds the retrieved configuration setting.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






