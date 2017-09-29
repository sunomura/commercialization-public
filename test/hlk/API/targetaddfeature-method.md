---
title: Target.AddFeature Method
description: Target.AddFeature Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 077f7071-3f38-48fa-997d-532a189be61d
---

# Target.AddFeature Method


This method adds a [Feature](feature-class.md).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public abstract void AddFeature (`

          `Feature feature`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*feature*

The feature to add to the test target.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


When features are added using this method, the features were not automatically detected. Using this method will introduce all the tests associated with the feature to the target and those tests will have to run and pass. Since the feature was not detected, there is a chance that the added tests may fail.

This method is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






