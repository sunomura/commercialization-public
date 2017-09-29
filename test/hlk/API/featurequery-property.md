---
title: Feature.Query Property
description: Feature.Query Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b4e0dcac-5690-4f6c-8008-7e0a26b1f90a
---

# Feature.Query Property


Represents the query used to determine the contents of a **Feature**.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Feature`

`Dim value As String`

`value = instance.Query`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataMemberAttribute> _`

`Public Property Query As String`

**C#**

`[DataMemberAttribute]`

`public string Query { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **String**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The query is used for automatic detection of Features and Requirements. This query is run against all the target data for a particular machine. If there are any results, the Feature is present on the Machine.

 

 






