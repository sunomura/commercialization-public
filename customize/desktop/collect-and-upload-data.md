---
title: Collect and upload data
description: Collect encrypted user data and upload it to your server.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.author: alhopper
ms.date: 09/27/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Collect and upload data

Create and preinstall a Microsoft Store app, or write a service to run after first sign-in, to:

1. Collect the encrypted customer data, including the user name from the [Windows.System.User namespace](https://docs.microsoft.com/en-us/uwp/api/windows.system.user) as well as the [local time stamp](#timestamp) of first sign-in.
1. Upload that data set to your server for decryption and use.

> [!Note]
> A Microsoft Store app must be started by the customer for the data to be returned.

The app is registered using its Application User Model ID (AUMID) and can collect the time stamp, user data, session key, and check box state data written to the appdata folder for the app. To do this, you can use the [Microsoft-Windows-Shell-Setup | OOBE | OEMAppId](https://docs.microsoft.com/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-shell-setup-oobe-oemappid) setting.

If you create and run a service to upload the data, you should set the service to run at least 30 minutes after the user gets to the Start screen, and only run the service once. Setting your service to run at this time ensures that your service won't consume system resources in the background while users are getting their first chance to explore the Start screen and their apps. The service must gather the data from within the OOBE directory, as well as the time stamp and user name, as applicable. The service should also determine what actions to take in response to the user's choices. For example, if the user opted in to an anti-malware app trial, your service should start the trial rather than rely on the anti-malware app to decide if it should run. Or, as another example, if your user opted in to emails from your company or partner companies, your service should communicate that info to whomever handles your marketing emails.

For more info about how to write a service, see [Developing Windows Service Applications](https://msdn.microsoft.com/en-us/library/y817hyb6(v=vs.110).aspx).

## <A name="timestamp"></a>Collect the time stamp

The time stamp of first sign-in is written to the Windows registry under this key:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\OOBE\Stats [EndTimeStamp]`

The time stamp is written in UTC (Coordinated Universal Time) format.

If you implement a Microsoft Store app to collect customer data from the Registration pages, you can provide the Application User Model ID (AUMID) for that app so that the time stamp is written to the AppData folder of your app. For more info about how to use AUMID and the AppData folder, see [Develop UWP apps](https://developer.microsoft.com/en-us/windows/apps/develop).

If you implement a service to collect customer data from the Registration pages, your service can read the time stamp from the registry.