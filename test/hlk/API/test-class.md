---
title: Test Class
description: Test Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 660ca404-396c-4eb6-8ab8-41c283d6c0b9
---

# Test Class


This abstract class represents a certification test. It defines the common behavior and properties every certification test is expected to expose.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Test`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataContractAttribute> _`

`Public MustInherit Class Test`

          `Implements IRunTests`

**C#**

`[DataContractAttribute]`

`public abstract class Test : IRunTests`

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Some tests require additional information to run. These tests are called parameters. You can set default values for parameters as well as specific values for individual runs. APIs to set these parameters are also available.

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

     **Microsoft.Windows.Kits.Hardware.ObjectModel.Test**

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






