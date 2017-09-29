---
title: ProjectManager Class
description: ProjectManager Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1cfba6e8-f42b-4210-b486-4951a7d4e81b
---

# ProjectManager Class


This class provides an interface to connect to a project packager or a running database and controller.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProjectManager`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustInherit Class ProjectManager`

          `Implements IDisposable`

**C#**

`public abstract class ProjectManager : IDisposable`

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

     **Microsoft.Windows.Kits.Hardware.ObjectModel.ProjectManager**

          **Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection.DatabaseProjectManager**

          **Microsoft.Windows.Kits.Hardware.ObjectModel.Submission.PackageManager**

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






