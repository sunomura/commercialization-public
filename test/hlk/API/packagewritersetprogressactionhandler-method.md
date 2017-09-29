---
title: PackageWriter.SetProgressActionHandler Method
description: PackageWriter.SetProgressActionHandler Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: aa554d0f-db45-4ec4-938f-bfb84cd7139d
---

# PackageWriter.SetProgressActionHandler Method


This method sets an action handler that is used to send out submission progress updates. This method can be used for both submission packages and update packages.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageWriter`

`Dim actionHandler As Action(Of PackageProgressInfo)`

`instance.SetProgressActionHandler(actionHandler)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub SetProgressActionHandler ( _`

          `actionHandler As Action(Of PackageProgressInfo) _`

`) `

**C#**

`public void SetProgressActionHandler (`

          `Action<PackageProgressInfo> actionHandler`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*actionHandler*

     The name of the handler to call.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






