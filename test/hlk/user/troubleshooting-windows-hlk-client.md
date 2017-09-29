---
title: Troubleshooting Windows HLK Client
description: Troubleshooting Windows HLK Client
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 687d0235-37d6-432a-9d79-3d81ac31a028
---

# Troubleshooting Windows HLK Client


This topic describes how to troubleshoot issues with the Windows Hardware Lab Kit (Windows HLK) Client.

For help with problems that occur during Windows HLK Client setup, see [Troubleshooting Windows HLK Setup](troubleshooting-windows-hlk-setup.md).

**In this topic:**

-   [Cannot get a client computer out of Debug state](#debugstate)

-   [Cannot select tests after previous test fails](#prevfail)

-   [Client computer goes to sleep during a test](#sleep)

-   [Client computer is locked by an LLU account](#llulock)

-   [Client computers cannot communicate with the Windows HLK Controller](#clicommcntr)

-   [Client information in HLK Studio is inaccurate](#inaccdatastudio)

-   [Client software is not uninstalled from the test system](#nouninst)

-   [Error encountered while adding user &lt;domain\\username&gt;](#domerror)

-   [Error: Skipped as Public key is null for the machine](#nullkey)

-   [Job is stuck in the Scheduler](#stuckjob)

-   [Jobs do not run after reinstalling the Windows HLK Client](#jobsno)

-   [Multiple client systems are identified as the same system](#multcli)

-   [Remote Desktop cannot connect to a Windows HLK Client computer](#rem)

-   [Remove and reinstall the Windows HLK Client](#remcli)

-   [SQL Server updates cause Windows HLK Client to crash](#sqlserver)

-   [Unsupported scenarios](#unsupp)

-   [Watched system does not have a heartbeat](#watched)

-   [Windows 7 Clients do not enter the Ready state](#win7)

## <span id="debugstate"></span><span id="DEBUGSTATE"></span>Cannot get a client computer out of Debug state


**Problem.** The Client does not change from the **Debug** state to the **Ready** state, even after changing the state to **Reset** in Windows HLK Manager.

This problem can be caused by a lack of communication between the Windows HLK Controller computer and the Windows HLK Client computer, or by a trusted key mismatch between the two systems.

Try these solutions in the following order:

1.  Try the solutions in [Client computers cannot communicate with the Windows HLK Controller](#clicommcntr).

2.  Reinstall the Client using the steps in [Remove and reinstall the Windows HLK Client](#remcli).

## <span id="prevfail"></span><span id="PREVFAIL"></span>Cannot select tests after previous test fails


After a test fails, the checkboxes for the list of tests are dimmed and you cannot select additional tests.

If you select a target but cannot select any of the tests, the computer is not in a ready state.

Go to the **Configuration** menu and put the computer in a ready state.

## <span id="sleep"></span><span id="SLEEP"></span>Client computer goes to sleep during a test


An always on, always connected (AOAC) computer that is not an ARM machine can go to sleep during a test. To prevent this, run the following command from an elevated command prompt on each Windows HLK Client computer:

``` syntax
powercfg /setacvalueindex scheme_current sub_video videoidle 0 & Powercfg /setdcvalueindex scheme_current sub_video videoidle 0 & Powercfg /s scheme_current
```

## <span id="llulock"></span><span id="LLULOCK"></span>Client computer is locked by an LLU account


If a client computer is locked by a LLU account or is unresponsive, you must log on by using the correct credentials for the LLU account. The two main LLU accounts on a client computer are:

-   **Local Standard User account**

    The client computer uses this account to run tests that require local standard user access on the client computer and any other computers with which it communicates. The local administrator account credentials can also be used for tests of this type, but the additional privileges might not be necessary.

    -   **LLU Name.** LLU\_LSU

    -   **UserName.** *&lt;client machine name&gt;*\\WDKLclStdUsr

    -   **Password.** WDKStdTstUsr!

-   **Local Administrative User account**

    The client computer uses this account to run tests that require local administrator access on the client computer and any other computers with which it communicates.

    -   **LLU Name.** LLU\_LAU

    -   **UserName.** *&lt;client machine name&gt;*\\LLUAdminUser

    -   **Password.** Testpassword,1

## <span id="clicommcntr"></span><span id="CLICOMMCNTR"></span>Client computers cannot communicate with the Windows HLK Controller


If a client computer cannot communicate with the Windows HLK Controller, review the following problems and solutions:

-   Client computers do not appear in the **Machine List** in the Windows HLK **Manager Job Monitor** window.

-   Client computers can't connect to the Controller computer.

-   Client computers do not process jobs in the job Scheduler in Windows HLK Manager.

-   Client computers always go to the debug state, even after a reset.

Try these solutions in the following order:

1.  Review the steps in [Step 2: Install Client on the test computer(s)](..\getstarted\step-2--install-client-on-the-test-system-s-.md) and check basic networking connectivity between the two computers.

2.  Run the procedure [To change the Windows HLK Client to a Home or Private network](#win7).

3.  Make sure the Internet Connection Firewall (ICF) port for Windows HLK is open on both the Windows HLK Client and Windows HLK Controller computers.

    **To open an ICF port for Windows HLK in Windows 7**

    1.  Open Control Panel.

    2.  Click **System and Security** &gt;**Windows Firewall** &gt; **Advanced Settings** &gt; **Inbound Rules**.

    3.  Make sure that **WLK Client** is present and enabled.

    4.  If WLK Client isn't there, click **New Rule**, click **Port**, and then click **Next**.

    5.  Type **1771** in the **Specific local ports** box, click **Next** twice for **Allows the Connection**.

    6.  Leave all Profiles checked and click **Next**.

    7.  For Name, type **WLK Client** and then click **Finish**.

    **To open an ICF port for Windows HLK**

    1.  Open Control Panel.

    2.  Click **Security** &gt;**Windows Firewall** &gt; **Change Settings**.

    3.  Click the **Exceptions** tab. Make sure that **WLK Client** is present and selected under **Programs and Services**.

    4.  If **WLK Client** does not appear, click **Add Port** and enter this information:

        -   In the **Name** box, type **WLK Client**.

        -   In the **Port number** box, type **1771**.

        -   Click the **TCP** button, and then click **OK**.

    5.  Return to the exceptions tab and make sure that the **WLK Client** check box is selected, and then click **OK**.

4.  Disable Internet Protocol security (IPsec)

    For Windows HLK Client and Windows HLK Controller computers to communicate, all computers must either be running IPsec or all computers must have IPsec disabled.

    **To disable IPsec**

    -   At a command prompt, type **net stop ipsec**, and then press Enter.

    **To change IPSec properties**

    1.  At a command prompt, type **services.msc**, and then press Enter. The Microsoft Management Console appears.

    2.  Double-click **IPsec Policy Agent** and change its **Startup Type** (**Automatic** | **Manual** | **Disabled**) and/or **Service Status** (**Start** | **Stop**).

## <span id="inaccdatastudio"></span><span id="INACCDATASTUDIO"></span>Client information in HLK Studio is inaccurate


The Windows HLK Client information that shows in Windows HLK Studio can be inaccurate if the gatherer data is not current. Inaccurate information can include the following data:

-   Missing or detected features.

-   Missing or extra tests.

-   Drivers that are included with the operating system are reported as not being included.

    Drivers that are not included with the operating system are reported as being included.

To work around this issue, perform the following steps:

1.  Restart the Windows HLK Client computer.

2.  (Optional) Delete the project in Windows HLK Studio.

3.  (Optional) Reset the status of the client computer in Windows HLK Manager Job Monitor.

4.  Close all instances of Windows HLK Studio and Windows HLK Manager.

5.  Restart Windows HLK Studio.

6.  Create a new project and add the Windows HLK Client computer to the machine pool.

## <span id="nouninst"></span><span id="NOUNINST"></span>Client software is not uninstalled from the test system


This problem occurs when the entry in the database for the Windows HLK Controller is deleted for the test system. After ten minutes or less, the client software sends out a new signal (heartbeat) and the controller generates a new client entry in the database. After the client entry appears, the client is visible in the **Configuration** screen in Windows HLK Studio; however, when you select the machine pool on the **Selection** tab, no targets are listed for the system.

To resolve this problem, get a gatherer to return some new data. You can do this by installing a driver or hardware or by restarting the client system.

## <span id="domerror"></span><span id="DOMERROR"></span>Error encountered while adding user &lt;domain\\username&gt;


When you try to create a user account for a domain user, the following error message appears:

Error encountered while adding user &lt;*domain\\username*&gt;

Cannot grant/remove permission for user on data store *controller name*: User *username* does not exist in domain *domain*. Please ensure that user name is valid or contact your network administrator.

The domain that the error message refers to is the local machine domain. You cannot create a user account for a domain user if you are logged onto the Windows HLK Studio computer as a local Administrator. You must log off and log back on as a domain user who has Administrator rights, and then create the user account for the domain user.

## <span id="nullkey"></span><span id="NULLKEY"></span>Error: Skipped as Public key is null for the machine


When you try to add a local logical user (LLU) to a client computer, the following error appears:

Skipped as Public key is null for the machine.

This error means that the Windows HLK Client did not install correctly. To fix this problem, uninstall and reinstall the Windows HLK Client. For more info, see [Remove and reinstall the Windows HLK Client](#remcli).

## <span id="stuckjob"></span><span id="STUCKJOB"></span>Job is stuck in the Scheduler


When you set up a job, Windows Scheduler searches for a client computer to run the job. The Scheduler considers all client computers in the machine pool that are available and capable of running the job.

When you use Windows HLK Manager Job Monitor to view the status of a job, the **Current Pipeline** column of the **Job Execution Status** pane displays the job status. If the **Current Pipeline** value for your job is **Scheduler**, and if this value hasn't changed for several minutes, make sure that a Windows HLK Client in the machine pool with a **Ready** status exists.

-   If no Windows HLK Client computers are ready to run jobs, see [Step 3: Create a machine pool](..\getstarted\step-3-create-a-machine-pool.md).

-   If Windows HLK Client computers are available to run the job, make sure that at least one Windows HLK Client computer is capable of running the job. Check the attributes of the Windows HLK Client computers and compare them with the job requirements.

-   If a job contains machine sets, confirm that there are enough Windows HLK Client computers to meet the requirements of all machine sets. Windows HLK schedules all of the Windows HLK Client computers at the same time.

If a job remains unchanged in the Scheduler, make sure that the SQL Server (**MSSQLSERVER**), **WLKSvc**, and **DTMSERVICE** services are started in services.msc.

## <span id="jobsno"></span><span id="JOBSNO"></span>Jobs do not run after reinstalling the Windows HLK Client


Previously scheduled jobs do not run if you have installed the Windows HLK Controller and Windows HLK Studio, scheduled some jobs, and then uninstalled and reinstalled the Windows HLK Client.

In this case, you must establish a new connection between the Windows HLK Client computer and the Windows HLK Controller computer by uninstalling and reinstalling the Client. For information on how to do this, see [Remove and reinstall the Windows HLK Client](#remcli).

## <span id="multcli"></span><span id="MULTCLI"></span>Multiple client systems are identified as the same system


Client systems are identified through a pair of hashes. These hashes are individually composed of the following data sets:

**Hash1:**

``` syntax
smbios UUID
smbios serial number
smbios manufacturer
smbios model
smbios SKU number
```

**Hash 2:**

``` syntax
mac address 0
driver 0 vendor
driver 0 product
driver 0 serial number
```

This characteristic allows you to change the hardware while retaining the same machine identifier. However, if the hashes are too similar between two (or more) different systems, the systems are identified as the same system. This causes the last system’s heart-beat to be the active client.

To prevent this from happening, the hash data should be unique for each client system. The easiest values to update are **smbios UUID** and **smbios serial number**.

You can see these values in the CLIENTMACHINE gatherer data. This log does not determine these values and modifying this log does not prevent or resolve the problem.

This log exists at **%SystemDrive%\\WLK\\JobsWorkingDir\\AssetCfg\\Log**.

## <span id="rem"></span><span id="REM"></span>Remote Desktop cannot connect to a Windows HLK Client computer


If Remote Desktop cannot connect to a Windows HLK Client computer, make sure that Remote Desktop is a Windows Firewall exception.

**To allow a Remote Desktop connection in Windows 7**

1.  Open Control Panel.

2.  Click **System and Security** &gt; **Windows Firewall** &gt; **Allow a program or feature through Windows Firewall**.

3.  Click the **Remote Desktop** check box, and then click **OK**.

**To allow a Remote Desktop connection in Windows Vista**

1.  Open Control Panel.

2.  System and Security **Security** &gt; **Windows Firewall** &gt; **Change Settings**.

3.  Click the **Exceptions** tab.

4.  Click the **Remote Desktop** check box, and then click **OK**.

## <span id="remcli"></span><span id="REMCLI"></span>Remove and reinstall the Windows HLK Client

>[!WARNING]
>  
Do not remove the Windows HLK Client as the first step in troubleshooting Windows HLK Client problems. If you reinstall the Windows HLK Client, any certification testing in progress is lost and you have to rerun all the tests in a new project.

 

**To remove and reinstall the Windows HLK Client**

1.  Uninstall the Windows HLK Client (**Control Panel** &gt; **Uninstall a program** &gt; **Windows Hardware Certification Kit Client**.)

2.  Start the Windows HLK Manager, go to **Explorers | Job Monitor**, right-click your computer, and then select **Change Status -&gt; Unsafe** to set the computer to the **Unsafe** state.

3.  Install the Windows HLK Client by using the steps in the [Step 2: Install Client on the test system(s)](..\getstarted\step-2--install-client-on-the-test-system-s-.md) topic.

4.  Wait for the computer to go into the **Manual** state in **HLK Manager | Job Monitor**, below the **Status** column.

5.  Go to **Explorers | Job Monitor**, right-click your computer, and then select **Change Status -&gt; Reset**.

6.  Wait for the computer to automatically return to the **Ready** state, or click **Refresh** in Windows HLK Manager.

## <span id="sqlserver"></span><span id="SQLSERVER"></span>SQL Server updates cause Windows HLK Client to crash


SQL Server updates can cause the Windows HLK Client to crash. To fix, disable automatic updates while running HLK tests:

-   Windows 10
    1.  Open the Settings app
    2.  Select Update & security
    3.  Select Windows Update
    4.  Choose Advanced Options
    5.  Choose the defer upgrades option
-   Pre-Windows 10
    1.  Open Control Panel
    2.  Select **Windows Update**
    3.  Select **Change settings**
    4.  Choose an option that disables automatic updates

## <span id="unsupp"></span><span id="UNSUPP"></span>Unsupported scenarios


The following scenarios are not supported by the Windows HLK Client:

-   **Multiple operating systems.** Installing multiple operating systems on a computer with the Windows HLK Client installed is not supported. If you have more than one operating system installed on a computer, and multiple instances of Windows HLK Client installed, you might cause errors than cannot be fixed without reinstalling the operating system.

    Only one instance of Windows HLK Client should be installed on the system under test. In this scenario, the system includes all related physical discs and partitions.

-   **Testing on multiple client computers.** If you are using multiple client computers to complete a test project, you must use the same client computers to complete and also package the test project in Windows HLK Studio. For example, if one computer is testing for Windows 7 x86 and another computer is testing for Windows 7 x64, you must complete and package all testing on each computer before you make any changes to a system or operating system. If you change anything about the client computer, you might invalidate the project and then have to restart the test by using a new project. You might need to restart your test project if you make any of these changes:

    -   Change the computer name

    -   Reinstall the Client

    -   Reinstall the operating system

    -   Move the computer from a DOMAIN to a WORKGROUP or from a WORKGROUP to a DOMAIN.

If you have one of the above unsupported scenarios on a Windows HLK Client computer, you might have no heartbeat, jobs stuck in the Scheduler, or jobs that do not run.

To re-establish a working test environment, change the Windows HLK Client system back to its original state to continue and complete the test submission. Optionally, uninstall and reinstall Windows HLK Controller and Windows HLK Client so that all systems are either joined to a domain or part of a workgroup.

## <span id="watched"></span><span id="WATCHED"></span>Watched system does not have a heartbeat


If you select a machine pool in configuration, and watch the test system from the configuration screen, the heart-beat, that is, the user interface (UI) time stamp, does not update.

This is a Windows HLK Studio UI issue. The system does continue to heart-beat, but the UI just does not update.

To update the heart-beat time stamp, switch machine pools.

## <span id="win7"></span><span id="WIN7"></span>Windows 7 Clients do not enter the Ready state


**Problem.** A test Windows HLK Client appears in the Default Test Pool and has a recent heartbeat, but when you change the state of the Client to **Reset**, the status does not change to **Ready** and it eventually changes to **Debug**.

If the test computer is connected to a public network, the Windows HLK Client does not enter the **Ready** state because the public network category is restrictive, and network discovery is turned off by default.

**Solution.** Change the network location of the Windows HLK Client.

**To change the Windows HLK Client to a Home or Private network**

1.  On the client computer, open Control Panel, click **Network and Internet**, and then click **View network status and tasks**.

2.  On Windows 7, if the network under **View your active networks** is set to **Public Network**, click **Public Network**, and then change it to **Home network**.

    -or-

    On Windows Vista, if the Network category (under **Network Details**) is set to **Public network**, click **Change**, and then click **Private**.

The Windows HLK Client status changes from **Reset** to **Ready**, and this action reinstalls the Windows HLK Client on the computer.

## <span id="related_topics"></span>Related topics


[Troubleshooting the Windows HLK Environment](troubleshooting-the-windows-hlk-environment.md)

 

 







