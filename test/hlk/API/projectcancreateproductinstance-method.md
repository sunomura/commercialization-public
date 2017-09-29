---
title: Project.CanCreateProductInstance Method
description: Project.CanCreateProductInstance Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a45ff342-246b-4392-a653-fe6fbe83fdd3
---

# Project.CanCreateProductInstance Method


This method validates that a child product instance object can be created but does not add the product instance. This function does not create a **ProductInstance**. You must call the CreateProductInstance method to create a **ProductInstance**.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As Project`

`Dim productInstanceName As String`

`Dim pool As MachinePool`

`Dim platform As OSPlatform`

`Dim returnValue As Boolean`

`returnValue = instance.CanCreateProductInstance(productInstanceName, pool, platform)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public MustOverride Function CanCreateProductInstance ( _`

          `productInstanceName As String, _`

          `pool As MachinePool, _`

          `platform As OSPlatform _`

`) As Boolean`

**C#**

`public abstract bool CanCreateProductInstance (`

          `string productInstanceName,`

          `MachinePool pool,`

          `OSPlatform platform`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*productInstanceName*

     The name of the **ProductInstance** object.

*pool*

     The machine pool to use for this **ProductInstance**.

*platform*

     The operating system platform (operating system architecture plus the product SKU) to use for this platform instance.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An error occurs if *productInstanceName* or *pool* is **null**, or if *productInstanceName* is empty.

This method does not create a ProductInstance. You must call CreateProductInstance to create the Product Instance.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






