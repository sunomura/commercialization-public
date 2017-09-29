---
title: Setting Test Parameters
description: Setting Test Parameters
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6aa655e1-6048-499f-aaa0-d22474711eb9
---

# Setting Test Parameters


Use the **SetParameter()** method to set parameters for the current instance of a **Test** or as the default value for subsequent test runs.

You can also use **SetParameter()** to find all instances of the same name for all of a target’s tests. For example, you could find every parameter with the name *TargetIPAddress* in a large group of tests.

Here's an example of how to set a **Test** parameter:

``` syntax
Test myTest = SomeClass.GetTest();
myTest.SetParameter("TargetIpAddress", "1.2.3.4", ParameterSetAsDefault.ApplyToAllTargets);    
```

When you use the **ParameterSetAsDefault.ApplyToAllTargets()** method, all tests that are associated with the current target are searched, and all parameters that have the same parameter name are set via the supplied values. This parameter setting doesn't span targets within a target family.

 

 






