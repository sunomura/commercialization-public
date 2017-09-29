---
title: Project Class
description: Project Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 54b84baf-999f-4618-ac8a-ea6c368ae544
---

# Project Class


This class represents a **Project** object which is created in the database for each project the user initiates. It is effectively handles a set of product instances that users will be running logo tests for. In addition to that, there is metadata stored along with each **Project** object.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Project`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataContractAttribute> _`

`Public MustInherit Class Project`

          `Implements IRunTests`

**C#**

`[DataContractAttribute]`

`public abstract class Project : IRunTests`

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

     **Microsoft.Windows.Kits.Hardware.ObjectModel.NotificationBase**

          **Microsoft.Windows.Kits.Hardware.ObjectModel.Project**

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Projects are the highest level objects in the hierarchy of data and objects used to represent certification. There are a number of layers of objects between the project and the test results and logs.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






