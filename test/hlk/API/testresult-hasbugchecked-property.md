---
title: HasBugchecked Property
description: HasBugchecked Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 178D7CEC-4840-4316-A47D-E76BC45E6764
---

# HasBugchecked Property


Indicates whether a bugcheck occurred on the client machine during the test run.

>[!NOTE]
>  Bugchecks aren't necessarily caused by tests. Additional triage of the crash dump file is required to determine what caused the bugcheck. For example, while running WiFi tests, a display driver might cause a bugcheck.

 

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public virtual bool HasBugchecked { get; internal set; }`

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






