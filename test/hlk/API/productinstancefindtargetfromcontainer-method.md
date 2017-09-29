---
title: ProductInstance.FindTargetFromContainer Method
description: ProductInstance.FindTargetFromContainer Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1f126e70-43b4-4044-8ae2-a5f7d0dc7e93
---

# ProductInstance.FindTargetFromContainer Method


This method creates a list of targets containing the specific container ID. There are two special containerIds to consider. The first is the system containerId(00000000-0000-0000-ffff-ffffffffffff). If this is passed in, then the method returns a list with just a single "system" target. The second is a zero-decorated GUID (00000000-0000-0000-0000-000000000000). This is an invalid GUID.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ProductInstance`

`Dim containerId As Guid`

`Dim returnValue As ReadOnlyCollection(Of TargetData)`

`returnValue = instance.FindTargetFromContainer(containerId)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function FindTargetFromContainer ( _`

          `containerId As Guid _`

`) As ReadOnlyCollection(Of TargetData)`

**C#**

`public ReadOnlyCollection<TargetData> FindTargetFromContainer (`

          `Guid containerId`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*containerId*

     The GUID of containerId for (most likely) a device.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection**, which is a list of test targets with &lt;paramref name="containerId"/&gt;. If no test targets (devices) contains a container ID of &lt;paramref name="containerId"/&gt; then an empty list is returned.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






