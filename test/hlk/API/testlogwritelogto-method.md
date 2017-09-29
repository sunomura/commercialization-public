---
title: TestLog.WriteLogTo Method
description: TestLog.WriteLogTo Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7ed56c3d-8805-436b-bdd5-d9ba68e32b61
---

# TestLog.WriteLogTo Method


This method writes a log file to a specific file location on disk.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TestLog`

`Dim destination As String`

`instance.WriteLogTo(destination)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub WriteLogTo ( _`

          `destination As String _`

`)`

**C#**

`public abstract void WriteLogTo (`

          `string destination`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*destination*

     A string value that describes the destination (file path and file name) to write the log to.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs if *destination* is **null** or empty.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






