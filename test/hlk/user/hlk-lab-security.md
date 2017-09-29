---
title: HLK Lab Security
description: HLK Lab Security
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c625ae97-9c35-4d8d-be7d-948cef508635
---

# HLK Lab Security


Before you deploy Windows HLK, you should consider security requirements. There are two areas of certification testing that significantly affect security:

-   Enabling auto-logon functionality

    Do not change or create an autologon account, as this may cause Windows HLK to stop functioning properly. The Windows HLK handles this process automatically.

-   Running tests in an administrator role

## <span id="Additional_security_precautions"></span><span id="additional_security_precautions"></span><span id="ADDITIONAL_SECURITY_PRECAUTIONS"></span>Additional security precautions


In addition, be aware of the following security precautions and considerations:

-   Isolate Windows HLK computers on the network

    To prepare to deploy Windows HLK in your lab, you should isolate the computers that you intend to install it on. For example, do not allow those computers access to the Internet or your primary network. If any of your test systems can connect to a corporate network or the Internet, those connections should be disabled during testing. Alternately, put lab computers on their own private subnet. For more information about configuring a private subnet, search the [Windows XP Professional Resource Kit](http://go.microsoft.com/fwlink/p/?linkid=63109) for information about Configuring APIPA.

-   Use dedicated computers and reformat them before use

    Systems that are used for testing should not store sensitive data or be used (or have been used in the past) for company-provided services (such as a Web server, Dynamic Host Command Protocol \[DHCP\] server, or a backup domain controller \[BDC\]). If new systems are not available, then reformat and wipe clean all dedicated Windows HLK computers before installing Windows HLK and running the certification test to ensure that no sensitive information is inadvertently captured in the Windows HLK logs. For example, in the event of a kernel crash, the job log could record a full memory dump that might contain potentially sensitive information. For more information about cleaning your lab computers, see [Fdisk and Format a Hard Disk](http://go.microsoft.com/fwlink/p/?LinkId=236083). After you have cleaned the computer you must install the operating system you want the computer to run.

-   Use hardware and/or software firewalls

    When you install the Windows HLK controller and Windows HLK client, the installers will open TCP port 1771. Ensure that no other software running on a controller or client uses port 1771. The controller and client installers will prompt you to open this port in the Window's software firewall. However, if your lab includes non-Microsoft software firewalls or hardware firewalls, you must manually make sure that port 1771 is open. Otherwise, Windows HLK controllers will be unable to communicate with their clients and schedule them to run tests. If you use a hardware firewall, refer to the documentation that came with it to open TCP port 1771.

-   Set user permissions

    When you install the Windows HLK controller, its installer will create a network share and set the permissions for the share to allow access for Windows HLK clients. One folder inside the network share is for the Windows HLK client installer, and another folder is for the Windows HLK Studio installer. Another network share is created for clients to communicate job results back to the controller. You can increase security by allowing only testers and Windows HLK clients to connect to these shares across the network, which is another reason why you should isolate the computers of your lab on a private subnet.

-   Physically secure your lab

    You should enable auto-logon on Windows HLK clients. Therefore, wherever possible, test systems should be located in a locked room and should be physically available to testing and support personnel only. Enabling auto-logon is described in a bit more detail in the section that follows.

For more information about security and enabling automatic logon, see the following references:

-   [Microsoft Security](http://go.microsoft.com/fwlink/p/?linkid=11569)

-   [Microsoft TechNet](http://go.microsoft.com/fwlink/p/?linkid=10111)

 

 






