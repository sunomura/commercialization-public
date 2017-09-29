---
title: PackageManager Constructor (String)
description: PackageManager Constructor (String)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8d9ac67e-0480-44ee-8a33-f7efa11ef110
---

# PackageManager Constructor (String)


This constructor initializes a new instance of the **PackageManager** class.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim packagePath As String`

`Dim instance As New PackageManager(packagePath)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New ( _`

          `packagePath As String _`

`)`

**C#**

`public PackageException (`

          `string packagePath`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*packagePath*

     The path to the package file that this instance manages.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown if *packagePath* is null or invalid, or if there is more than one relationship.

 

 






