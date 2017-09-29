---
title: ProductInstance.DeleteTarget Method (String, Machine)
description: ProductInstance.DeleteTarget Method (String, Machine)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0f60ede5-caa1-4ef4-b3df-1a341b9f8f19
---

# ProductInstance.DeleteTarget Method (String, Machine)


This method deletes a targetTableEntry by name/id.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

`Dim targetIdToDelete As String`

`Dim machine As Machine`

`instance.DeleteTarget(targetIdToDelete, machine)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub DeleteTarget ( _`

          `targetIdToDelete As String _`

          `machine As Machine _`

`)`

**C#**

`public void DeleteTarget (`

          `string targetIdToDelete`

          `Machine machine`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*targetIdToDelete*

     The name or id of the targetTableEntry to delete.

*machine*

     The machine which contains this test target.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown when:

-   The *targetIdToDelete* parameter is **null** or empty.

-   The **ProductInstance** could not be found or was deleted.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






