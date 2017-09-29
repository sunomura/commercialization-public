---
title: ProductInstance.RemoveTests Method
description: ProductInstance.RemoveTests Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 4EA0E7FD-007C-4D15-91B4-07BB93159BF3
---

# ProductInstance.RemoveTests Method

>[!WARNING]
>  This functionality is being deprecated. Please use playlists to create custom test pass lists.

 

Removes the given Tests from the [ProductInstance](productinstance-class.md).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public virtual void RemoveTests (`

          `IEnumerable<TestDefinition> tests`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*tests*

The tests to remove.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






