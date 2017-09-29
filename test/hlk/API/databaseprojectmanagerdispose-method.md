---
title: DatabaseProjectManager.Dispose Method
description: DatabaseProjectManager.Dispose Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d24ef04f-c6d1-465a-a043-685592c2b868
---

# DatabaseProjectManager.Dispose Method


This method implements the **IDisposable** interface.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim disposing As Boolean`

`Me.Dispose(disposing)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Protected Overrides Sub Dispose ( _`

          `disposing As Boolean _`

`) `

**C#**

`protected override void Dispose (`

          `bool disposing`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*disposing*

     A Boolean value to indicate if this is being removed.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs when the *projectNameToDelete* parameter is **null** or empty.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






