---
title: PackageWriter.TargetFamiliesAreDeepMergeCompatible Method
description: PackageWriter.TargetFamiliesAreDeepMergeCompatible Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 59B0968E-C9EE-4867-82F2-3B0D768CF2C0
---

# PackageWriter.TargetFamiliesAreDeepMergeCompatible Method


Checks if two target families are similar enough for deep merging.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

` public static bool TargetFamiliesAreDeepMergeCompatible (`

          `TargetFamily firstTargetFamily,`

          `TargetFamily secondTargetFamily`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*firstTargetFamily*

First instance of TargetFamily for deep merge comparison.

*secondTargetFamily*

Second instance of TargetFamily for deep merge comparison.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns true if the targets' families are similar enough; otherwise it returns false.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






