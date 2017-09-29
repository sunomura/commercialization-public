---
title: TargetException Constructor (String, Exception)
description: TargetException Constructor (String, Exception)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 226cd8ed-6b2e-40c3-a021-c8f82a4fce90
---

# TargetException Constructor (String, Exception)


This constructor initializes a new instance of the **TargetException** class.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim message As String`

`Dim except As Exception`

`Dim instance As New TargetException (message, except)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New ( _`

          `message As String, _`

          `except As Exception _`

`)`

**C#**

`public TargetException (`

          `string message,`

          `Exception except`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*message*

     A string that represents the message for the exception.

*except*

     An **Exception** object.

 

 






