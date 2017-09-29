---
title: AppId
description: AppId
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cce5998e-d722-43c7-a17c-ed0847cca128
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# AppId


`AppId` specifies the application whose monochrome icon appears on the **Lock** screen. The `AppId` must be the `AppUserModelID` found in the application's AUMIDs.txt file, which is located in the app package downloaded from the OEM channel partner portal of the Microsoft Store.

## Values


The `AppId` is a string, with a maximum value of 256 characters.

## Valid Configuration Passes


specialize

auditUser

oobeSystem

## Parent Hierarchy


[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [StartTiles](microsoft-windows-shell-setup-starttiles.md) | [LockScreen](microsoft-windows-shell-setup-starttiles-lockscreen.md) | [Badge](microsoft-windows-shell-setup-starttiles-lockscreen-badge.md) | **AppId**

## Applies To


For a list of the supported Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example


The following XML output shows how to configure the AppId for the `LockScreen`.

```
<LockScreen>
  <Badge>
      <AppId>34567ChannelFabrikam.channel-DEF_012ghijk345!App</AppId>
  </Badge>
</LockScreen>
```

## Related topics


[SquareTiles](microsoft-windows-shell-setup-starttiles-squaretiles.md)

[WideTiles](microsoft-windows-shell-setup-starttiles-widetiles.md)

 

 







