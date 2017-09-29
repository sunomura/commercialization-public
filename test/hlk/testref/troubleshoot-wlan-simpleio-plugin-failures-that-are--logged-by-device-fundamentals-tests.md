---
title: Troubleshoot WLAN SimpleIO plugin failures that are logged by Device Fundamentals tests
description: Troubleshoot WLAN SimpleIO plugin failures that are logged by Device Fundamentals tests
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e81a7a92-88c5-4464-9cef-c1d1acead9c5
---

# Troubleshoot WLAN SimpleIO plugin failures that are logged by Device Fundamentals tests


Device Fundamentals tests in Windows Hardware Lab Kit (Windows HLK) and [Windows Drivers Kit (WDK)](http://go.microsoft.com/fwlink/?LinkID=296487) use [Windows Device Testing Framework (WDTF)](http://go.microsoft.com/fwlink/?LinkID=296367)[SimpleIO plugins](http://go.microsoft.com/fwlink/?LinkID=296486) to test device-specific IO when they run. If a WDTF plugin exists for the type of device being tested, then the tests use the [IWDTFSimpleIOStressAction2 interface](http://go.microsoft.com/fwlink/?LinkID=299599) to test I/O on the device.

This article contains information that can help with troubleshooting failures that are logged by the WDTF WLAN SimpleIO plug-in when it is used to test IO on wireless network adapters during device and system testing in WDK and Windows HLK.

## <span id="configreq"></span><span id="CONFIGREQ"></span>Configuration requirements


The WLAN SimpleIO plug-in requires a basic WPA2-PSK wireless network that uses AES that it can connect to when it runs. The SSID and password of the wireless network must be passed in as parameters to the tests that require them. These parameters are named as follows in the tests that require them: **Wpa2PskAesSsid** and **Wpa2PskPassword**. The default values of the two parameters are **kitstestssid** and **password**, respectively.

## <span id="ov"></span><span id="OV"></span>Test coverage overview


The WLAN SimpleIO plug-in performs the following tests on the wireless adapter under test:

1.  Finds the Wlan interface that is under test by calling the [WlanEnumInterfaces function](http://go.microsoft.com/fwlink/?LinkID=296597).

2.  Deletes the test profile that is named WDTFWlanTestProfile (if it exists) by calling the [WlanGetProfile() function](http://go.microsoft.com/fwlink/?LinkID=296598) and the [WlanDeleteProfile() function](http://go.microsoft.com/fwlink/?LinkID=296599).

3.  Creates a new test profile named **WDTFWlanTestProfile** by calling the [WlanSetProfile() function](http://go.microsoft.com/fwlink/?LinkID=296600) and by using a profile XML. The profile uses the SSID and password of the wireless network as input parameters to the test.

4.  Connects to the newly created profile by calling the [WlanConnect() function](http://go.microsoft.com/fwlink/?LinkID=296601). Expect to receive a *connect complete* notification in 30 seconds.

5.  Checks for connectivity by calling the [INetworkListManager::GetConnectivity method](http://go.microsoft.com/fwlink/?LinkID=296604) of the [Network List Manager](http://go.microsoft.com/fwlink/?LinkID=296603) API, and looks for [NLM\_CONNECTIVITY enumeration](http://go.microsoft.com/fwlink/?LinkID=296605) NLM\_CONNECTIVITY\_IPV4\_INTERNET or NLM\_CONNECTIVITY\_IPV4\_LOCALNETWORK flags to be set. The plug-in calls the **GetConnectivity()** function several times (if required) as it waits for a connection, before it eventually times out and reports an error.

6.  Calls the [GetAdaptersInfo() function](http://go.microsoft.com/fwlink/?LinkID=296606) to determine the gateway address that corresponds to the test adapter.

7.  Opens an ICMP handle by calling [IcmpCreateFile() function](http://go.microsoft.com/fwlink/?LinkID=296607), and calls an internal function in a loop for several minutes that pings the IPv4 gateway address (by using the [IcmpSendEcho() function](http://go.microsoft.com/fwlink/?LinkID=296608) with one-second timeout) 500 times each time it is called, and logs an error message if at any time it is called, the failure rate is &gt;10%.

8.  Disconnects from the network by calling the [WlanDisconnect() function](http://go.microsoft.com/fwlink/?LinkID=296602).

9.  Deletes the test profile by calling the [WlanGetProfile() function](http://go.microsoft.com/fwlink/?LinkID=296598) and the [WlanDeleteProfile() function](http://go.microsoft.com/fwlink/?LinkID=296599).

## <span id="guidance"></span><span id="GUIDANCE"></span>Troubleshooting guidance


### <span id="Identify_failures_that_are_logged_by_the_WLAN_SimpleIO_plugin"></span><span id="identify_failures_that_are_logged_by_the_wlan_simpleio_plugin"></span><span id="IDENTIFY_FAILURES_THAT_ARE_LOGGED_BY_THE_WLAN_SIMPLEIO_PLUGIN"></span>Identify failures that are logged by the WLAN SimpleIO plugin

The error messages logged by the plug-in will contain the text “WirelessPlugin:”. The text that immediately follows “WirelessPlugin:” provides more context about the errors. For example:

``` syntax
WDTF_SIMPLE_IO            : ERROR :  - Open(802.11n USB Wireless LAN Card USB\VID_XXXX&PID_XXXX\5&35DEE9D9&0&5 ) Failed : WirelessPlugin: ConnectToTestProfile() - Failed to connect to test profile; Reason string: "The specific network is not available." HRESULT=0x80004005
```

### <span id="General_troubleshooting_guidance"></span><span id="general_troubleshooting_guidance"></span><span id="GENERAL_TROUBLESHOOTING_GUIDANCE"></span>General troubleshooting guidance

We recommend that you follow troubleshooting steps in the listed order:

1.  Review the test documentation to understand the test scenario.

2.  Review [Test coverage overview](#ov) to understand how the plugin tests a device or driver.

3.  Carefully review log entries that precede the error message, and the error message itself, to understand the test scenario and the reason for the failure.

4.  Troubleshoot the router setup. Make sure that you can manually connect to the router, that you can ping the gateway address after making the connection, and that the router is in range to the test computer. If the router fails any of these tests, reset the router.

5.  Enable tracing in the test driver and review driver traces from the time when the test logged the error(s).

6.  Enable **WLAN OS tracing** and review traces that are logged from the time when the logged the error(s). For more information about WLAN OS tracing, see [Tools for Troubleshooting using Network Tracing in Windows 7](http://go.microsoft.com/fwlink/?LinkID=296757).

In some cases, it is helpful to run the failing test manually from a command line (without using Windows HLK or WDK), and then reviewing the plug-in’s WPP traces. See [How to run tests from the command line](#cmd) and [View WLAN plug-in traces](#view).

## <span id="cmd"></span><span id="CMD"></span>How to run tests from the command line


We recommend that you use a Windows HLK Client to run tests manually because Windows HLK clients have WDTF installed on them. Follow the steps in **How to run the Windows HLK device fundamentals tests on the command line**. Enable Driver Verifier on Ndis.sys and the test Wi-Fi driver.

## <span id="view"></span><span id="VIEW"></span>View WLAN plug-in traces


The WLAN plugin uses WPP tracing to trace information and errors that you might find useful when you investigate failures that are logged by the WLAN plug-in. See [Collect and View Windows Device Testing Framework (WDTF) Traces](collect-and-view-windows-device-testing-framework--wdtf--traces.md) for instructions on how to collect and view WDTF traces.

>[!NOTE]
>  
**WDTF\_Action\_SimpleIO\_Wireless** is the name of the provider that you can use for filtering.

 

## <span id="Sample_trace_output"></span><span id="sample_trace_output"></span><span id="SAMPLE_TRACE_OUTPUT"></span>Sample trace output


``` syntax
                               -->this(047BB318):?FinalConstruct@CWirelessImpl@@QEAAJXZ(void)
                               <--this(047BB318):?FinalConstruct@CWirelessImpl@@QEAAJXZ(): S_OK
                               o->this(047BB318):?SetTarget@CWirelessImpl@@UEAAJPEAUITarget@@UtagVARIANT@@@Z(pMainTarget = 0476BBAC, MoreTargets = 8)
                                    INFO:Calling WlanOpenHandle() function
                                    INFO:Calling WlanEnumInterfaces() function to find wlan interface under test: N300 USB Network Adapter" ({4138C082-E821-433C-ABB8-6FF864BF80B5})"
                                    INFO:Found 1 wlan interfaces in total
                                    INFO:Processing wlan interface: N300 USB Network Adapter""
                                    INFO:Found the wlan interface under test!
                                    INFO:Interface information: Interface Guid: {4138C082-E821-433C-ABB8-6FF864BF80B5}; Interface State: disconnected""
                               o<-this(047BB318):?SetTarget@CWirelessImpl@@UEAAJPEAUITarget@@UtagVARIANT@@@Z(): S_OK
           o->this(047BB318):?Open@CWirelessImpl@@UEAAJXZ(void)
                INFO:Calling WlanOpenHandle() function
                -->this(047BB318):?FindAndDeleteTestProfile@CWirelessImpl@@AEAAJXZ(void)
                     INFO:Test profile WDTFWlanTestProfile" doesn't exist"
                o<-this(047BB318):?FindAndDeleteTestProfile@CWirelessImpl@@AEAAJXZ(): S_OK
                -->this(047BB318):?CreateTestProfile@CWirelessImpl@@AEAAJXZ(void)
                     INFO:Calling WlanSetProfile() with a profile XML to create a profile with name: WDTFWlanTestProfile"
                o<-this(047BB318):?CreateTestProfile@CWirelessImpl@@AEAAJXZ(): S_OK
                -->this(047BB318):?ConnectToTestProfile@CWirelessImpl@@AEAAJXZ(void)
                     INFO:Calling WlanRegisterNotification() to get notified of connect complete event
                     INFO:Calling WlanConnect() to connect to test profile with name: WDTFWlanTestProfile""
                     INFO:Waiting to receive connect complete notification
                     INFO:Received connect complete notification: 0
                     INFO:Calling WlanRegisterNotification() to unregister from notifications
                o<-this(047BB318):?ConnectToTestProfile@CWirelessImpl@@AEAAJXZ(): S_OK
                INFO:Calling an internal helper function to check for the connectivity state of the network connection
                -->this(047BB318):?CheckForConnectivity@CWirelessImpl@@AEAAJPEA_N@Z(void)
                     INFO:Creating an instance of the NLM COM object
                     INFO:Calling NLM GetNetworkConnections() to get a list of network connections
                     INFO:Iterating through the network connections found looking for the connection corresponding to the test adapter ({4138C082-E821-433C-ABB8-6FF864BF80B5})
                     INFO:Calling NLM GetAdapterId() on a network connection found
                     INFO:Calling NLM GetAdapterId() on a network connection found
                     INFO:Found a network connection using the test adapter!
                     INFO:Calling NLM GetConectivity() on a network connection using the test adapter
                     INFO:NLM GetConectivity() reported the following connectivity state: 66
                     INFO:NLM GetConectivity() reported IPv4 connectivity!
                o<-this(047BB318):?CheckForConnectivity@CWirelessImpl@@AEAAJPEA_N@Z(): S_OK
                -->this(047BB318):?RefreshIPInfo@CWirelessImpl@@AEAAJXZ(void)
                     INFO:Calling GetAdaptersInfo() function to find IP address info for adapter {4138C082-E821-433C-ABB8-6FF864BF80B5}""
                     INFO:Found the adapter we are looking for!
                     INFO:Adapter Info: Index: 4, IPv4 Address: 192.168.1.147, Gateway Address: 192.168.1.1
                o<-this(047BB318):?RefreshIPInfo@CWirelessImpl@@AEAAJXZ(): S_OK
                INFO:Calling IcmpCreateFile() function
                INFO:Pinging gateway (192.168.1.1) 10 times
                -->this(047BB318):?TestPingGateway@CWirelessImpl@@AEAAJHH@Z(numPings: 10)
                     INFO:Calling IcmpSendEcho() to ping gateway (192.168.1.1) 10 times with a random input buffer of size 255 and a timeout value of 1000 milliseconds
                o<-this(047BB318):?TestPingGateway@CWirelessImpl@@AEAAJHH@Z(): S_OK
           o<-this(047BB318):?Open@CWirelessImpl@@UEAAJXZ(): S_OK
           o->this(047BB318):?RunIO@CWirelessImpl@@UEAAJXZ(void)
                -->this(047BB318):?TestPingGateway@CWirelessImpl@@AEAAJHH@Z(numPings: 500)
                     INFO:Calling IcmpSendEcho() to ping gateway (192.168.1.1) 500 times with a random input buffer of size 255 and a timeout value of 1000 milliseconds
                o<-this(047BB318):?TestPingGateway@CWirelessImpl@@AEAAJHH@Z(): S_OK
           o<-this(047BB318):?RunIO@CWirelessImpl@@UEAAJXZ(): S_OK
           o->this(047BB318):?RunIO@CWirelessImpl@@UEAAJXZ(void)
                -->this(047BB318):?TestPingGateway@CWirelessImpl@@AEAAJHH@Z(numPings: 500)
                     INFO:Calling IcmpSendEcho() to ping gateway (192.168.1.1) 500 times with a random input buffer of size 255 and a timeout value of 1000 milliseconds
                o<-this(047BB318):?TestPingGateway@CWirelessImpl@@AEAAJHH@Z(): S_OK
           o<-this(047BB318):?RunIO@CWirelessImpl@@UEAAJXZ(): S_OK
...
...
...
           o->this(047BB318):?Close@CWirelessImpl@@UEAAJXZ(void)
                -->this(047BB318):?DisconnectFromTestProfile@CWirelessImpl@@AEAAJXZ(void)
                     INFO:Calling WlanDisconnect() to disconnect
                o<-this(047BB318):?DisconnectFromTestProfile@CWirelessImpl@@AEAAJXZ(): S_OK
                -->this(047BB318):?FindAndDeleteTestProfile@CWirelessImpl@@AEAAJXZ(void)
                     INFO:Calling WlanDeleteProfile() to delete the previously created test profile with name WDTFWlanTestProfile""
                o<-this(047BB318):?FindAndDeleteTestProfile@CWirelessImpl@@AEAAJXZ(): S_OK
           o<-this(047BB318):?Close@CWirelessImpl@@UEAAJXZ(): S_OK
```

## <span id="related_topics"></span>Related topics


[Troubleshooting Device Fundamentals Reliability Testing by using the Windows HLK](troubleshooting-device-fundamentals-reliability-testing-by-using-the-windows-hck.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

[Windows HLK Support](..\user\windows-hlk-support.md)

 

 







