---
title: Task.AssessmentScores Property
description: Task.AssessmentScores Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 26a41498-6bfc-401e-8260-c0b2e239d432
---

# Task.AssessmentScores Property


This property represents a collection of assessment scores for this task.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Task`

`Dim value As ReadOnlyCollection(Of AssessmentData)`

`value = instance.AssessmentScores`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride ReadOnly Property AssessmentScores As ReadOnlyCollection(Of AssessmentData)`

**C#**

`public abstract ReadOnlyCollection<AssessmentData> AssessmentScores { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






