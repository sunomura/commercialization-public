---
title: PackageException Constructor (String, Exception)
description: PackageException Constructor (String, Exception)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f2c8d3b6-62d9-4dd9-b50f-6370ae5fda13
---

# PackageException Constructor (String, Exception)


This constructor initializes a new instance of the **PackageException** class.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim message As String`

`Dim inner As Exception`

`Dim instance As New PackageException(message, inner)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New ( _`

          `message As String, _`

          `inner As Exception _`

`)`

**C#**

`public PackageException (`

          `string message,`

          `Exception inner`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*message*

     The exception message.

*inner*

     The inner exception.

 

 






