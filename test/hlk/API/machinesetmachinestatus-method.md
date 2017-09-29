---
title: Machine.SetMachineStatus Method
description: Machine.SetMachineStatus Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 67131a0c-c024-4e5c-a465-d48863658061
---

# Machine.SetMachineStatus Method


This method sets the machine status. This is a blocking call and will wait until the machine status is set or the timeout has elapsed. A good default value is 10 min (600000 milliseconds).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Machine`

`Dim status As MachineStatus`

`Dim millisecondsTimeout As Long`

`Dim returnValue As Boolean`

`returnValue = instance.SetMachineStatus(status, millisecondsTimeout)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function SetMachineStatus ( _`

          `status As MachineStatus, _`

          `millisecondsTimeout As Long _`

`) As Boolean`

**C#**

`public abstract bool SetMachineStatus (`

          `MachineStatus status,`

          `long millisecondsTimeout`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*status*

     The machine status to be set.

*millisecondsTimeout*

     The number of milliseconds to wait before this method returns. This value can be -1 (indicating an infinite wait time) or a positive number.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if the machine value is set,or **false** if the timeout value was reached.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception occurs if:

-   *status* is not valid.

-   The value of *millisecondsTimeout* is less than -1.

    This is a blocking call and will wait until the machine status is set or the timeout has elapsed. A good default value is 10 min (600000 milliseconds). To specify infinite time, set the timeout to -1.

    This is not supported when the project is connected to a package.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






