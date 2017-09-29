---
title: Troubleshooting Windows HLK Setup
description: Troubleshooting Windows HLK Setup
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c3e3a340-a5e9-49fa-84e4-3ae20ae2cf05
---

# Troubleshooting Windows HLK Setup


This article contains information to help you to troubleshoot Windows Hardware Lab Kit (Windows HLK) installation and setup issues.

**In this topic:**

-   [Cannot browse \\\\&lt;controller-name&gt;\\HLKInstall\\ on Studio or Client computer](#cantbrowse)

-   [Cannot change or repair Windows HLK by using Control Panel](#nocp)

-   [Cannot install HLK.AddLoggerEntries: Access is denied](#accessden)

-   [Cannot install the Windows HLK Client](#tsclient)

-   [Cannot install or remove the Windows HLK Controller](#contr)

-   [Client installation fails with error "This app can't run on your PC”](#appcantrun)

-   [Error: Failed to connect to database. Failed to connect to OM.](#noconn)

-   [Error: SQL client components are required for this operation](#sqlerror)

-   [Cannot install the Windows HLK Client](#tsclient)

-   [Error: There is already an object named DSLinkType in the database.](#databasedrop)

-   [Error: The database *database\_name* already exists.](#databasedrop)

-   [Error: Failed to create SQL database.](#databasedrop)

## <span id="cantbrowse"></span><span id="CANTBROWSE"></span>Cannot browse \\\\&lt;controller-name&gt;\\HLKInstall\\ on Studio or Client computer


If you cannot browse to the HLKInstall folder from the Windows HLK Studio or Client, review the setup and configuration information in the [Step 1: Install Controller and Studio on the test server](..\getstarted\step-1-install-controller-and-studio-on-the-test-server.md) topic.

## <span id="nocp"></span><span id="NOCP"></span>Cannot change or repair Windows HLK by using Control Panel


If you try to change or repair the Windows HLK by using Control Panel, you receive an error message that the repair failed. To change or repair your Windows HLK installation, use Control Panel to uninstall **Windows Hardware Certification Kit**, and then reinstall the Windows HLK See [Step 1: Install Controller and Studio on the test server](..\getstarted\step-1-install-controller-and-studio-on-the-test-server.md).

## <span id="accessden"></span><span id="ACCESSDEN"></span>Cannot install HLK.AddLoggerEntries: Access is denied


In rare cases, Windows HLK setup might fail just before it completes. If you look at the Windows HLK Controller log, CA AddLoggerEntries appears with an **Access is denied** error. If this happens, run HLKSetup.exe again to see if the Windows HLK installs successfully. If setup fails again, see [Windows HLK Support](windows-hlk-support.md) for instructions about how to contact Support. Include the \*HLKControllerx86\_en\_us.log file from the %temp%\\hlk folder. For information about how to review the Windows HLK Controller log file, see [To review the Windows HLK Controller log file](#contr).

## <span id="tsclient"></span><span id="TSCLIENT"></span>Cannot install the Windows HLK Client


If you cannot install the Windows HLK Client, review the installation info in the [Step 2: Install Client on the test system(s)](..\getstarted\step-2--install-client-on-the-test-system-s-.md) topic and make sure that you follow these instructions.

If you still cannot install the Windows HLK Client, locate these Client log files in the **%TEMP%** folder. See [Windows HLK Support](windows-hlk-support.md) for information about how to contact Support, and share the following client log files with Microsoft Support:

-   WLKInstall.log

-   Windows Hardware Certification Kit Client\_Install.log

-   Windows Driver Testing Framework (WDTF) Runtime Libraries\_Install.log

-   Application Verifier x64 External Package\_Install.log

-   WPTx64\_Install.log

## <span id="contr"></span><span id="CONTR"></span>Cannot install or remove the Windows HLK Controller


If you encounter issues installing the Windows HLK Controller, confirm the following:

-   The operating system uses the English language (en-us) version of Windows Server 2008 R2 x64 or Windows Server® 2012 and is not running as a domain controller.

-   The system language is set to US English. To do this, click **Region and Language** in **Control Panel**, click the **Administrative tab**, click **Change system locale**, and then select **English (United States)**.

If you cannot install or remove the Windows HLK Controller, review the controller log file that is located in the %temp%\\HLK folder.

**To review the Windows HLK Controller log file**

1.  At a command prompt, type **%HomeDrive%**, and then press **Enter**.

2.  Type **cd %temp%\\HLK**, and then press **Enter**.

3.  Type **dir \*HLKControllerx86\_en\_us.log**, and then press **Enter**.

4.  Open the log file in a text editor such as Notepad.

    >[!NOTE]
    >  
    If more than one file ends in HLKControllerx86\_en\_us.log, open the newest file. To open the log file in Notepad from the command line, type **Notepad**, the full file name, and then press **Enter**.

     

5.  Search for **return value 3** to see which action failed. Error information is located a few lines above the string **return value 3**.

    ``` syntax
    MSI (s) (F4:74) [18:58:28:187]: Executing op: ActionStart(Name=CreateStandaloneEnterprise,,)
    MSI (s) (F4:74) [18:58:28:187]: Executing op: CustomActionSchedule(Action=CreateStandaloneEnterprise,ActionType=17409,Source=BinaryData,Target=CAQuietExec,CustomActionData="C:\Program Files (x86)\Windows Kits\8.0\Hardware Certification Kit\Controller\WTTStandaloneEnterpriseSetup.exe" "TEST-SERVER" "HLKJobs" "C:\StandaloneEnterprise")
    MSI (s) (F4:48) [18:58:28:187]: Invoking remote custom action. DLL: C:\Windows\Installer\MSI9E59.tmp, Entrypoint: CAQuietExec
    CAQuietExec:  Standalone Enterprise setup started by user TEST-SERVER\Administrator
    CAQuietExec:  Error::
    ************************************************************ERROR REPORT (Exception levels including inner exceptions. Level 0 denotes outermost exception)
    CAQuietExec:  
    CAQuietExec:  ------------START OF ERROR REPORT------------
    CAQuietExec:  
    CAQuietExec:  Level            : 0
    CAQuietExec:  Error Message    : Error while creating new data store  'HLKJobs' .
    CAQuietExec:  Source           : Void CreateEnterprise(Microsoft.DistributedAutomation.DSLink, Microsoft.DistributedAutomation.ServiceCollection, Boolean)
    CAQuietExec:  Inner Exception  : System.Runtime.InteropServices.COMException (0x80041432): Cannot create file 'C:\Program Files (x86)\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\DATA\HLKJobs.mdf' because it already exists. Change the file path or the file name, and retry the operation.
    CREATE DATABASE failed. Some file names listed could not be created. Check related errors.
    CAQuietExec:     at Interop.SQLDMO.Databases.Add(_Database Object)
    CAQuietExec:     at Microsoft.DistributedAutomation.SqlDataStore.SqlDataStoreSetup.CreateDeploymentDataStore(ServiceCollection serviceList, DSLink newDSLink)
    CAQuietExec:  Call Stack       :    at Microsoft.DistributedAutomation.SqlDataStore.SqlDataStoreSetup.CreateEnterprise(DSLink identityDSLink, ServiceCollection serviceList, Boolean standaloneInstall)
    CAQuietExec:     at Microsoft.DistributedAutomation.EnterpriseSetup.EnterpriseSetupHelper.CreateEnterprise(EnterpriseConfiguration enterpriseConfig, DSLink dsLink, String setupFilePath, Boolean standaloneInstall)
    CAQuietExec:     at Microsoft.DistributedAutomation.EnterpriseSetup.Tools.CMain.Main(String args)
    CAQuietExec:  Trace            : 
    CAQuietExec:  
    CAQuietExec:  Level            : 1
    CAQuietExec:  Error Message    : Cannot create file 'C:\Program Files (x86)\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\DATA\HLKJobs.mdf' because it already exists. Change the file path or the file name, and retry the operation.
    CREATE DATABASE failed. Some file names listed could not be created. Check related errors.
    CAQuietExec:  Source           : Void Add(Interop.SQLDMO._Database)
    CAQuietExec:  Inner Exception  : 
    CAQuietExec:  
    CAQuietExec:  --------------END OF ERROR REPORT------------************************************************************
    CAQuietExec:  Error 0x80070001: Command line returned an error.
    CAQuietExec:  Error 0x80070001: CAQuietExec Failed
    CustomAction CreateStandaloneEnterprise returned actual error code 1603 (note this may not be 100% accurate if translation happened inside sandbox)
    MSI (s) (F4:74) [18:58:30:137]: User policy value 'DisableRollback' is 0
    MSI (s) (F4:74) [18:58:30:137]: Machine policy value 'DisableRollback' is 0
    Action ended 18:58:30: InstallFinalize. Return value 3
    ```

If the \*HLKControllerx86\_en\_us.log file includes **Error while creating new data store 'Jobs'**, complete these steps:

``` syntax
CAQuietExec:  Error Message    : Cannot create file 'C:\Program Files (x86)\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\DATA\HLKJobs.mdf' because it already exists. Change the file path or the file name, and retry the operation.
CREATE DATABASE failed. Some file names listed could not be created. Check related errors.
```

****

1.  Delete these files from the C:\\Program Files (x86)\\Microsoft SQL Server\\MSSQL10\_50.MSSQLSERVER\\MSSQL\\DATA folder:

    -   HLKJobs.mdf

    -   HLKJobs\_Log.ldf

2.  Reinstall the Windows HLK Controller. For info on how to do this, see [Step 1: Install Controller and Studio on the test server](..\getstarted\step-1-install-controller-and-studio-on-the-test-server.md)

## <span id="appcantrun"></span><span id="APPCANTRUN"></span>Client installation fails with error "This app can't run on your PC”


The system returns an error “This app can’t run on your PC” if you try to install Windows HLK Client software on a computer that is running Windows 8 RT. This is not a supported platform; however, you can install Windows HLK Client software on a computer that is running Windows RT 8.1.

## <span id="noconn"></span><span id="NOCONN"></span>Error: Failed to connect to database. Failed to connect to OM.


If you get an error message that states **Failed to connect to database. Failed to connect to OM** when you start Windows HLK Studio, make sure that your user account is added to the Windows HLK Controller. For instructions on how to add your user account to the Windows HLK Controller, see “Configure additional user accounts” in [Install a remote HLK Studio](install-a-remote-hlk-studio.md).

## <span id="sqlerror"></span><span id="SQLERROR"></span>Error: SQL client components are required for this operation


This error occurs when you attempt to install the full version of HLK (HLK Controller + Studio option), after you first downloaded the HLK product on a separate machine that already has the HLK Studio only option installed.

**Workaround:** Uninstall the HLK Studio-only version and try downloading and reinstalling the full HLK version again.

## <span id="databasedrop"></span><span id="DATABASEDROP"></span>HLK setup fails with a database-related error


This error can occur when uninstalling and then reinstalling HLK. When the new instance of HLK is installed, one of the following error messages appears:

-   There is already an object named DSLinkType in the database.
-   The database *database\_name* already exists.
-   Failed to create SQL database.

When uninstalling HLK, database uninstall can fail if the database is locked by another process. The HLK uninstall reports success, but the database is left behind.

To recover, follow these steps:

1.  From an elevated command prompt, run `SQLCMD -E`
2.  From the SQL Shell command line, enter the following:

    ``` syntax
    ALTER DATABASE WTTIdentity SET SINGLE_USER WITH ROLLBACK IMMEDIATE
    DROP DATABASE WTTIdentity
    GO
    ALTER DATABASE HLKJobs SET SINGLE_USER WITH ROLLBACK IMMEDIATE
    DROP DATABASE HLKJobs
    GO
    ```

3.  Verify that `C:\Program Files\Microsoft SQL Server\MSSQL(sql version).MSSQLSERVER\MSSQL\DATA` contains no files starting with WTTIdentity or HLKJobs
4.  Install the HLK

## <span id="related_topics"></span>Related topics


[Troubleshooting the Windows HLK Environment](troubleshooting-the-windows-hlk-environment.md)

 

 







