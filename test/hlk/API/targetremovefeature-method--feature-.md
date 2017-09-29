---
title: Target.RemoveFeature Method (Feature)
description: Target.RemoveFeature Method (Feature)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 71d53e36-7c21-41ee-9dc5-733324d454b8
---

# Target.RemoveFeature Method (Feature)


**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Target`

`Dim feature As Feature`

`instance.RemoveFeature(feature)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Sub RemoveFeature ( _`

          `feature As Feature _`

`)`

**C#**

`Public abstract void RemoveFeature (`

          `Feature feature`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*feature*

     The feature to remove.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown when the feature to remove was not manually added, or is not present.

Only features that are added by using the AddFeature method can be deleted.

This method is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






