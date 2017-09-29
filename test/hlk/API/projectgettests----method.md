---
title: Project.GetTests () Method
description: Project.GetTests () Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6548f35e-14f5-43a4-9aee-7ad3a6cd9a56
---

# Project.GetTests () Method


Retrieves all tests for this project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

``` syntax
Public Overridable Function GetTests() As IList(Of Test) 
    Dim tests As List(Of Test) = New List(Of Test)()
    For Each productInstance As ProductInstance In Me.GetProductInstances()
        tests.AddRange(productInstance.GetTests())
    NextReturn tests
End Function
```

**C#**

``` syntax
public virtual IList<Test> GetTests()
{
    List<Test> tests = new List<Test>();
    foreach (ProductInstance productInstance in this.GetProductInstances())
    {
        tests.AddRange(productInstance.GetTests());
    }
    return tests;
}
```

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


A collection of all tests for this project.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


For backwards compatibility with HCK 2.0, returns tests that are tagged with Certification content level. To get tests for other content levels, use the overloaded method that takes a collection of ContentLevelType.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






