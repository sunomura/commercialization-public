---
title: PackageManager.Sign Method (String, X509Certificate, String)
description: PackageManager.Sign Method (String, X509Certificate, String)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b2e952fe-dc3c-42ae-b87e-1e9737ce0873
---

# PackageManager.Sign Method (String, X509Certificate, String)


Sign an existing package.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public static void Sign (`

          `string sourcePackage,`

          `X509Certificate certificate,`

          `string outputPackage`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*sourcePackage*

File name (including path) to the package file.

*certificate*

The certificate used for signing.

*certificate*

File name (including path) to the signed package.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


If the sourcePackage and outputPackage parameters are the same the package will be replaced.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






