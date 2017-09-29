---
title: Install a remote HLK Studio
description: Install a remote HLK Studio
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9e5262b8-f623-4497-b0e8-a71d38ad6faf
---

# Install a remote HLK Studio


You can optionally install HLK Studio on a separate computer. The computer must be able to connect to the installation folder that is shared from the HLK Controller computer. Therefore, before you can install HLK Studio, you must have already installed HLK Controller.

## <span id="Install_remote_HLK_Studio"></span><span id="install_remote_hlk_studio"></span><span id="INSTALL_REMOTE_HLK_STUDIO"></span>Install remote HLK Studio


-   From your remote computer, click **Start**, click **Run**, type **\\\\*ControllerName*\\HLKInstall\\Studio\\Setup.exe**, and then click **Yes**.

Replace **ControllerName** with the actual name of your controller. Completing this step will install, if not already present, .NET Framework 4.0 (Client Profile and Extended).

## <span id="Configure_additional_user_accounts"></span><span id="configure_additional_user_accounts"></span><span id="CONFIGURE_ADDITIONAL_USER_ACCOUNTS"></span>Configure additional user accounts


By default, the user account used to install the Controller is the only account that can run tests using HLK Studio. If you want to allow additional accounts to manage tests via remote HLK Studio, you must manually add each account to your Controller.

1.  On your Controller, add each account to the **Administrator group**.

2.  Open **HLK Manager**, click **Tools** &gt; **Management Console**, and then expand the **Users** node.

3.  Right-click **hlk\_dsowners**, select **New User**.

4.  Enter the account (DOMAIN\\accountname) or MACHINE\\account).

5.  Click **OK**.

## <span id="_Optional___Configure_Internet_Connection_Firewall__ICF_"></span><span id="_optional___configure_internet_connection_firewall__icf_"></span><span id="_OPTIONAL___CONFIGURE_INTERNET_CONNECTION_FIREWALL__ICF_"></span>(Optional): Configure Internet Connection Firewall (ICF)


If you choose to install HLK Studio on a computer other than the HLK Controller, you must configure the Internet Connection Firewall correctly on the HLK Controller, otherwise HLK Studio will be unable to connect to the HLK database.

This is only needed if the user account is correctly added, but is blocked by the firewall from connecting to the SQL server instance on a remote studio. This is usually in a workgroup scenario.

To configure ICF, complete the following task on the HLK Controller.

**Option 2: Add an exception to ICF**

1.  In the Control Panel, click System and Security, and then click Windows Firewall.

2.  On the left pane, click Advanced Settings.

3.  On the left pane, under Windows Firewall with Advanced Security on Local Computer, click Inbound Rules.

4.  On the right pane, under Actions, click New Rule to launch the New Inbound Rule Wizard.

5.  Make sure that the Program is selected, and then click Next.

6.  After the program path is selected, click Browse and browse to the location where **SqlServr.exe** is located. Usually that is: %Program Files (x86)\\Microsoft SQL Server\\MSSQL11.MSSQLSERVER\\MSSQL\\Binn\\sqlservr.exe

7.  Click OK, and then click OK again.

 

 






