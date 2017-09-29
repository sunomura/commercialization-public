---
title: ProjectException Class
description: ProjectException Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c4be8d20-36a7-4734-8bed-e87b95e2fa96
---

# ProjectException Class


This class is a base class for all logo manager exceptions.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProjectException`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<SerializableAttribute> _`

`Public Class ProjectException`

          `Inherits ProjectManagerException`

**C#**

`[SerializableAttribute]`

`public class ProjectException: ProjectManagerException`

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

     **System.Exception**

          **Microsoft.Windows.Kits.Hardware.ObjectModel.ProjectManagerException**

               **Microsoft.Windows.Kits.Hardware.ObjectModel.ProjectException**                     **Microsoft.Windows.Kits.Hardware.ObjectModel.Submission.PackageException**

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






