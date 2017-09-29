---
title: DatabaseProjectManager.GetNetBiosName Method
description: DatabaseProjectManager.GetNetBiosName Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 108909A1-EA3E-4B40-A7AF-8C0A7F174925
---

# DatabaseProjectManager.GetNetBiosName Method


Converts a FQDN name to a NetBIOS name.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public static string GetNetBiosName (`

          `string server`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*server*

The FQDN name to convert.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns the first section that should be a NetBIOS name.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


If a NetBIOS name is passed in, it will be returned unaltered.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






