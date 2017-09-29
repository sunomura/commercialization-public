---
title: IRunTests Interface
description: IRunTests Interface
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7e047321-cc3a-4b71-ac96-19af35f87872
---

# IRunTests Interface


This class provides an interface that represents the contract that each schedulable object must implement.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IRunTests`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Interface IRunTests`

**C#**

`public interface IRunTests`

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This is mainly used to allow scheduling of tests from various objects. Currently the following objects implement this interface:

-   Project

-   ProductInstance

-   TargetFamily

-   Test

 

 






