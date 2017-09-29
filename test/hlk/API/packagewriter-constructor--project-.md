---
title: PackageWriter Constructor (Project)
description: PackageWriter Constructor (Project)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e46d2420-0b36-42e7-a21c-dad1b1609587
---

# PackageWriter Constructor (Project)


This constructor initializes a new instance of the **PackageWriter** class. This constructor is used for creating a new submission package. This constructor cannot be used to create an Update Package (for DUA).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim packagePath As Project`

`Dim instance As New PackageWriter(project)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New ( _`

          `project As Project _`

`)`

**C#**

`public PackageWriter (`

          `Project project`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*project*

     The name of the project for which a package object is created.

 

 






