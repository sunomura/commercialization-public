---
title: HLK Mobile Testing Tools and Utilities
description: Several command line tools are provided with the HLK for onboarding and device control.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: EA02C03A-488E-4D28-9992-7AC37B4BCF0D
---

# HLK Mobile Testing Tools and Utilities


Several command line tools are provided with the HLK for onboarding and device control.

## <span id="In_this_topic"></span><span id="in_this_topic"></span><span id="IN_THIS_TOPIC"></span>In this topic


-   [KitsDeviceDetector.exe](#kitsdevicedetector)
-   [AriesUtil.exe](#ariesutil)

## <span id="kitsdevicedetector"></span><span id="KITSDEVICEDETECTOR"></span>KitsDeviceDetector.exe


KitsDeviceDetector is used during the [Mobile Test system onboarding process](..\getstarted\hlk-proxy-client-getting-started-guide.md).

### <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage

``` syntax
KitsDeviceDetector.exe /<parameter>:<parameter value> …
```

***Supported parameters***

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>/ImagePath:&lt;Path to image.ffu&gt;</td>
<td>Optional. If supplied, the image will be flashed to the device.</td>
</tr>
<tr class="even">
<td>/ImageProfile:&lt;Default|Health|Retail&gt;</td>
<td>Optional. Valid types are Default, Health, Retail.</td>
</tr>
<tr class="odd">
<td>/LowCost:&lt;true/false&gt;</td>
<td>Optional. Informs the HLK that we are testing a low cost device.</td>
</tr>
<tr class="even">
<td>/SDMemory:&lt;true/false&gt;</td>
<td>Optional. Informs the HLK tests that the device has an additional SD memory card.</td>
</tr>
<tr class="odd">
<td>/SDCardImageInstalled</td>
<td>Optional.</td>
</tr>
<tr class="even">
<td>/DeviceName:&lt;device name&gt;</td>
<td>Required when onboarding USB connected phone.</td>
</tr>
<tr class="odd">
<td>/DeviceId:&lt;device ID&gt;</td>
<td>Required when onboarding USB connected phone.</td>
</tr>
<tr class="even">
<td>/DeviceMacAddress:&lt;Device MAC address&gt;</td>
<td>Optional. Derived from DeviceId when onboarding USB connected phone.</td>
</tr>
<tr class="odd">
<td>/?</td>
<td>Prints the help menu.</td>
</tr>
<tr class="even">
<td>/logical:&lt;logical connection&gt;</td>
<td>Optional. Specifies the logical connection DLL. Default value is WPConLC.dll.</td>
</tr>
<tr class="odd">
<td>/physical:&lt;physical connection&gt;</td>
<td>Specifies the physical connection DLL. Optional with Aries connected devices. Required with USB connected devices.</td>
</tr>
<tr class="even">
<td>/machinepool:&lt;machine pool&gt;</td>
<td>Required. Name of the machine pool to place the onboarded device.</td>
</tr>
<tr class="odd">
<td>(/DeviceFilters:&lt;comma-delimited-list&gt;)</td>
<td><div class="alert">
<strong>Note</strong>  /DeviceFilters only applies to certain physical connection plugins. The value should be a comma or semi-colon delimited list of devices to limit the scope of discovery.
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

***Examples***

``` syntax
KitsDeviceDetector /ImagePath:\\servername\images\image.ffu
            /devicefilters:device1,device2 /ImageProfile:Default
            /LowCost:true /SDMemory:true
```

\[Using USB-attached device\]

``` syntax
KitsDeviceDetector /Physical:Fake_PC.dll
            /machinepool:$\User
            /DeviceName:my-device
            /DeviceID:00000011-abc1-abc1-0000-000000000000
```

## <span id="ariesutil"></span><span id="ARIESUTIL"></span>AriesUtil.exe


AriesUtil.exe enables initial device discovery and provides a means to carry out operations on the Aries dongle or connected device. The tool exposes the following capabilities:

-   Send a discovery broadcast
-   Enumerate all Aries that have been associated / registered with this host
-   Get the firmware version of the Aries
-   Set the port used to route debug messages from the device to the host
-   Set the port used to route log messages from the Aries itself to the host
-   Power cycle the attached device
-   Power cycle the Aries itself
-   Flash an image to the attached device
-   Flash firmware to the Aries itself

### <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage

``` syntax
AriesUtil.exe <action> [action-arguments ...]
```

***Supported actions***

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Action</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Help [&lt;action-name&gt;]</td>
<td>Display general help, or help for a specific command.</td>
</tr>
<tr class="even">
<td>Enumerate</td>
<td>List Aries that have been registered with this host.</td>
</tr>
<tr class="odd">
<td>Discover [/Aries:&lt;aries-names&gt;] [/Adapter:&lt;adapter&gt;] [/TTL:&lt;ttl&gt;] [/TimeoutSec:(&lt;seconds&gt;|infinite) | /TimeoutMin:(&lt;minutes&gt;|infinite)] [/BroadcastAddr:&lt;addr&gt;][/BroadcastPort:&lt;port&gt;] [/ListenPort:&lt;port&gt;]</td>
<td><p>List the Aries that respond to a discovery broadcast.</p>
<p>The most common use case will specify no arguments.</p>
<p></p>
<dl>
<dt><span id="_Aries"></span><span id="_aries"></span><span id="_ARIES"></span><strong>/Aries</strong></dt>
<dd><p>Use to specify a filter list of Aries to look for responses from.</p>
<ul>
<li>Once all specified Aries are found the discovery can end before the timeout expires.</li>
<li>If not specified, then discovery will proceed to list any Aries that respond until the timeout expires.</li>
<li>The argument value can be a single Aries name, or a comma or semi-colon delimited list of Aries names. It can also be the wildcard asterisk (*) character, in which case all Aries registered on the current host will be considered.</li>
</ul>
</dd>
<dt><span id="_Adapter"></span><span id="_adapter"></span><span id="_ADAPTER"></span><strong>/Adapter</strong></dt>
<dd><p>Use to specify the network adapter to issue the discovery broadcast across.</p>
</dd>
<dt><span id="_TTL"></span><span id="_ttl"></span><strong>/TTL</strong></dt>
<dd><p>Use to specify time-to-live of the discovery broadcast.</p>
</dd>
<dt><span id="_TimeoutSec"></span><span id="_timeoutsec"></span><span id="_TIMEOUTSEC"></span><strong>/TimeoutSec</strong></dt>
<dd><p>Use to specify the discovery broadcast timeout in seconds.</p>
</dd>
<dt><span id="_TimeoutMin"></span><span id="_timeoutmin"></span><span id="_TIMEOUTMIN"></span><strong>/TimeoutMin</strong></dt>
<dd><p>Use to specify the discovery broadcast timeout in minutes.</p>
</dd>
<dt><span id="_BroadcastAddr"></span><span id="_broadcastaddr"></span><span id="_BROADCASTADDR"></span><strong>/BroadcastAddr</strong></dt>
<dd><p>Use to specify the discovery broadcast IP address to send to.</p>
</dd>
<dt><span id="_BroadcastPort"></span><span id="_broadcastport"></span><span id="_BROADCASTPORT"></span><strong>/BroadcastPort</strong></dt>
<dd><p>Use to specify the discovery broadcast destination port to send to.</p>
</dd>
<dt><span id="_ListenPort"></span><span id="_listenport"></span><span id="_LISTENPORT"></span><strong>/ListenPort</strong></dt>
<dd><p>Use to specify the discovery broadcast response port to listen on.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td>GetFirmwareVersion /Aries:&lt;aries-name&gt;</td>
<td><p>Gets the firmware version currently installed on the specified Aries.</p>
<p>The /Aries argument value can be a single Aries name, or a comma or semi-colon delimited list of Aries names. It can also be the wildcard asterisk (*) character, in which case all Aries registered on the current host will be selected.</p></td>
</tr>
<tr class="odd">
<td>MapDebugPort /Aries:&lt;aries-name&gt; /Port:&lt;port-number&gt;</td>
<td>Sets debug output for the device attached to the Aries to be routed to the local host on the specified port.</td>
</tr>
<tr class="even">
<td>MapSysLogPort /Aries:&lt;aries-name&gt; /Port:&lt;port-number&gt; [/Frequency:&lt;minutes&gt;] [/Verbosity:&lt;Critical|Error|Warning|Informational&gt;]</td>
<td><p>Sets SysLog output for the device attached to the Aries to be routed to the local host on the specified port. The Frequency option controls how often the Aries will broadcast its own health heartbeat, which will be 5 minutes by default.</p>
<p>Verbosity controls the maximum log level that will be displayed. Informational is the default.</p></td>
</tr>
<tr class="odd">
<td>ResetDevice /Aries:&lt;aries-name&gt; [/AutoSkip:&lt;true|false&gt;]</td>
<td>Resets the device attached to the specified Aries. By default, AutoSkip is turned off.</td>
</tr>
<tr class="even">
<td>ResetAries /Aries:&lt;aries-name&gt; [/Wait:&lt;seconds&gt;] [/SkipFail]</td>
<td><p>Power cycle the Aries aries itself. If the /Wait option is specified, the tool will wait for up to the specified number of seconds for the Aries to come back online before exiting.</p>
<p>The /Aries argument value can be a single Aries name, or a comma or semi-colon delimited list of Aries names. It can also be the wildcard asterisk (*) character, in which case all Aries registered on the current host will be selected.</p>
<p>If the /SkipFail argument is specified, any failures encountered during the operation will be ignored until the entire Aries list has been processed.</p></td>
</tr>
<tr class="odd">
<td>FlashDevice /Aries:&lt;aries-name&gt; /ImagePath:&lt;path-to-image.ffu&gt;</td>
<td>Flashes an FFU image onto the device attached to the specified Aries.</td>
</tr>
<tr class="even">
<td>FlashAries /Aries:&lt;aries-name&gt; /App:&lt;path-to-app-file&gt; [/MLO:&lt;path-to-mlo-file&gt;] [/Wait:&lt;seconds&gt;] [/SkipFail]</td>
<td><p>Flashes a firmware update to the Aries itself.</p>
<p>If the /Wait option is specified, the tool will wait for up to the specified number of seconds for the Aries to come back online before exiting.</p>
<p>If the /MLO option is specified, the loader will be flashed to the Aries prior to the flashing the App.</p>
<p>The /Aries argument value can be a single Aries name, or a comma or semi-colon delimited list of Aries names. It can also be the wildcard asterisk (*) character, in which case all Aries registered on the current host will be selected.</p>
<p>If the /SkipFail argument is specified, any failures encountered during the operation will be ignored until the entire Aries list has been processed.</p></td>
</tr>
<tr class="odd">
<td>StartPowMon /Aries:&lt;aries-name&gt; [/OutFile:&lt;Output&gt;] [/Duration:&lt;seconds&gt;]</td>
<td><p>Starts a power monitoring session for the specified Aries if one does not yet exist.</p>
<p>Note that power monitoring is a blocking action. To stop an active power monitoring session a StopPowMon action must be invoked.</p>
<p>If the /OutFile option is specified, the name of the output file containing the power sampling data will be the value passed in rather than the default.</p>
<p>If the /Duration option is specified, then the power monitoring session will only last for the specified duration. The duration is in seconds.</p>
<p>The /Aries argument value can be a single Aries name only.</p></td>
</tr>
<tr class="even">
<td>StopPowMon /Aries:&lt;aries-name&gt;</td>
<td>Stops the active power monitoring session for the specified Aries if one exists.</td>
</tr>
<tr class="odd">
<td>SignalOn /Aries:&lt;aries-name&gt;</td>
<td>Turn on the LED pulsing for both the Aries and the Beagle Bone.</td>
</tr>
<tr class="even">
<td>SignalOff /Aries:&lt;aries-name&gt;</td>
<td>Turn off the LED pulsing for both the Aries and the Beagle Bone.</td>
</tr>
</tbody>
</table>

 

***Examples***

*Aries discovery:*

``` syntax
AriesUtil.exe Discover
```

*Flash an Aries-connect mobile device:*

``` syntax
AriesUtil.exe ...
```

*Turn on Autoskip:*

``` syntax
AriesUtil.exe ResetDevice /Aries:myaries [/Autoskip:true]
```

 

 






