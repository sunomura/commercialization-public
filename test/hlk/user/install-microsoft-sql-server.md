---
title: Install Microsoft SQL Server
description: Install Microsoft SQL Server
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 004bb51b-adb9-41b4-8d1a-df662200029b
---

# Install Microsoft SQL Server

>[!WARNING]
>  HLK does not support SQL Server 2014. You must uninstall SQL Server 2014 prior to installing the HLK.

>[!WARNING]
>  HLK does not support 32-bit versions of SQL Server. Any 32-bit instance must be uninstalled prior to installing the HLK.

 

Windows HLK supports 64-bit versions of SQL Server 2012 and SQL Server 2008R2.

Depending on your operating system, you might need to install additional service packs for SQL prior to installing the HLK.

1.  Enable .NET 2.0/3.x feature from within Server Manager
2.  For SQL Server 2008R2 (not required for SQL Server 2012), do the following:
    -   Install SQL Server 2012 SharedManagementObjects.msi (64-bit) from the following link:
        -   <http://go.microsoft.com/fwlink/p/?linkid=239659&clcid=0x409>
    -   Install SQL Server 2012 SQLSysClrTypes.msi (64-bit) from the following link:
        -   <http://go.microsoft.com/fwlink/p/?linkid=239644&clcid=0x409>

Install SQL using the setup application using the following command line for a unattended install. /QUIET and /HIDECONSOLE flags may be omitted to see any errors that may occur during install.

``` syntax
(setup application) /QUIET /HIDECONSOLE /ACTION=install /FEATURES=SQL,RS /SQLSVCACCOUNT="NT AUTHORITY\SYSTEM" /AGTSVCACCOUNT="NT AUTHORITY\SYSTEM" /AGTSVCSTARTUPTYPE=Automatic /ASSVCACCOUNT="NT AUTHORITY\SYSTEM" /RSSVCACCOUNT="NT AUTHORITY\SYSTEM" /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" "%USERDOMAIN%\%USERNAME%" /INSTANCENAME=MSSQLSERVER /TCPENABLED=1 /NPENABLED=1 /IAcceptSQLServerLicenseTerms=1
```

 

 






