---
title: Test.ManuallyAdded Property
description: Test.ManuallyAdded Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 68ED9765-0E73-42F4-8421-FFEF7BFB7C75
---

# Test.ManuallyAdded Property


Gets whether the test was added separate from the feature detection process.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public abstract bool ManuallyAdded `

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns a value which indicates whether the test was added separate from the feature detection process.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


If tests are being manually added by the user to a Project, Product Instance, etc., the feature detection process will run and determine whether or not the test being manually added is relevant for the specific target/target family. If it is not, and the user has chosen to add the test anyways, then this property will be set to true.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






