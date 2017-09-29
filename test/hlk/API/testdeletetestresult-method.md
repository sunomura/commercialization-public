---
title: Test.DeleteTestResult Method
description: Test.DeleteTestResult Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1feaf060-4efc-4b85-9ed3-c4817670c6dc
---

# Test.DeleteTestResult Method


This method deletes a specific result.

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overridable Sub DeleteTestResult(ByVal resultToRemove As TestResult)`

**C#**

`public virtual void DeleteTestResult(TestResult resultToRemove)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*resultToRemove*

     Result to be removed

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Exception thrown if:

-   Result is null.

-   Result is invalid or the wrong type.

-   Result is not a result from this test.

-   Result could not be deleted from the database.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






