---
title: PackageManager.Sign Method (String, X509Certificate)
description: PackageManager.Sign Method (String, X509Certificate)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6a909337-3191-4dc6-9752-3efb13657817
---

# PackageManager.Sign Method (String, X509Certificate)


Sign an existing package.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public static void Sign (`

          `string sourcePackage,`

          `X509Certificate certificate`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*sourcePackage*

File name (including path) to the package file.

*certificate*

The certificate used for signing.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The package specified is signed and replaced. This is equivalent to invoking the [Sign(String, X509Certificate, String) Method](packagemanagersign-method--string-x509certificate-string-.md).

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






