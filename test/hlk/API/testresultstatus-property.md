---
title: TestResult.Status Property
description: TestResult.Status Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e27186c2-0ec9-47eb-b1aa-fe8f1a2497bc
---

# TestResult.Status Property


This property represents the status of this certification test result.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As TestResult`

`Dim value As TestResultStatus`

`value = instance.Status`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride ReadOnly Property Status As TestResultStatus`

**C#**

`public abstract TestResultStatus Status { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **TestResultStatus**.

>[!NOTE]
>  
**TestResult.Status** does not return **Queued** (if a test is scheduled or running it returns **Running**).

 

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






