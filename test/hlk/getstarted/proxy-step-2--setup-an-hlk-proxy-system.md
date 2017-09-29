---
title: Step 2 Setup an HLK Proxy System
description: Step 2 Setup an HLK Proxy System
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 25425C6A-D375-4C5A-9A91-5F596DB32E96
---

# Step 2: Setup an HLK Proxy System


Follow these steps on the machine you have designated as your Proxy system– this can be either the same machine as the HLK Controller or a separate machine running a Client or Server SKU.

>[!NOTE]
>  If a separate system is used as the Proxy client host, ensure that the Domain or Workgroup configuration matches the configuration of the HLK Controller. Account name and password of the proxy system should also match the HLK Controller.

 

1.  On the Proxy system (which may be the same machine as the HLK Controller), run setup.exe from the following location:
    -   \\\\&lt;ControllerName&gt;\\HLKInstall\\ProxyClient\\setup.exe

    >[!NOTE]
    >  Replace &lt;ControllerName&gt; with the name of the test server.

     

2.  The **WTT Proxy Setup** wizard appears. To start the wizard, choose **Next**.
3.  Select **Next** on the **Destination Folder** page.
4.  Select **Install** to proceed.
5.  Open an elevated command prompt and navigate to %ProgramFiles(X86)%\\WTTMobile\\Client\\
6.  Start the Proxy Service by running the following command from the elevated command prompt:

    ``` syntax
    WTTProxy.exe –console
    ```

7.  Leave the elevated command prompt window open.

 

 






