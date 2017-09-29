---
title: DatabaseProjectManager.GetFeatures Method
description: DatabaseProjectManager.GetFeatures Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 382c6044-7238-45b9-94ad-7873e03e4543
---

# DatabaseProjectManager.GetFeatures Method


This method returns all of the features stored in the Windows HCK.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DatabaseProjectManager`

`Dim returnValue As ReadOnlyCollection(Of Feature)`

`returnValue = instance.GetFeatures`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function GetFeatures As ReadOnlyCollection(Of Feature)`

**C#**

`public override ReadOnlyCollection<Feature> GetFeatures ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a list of known features.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






