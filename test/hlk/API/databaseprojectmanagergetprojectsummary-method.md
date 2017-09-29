---
title: DatabaseProjectManager.GetProjectSummary Method
description: DatabaseProjectManager.GetProjectSummary Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a7940dee-bfdd-4f0f-9c5a-b243545d25d9
---

# DatabaseProjectManager.GetProjectSummary Method


This method retrieves the list of requirements in the Windows HCK.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As DatabaseProjectManager`

`Dim returnValue As ReadOnlyCollection(Of Requirement)`

`returnValue = instance.GetRequirements`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function GetRequirements As ReadOnlyCollection(Of Requirement)`

**C#**

`public override ReadOnlyCollection<Requirement> GetRequirements ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a list a of known requirements.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






