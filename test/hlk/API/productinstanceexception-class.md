---
title: ProductInstanceException Class
description: ProductInstanceException Class
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 71ae8917-8a24-4eb5-b6d5-035be8207b27
---

# ProductInstanceException Class


This exception class is defined to handle target-specific errors. Every time a non-expected occurrence happens, a **ProductInstanceException** is thrown to add more details related to the target.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstanceException`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<SerializableAttribute> _`

`Public Class ProductInstanceException`

          `Inherits ProjectManagerException`

**C#**

`[SerializableAttribute]`

`public class ProductInstanceException : ProjectManagerException`

## <span id="Inheritance_Hierarchy"></span><span id="inheritance_hierarchy"></span><span id="INHERITANCE_HIERARCHY"></span>Inheritance Hierarchy


**System.Object**

     **System.Exception**

          **Microsoft.Windows.Kits.Hardware.ObjectModel.ProjectManagerException**

                    **Microsoft.Windows.Kits.Hardware.ObjectModel.ProductInstanceException**

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






