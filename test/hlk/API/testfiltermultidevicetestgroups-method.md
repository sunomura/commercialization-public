---
title: Test.FilterMultiDeviceTestGroups Method
description: Test.FilterMultiDeviceTestGroups Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0fda5e37-5e28-49b8-9f53-94955dd94cab
---

# Test.FilterMultiDeviceTestGroups Method


This method removes tests from a list of tests that can be consolidated and returns the consolidated groupings of tests that are compatible.

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Shared Function FilterMultiDeviceTestGroups(ByVal tests As List(Of Test)) As List(Of List(Of Test))`

**C#**

`public static List<List<Test>> FilterMultiDeviceTestGroups(List<Test> tests)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*tests*

     A list of tests to be filtered for multi-device tests.

## <span id="Returns"></span><span id="returns"></span><span id="RETURNS"></span>Returns


A list test groupings which can be consolidated.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






