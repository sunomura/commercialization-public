---
title: Project.RemoveTests Method
description: Project.RemoveTests Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1A3A5ECB-C26E-4E90-BBBD-75F7A41D3F1C
---

# Project.RemoveTests Method

>[!WARNING]
>  This functionality is being deprecated. Please use playlists to create custom test pass lists.

 

Removes the given Tests from the Project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public virtual void RemoveTests (`

          `IEnumerable<TestDefinition> tests`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*tests*

The tests to be removed from the Project.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Removes the tests from all Product Instances and Target Families in the Project.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






