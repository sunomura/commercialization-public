---
title: Requirement.GetDescriptionData Method
description: Requirement.GetDescriptionData Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cbc626ea-82ed-487a-8816-47df53026429
---

# Requirement.GetDescriptionData Method


This method returns a description of the requirementTableEntry given the specified language.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Requirement`

`Dim language As String`

`Dim returnValue As RequirementDescriptionData`

`returnValue = instance.GetDescriptionData(language)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function GetDescriptionData ( _`

          `language As String _`

`) As RequirementDescriptionData`

**C#**

`public abstract RequirementDescriptionData GetDescriptionData (`

          `string language`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*language*

     The language for the description data requested.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns [RequirementDescriptionData Class](requirementdescriptiondata-class.md), which is a DescriptionData class in the supplied language.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






