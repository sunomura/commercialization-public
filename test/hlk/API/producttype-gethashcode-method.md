---
title: ProductType.GetHashCode Method
description: ProductType.GetHashCode Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: D104C1F8-1533-41F0-80E4-2F223D34DA4E
---

# ProductType.GetHashCode Method


Returns the hash code for the current [ProductType](producttype-class.md) object.

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public override int GetHashCode ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns an integer hash code.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Product Types read from a Package will have different hash codes compared with ones read from the database.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






