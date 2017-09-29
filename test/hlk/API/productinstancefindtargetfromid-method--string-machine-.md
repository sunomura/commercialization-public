---
title: ProductInstance.FindTargetFromId Method (String, Machine)
description: ProductInstance.FindTargetFromId Method (String, Machine)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7b1354ff-8e10-4368-82c2-e6217d557ff6
---

# ProductInstance.FindTargetFromId Method (String, Machine)


This method returns an appropriate target type based on information associated with &lt;paramref name="targetId"/&gt;.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

`Dim targetId As String`

`Dim machine As Machine`

`Dim returnValue As ReadOnlyCollection(Of TargetData)`

`returnValue = instance.FindTargetFromId(targetId, machine)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function FindTargetFromId ( _`

          `targetId As String, _`

          `machine As Machine _`

`) As ReadOnlyCollection(Of TargetData)`

**C#**

`public ReadOnlyCollection<TargetData> FindTargetFromId (`

          `string targetId`

          `Machine machine`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*targetId*

     The ID that identifies the target. This can be found in the SysParse data.

*machine*

     The test computer to look for the ID value on.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**. If &lt;paramref name="targetId"/&gt; is not found on the machine (test computer) associated with the product instance, **null** is returned. Otherwise, an instance of the test target is returned.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown when the *targetIdToDelete* parameter is **null** or empty.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






