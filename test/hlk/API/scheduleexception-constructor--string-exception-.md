---
title: ScheduleException Constructor (String, Exception)
description: ScheduleException Constructor (String, Exception)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0088e9fe-e7fc-4a71-8d92-d828f906a963
---

# ScheduleException Constructor (String, Exception)


This constructor initializes a new instance of the **ScheduleException** class.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim message As String`

`Dim except As Exception`

`Dim instance As New ScheduleException(message, except)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New`

          `message As String _`

          `except As Exception _`

`)`

**C#**

`Public ScheduleException (`

          `string message`

          `Exception except`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*message*

     A string that represents the message for the exception.

*except*

     An exception object.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






