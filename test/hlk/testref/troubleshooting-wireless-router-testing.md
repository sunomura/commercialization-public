---
title: Troubleshooting Wireless Router Testing
description: Troubleshooting Wireless Router Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d775cd34-7653-4864-b571-823376accb30
---

# Troubleshooting Wireless Router Testing


To troubleshoot issues that occur with Device.Network tests, follow these steps:

-   Review the [Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md) topic.

-   Review the [Windows HLK release notes](http://go.microsoft.com/fwlink/?LinkID=236110) for current test issues.

-   For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

Use the following steps to test the ability of a computer to send higher bit rates over an Ethernet connection:

1.  Setup the hardware as shown below with only Ethernet connection.

2.  Assign the IP address to Machine **S** (for example: 10.0.0.2).

3.  Assign the IP address to Machine C (for example: 10.0.0.3).

4.  Open a command prompt and run Stats tool on Machine **C** with following parameters:

    **stats.exe –z DISCARD –i 20 –x 50 –y 30 –r 20000000 –c 3600 –l –h -u**

5.  Open the MS command prompt and run Stats tool at the Machine S with following parameters:

    **stats.exe –d 10.0.0.3 –r 20000000 –c 4200 –l –h -u**

6.  Observe the output of steps 4 and Step 5.

![ethernet troubleshooting](images/hck-win8-wireless-router-troubleshooting.png)

If the output of either step 4 or step 5 shows any failures then your machines cannot make bit rates using wireless adapters.

To manually add a wireless profile, use the following command:

**netsh wlan add profile filename=&lt;xmlfilename&gt; i=\***

For example, to add the 802\_11n\_wpa-psk.xml wireless profile:

1.  Click **Start**, click **Run**, and enter **cmd.exe**.

2.  Type **netsh wlan add profile filename=802\_11n\_wpa-psk.xml i=\***.

3.  Click **OK**.

>[!NOTE]
>  
Make sure that Wireless Profile XML file exists in the current directory or specify the full path.

 

## <span id="related_topics"></span>Related topics


[Device.Network Testing](device-network-tests.md)

 

 







