---
title: HLK Product Type Matrix
description: HLK Product Type Matrix
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 423551CF-D497-459F-AEE6-91DF229DAA0F
---

# HLK Product Type Matrix


The Windows 10 HLK Product Type Matrix lists all of the product types that can be included in the Windows Hardware Compatibility Program. Each product type defines features and requirements that must be met for program eligibility.

>[!NOTE]
>  
Some of the product types from the HCK for Windows 8/8.1 have been deprecated and must be submitted as **Other Devices** on Sysdev. The deprecated product types are included to enable you to obtain a unified signed driver by merging HCK and HLK packages together.

Please reference the matrix below prior to merging HCK and HLK packages.

 

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Active/Deprecated</th>
<th>Product Type</th>
<th>Required Features</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>3D Printer</p></td>
<td><p>Device.Imaging.3DPrinter.Base</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Accelerometer Sensor</p></td>
<td><p>Device.Input.Sensor.Accelerometer</p>
<p>Device.Input.Sensor.Base</p></td>
</tr>
<tr class="odd">
<td><p>System</p></td>
<td><p>Active</p></td>
<td><p>All In One</p></td>
<td><p>System.Client.Graphics</p>
<p>System.Client.PCContainer</p>
<p>System.Client.SystemConfiguration</p>
<p>System.Client.SystemPartition</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Firmware</p>
<p>System.Fundamentals.Graphics</p>
<p>System.Fundamentals.Graphics.DisplayRender</p>
<p>System.Fundamentals.Graphics.InternalDisplay</p>
<p>System.Fundamentals.PowerManagement</p>
<p>System.Fundamentals.Reliability</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Audio Device</p></td>
<td><p>Device.Audio.Base</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Audio Processing Objects</p></td>
<td><p>Device.Audio.APO</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Bluetooth Controller</p></td>
<td><p>Device.BusController.Bluetooth.Base</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Bluetooth Controller Non USB</p></td>
<td><p>Device.BusController.Bluetooth.Base</p>
<p>Device.BusController.Bluetooth.NonUSB</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Controller</p></td>
<td><p>Device.Audio.AudioController</p></td>
</tr>
<tr class="odd">
<td><p>System</p></td>
<td><p>Active</p></td>
<td><p>Convertible Tablet</p></td>
<td><p>System.Client.Digitizer.Touch</p>
<p>System.Client.Graphics</p>
<p>System.Client.PCContainer</p>
<p>System.Client.SystemPartition</p>
<p>System.Client.Tablet.Graphics</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Firmware</p>
<p>System.Fundamentals.Graphics</p>
<p>System.Fundamentals.Graphics.DisplayRender</p>
<p>System.Fundamentals.Graphics.InternalDisplay</p>
<p>System.Fundamentals.Input</p>
<p>System.Fundamentals.Reliability</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p></td>
</tr>
<tr class="even">
<td><p>System</p></td>
<td><p>Active</p></td>
<td><p>Desktop</p></td>
<td><p>System.Client.Graphics</p>
<p>System.Client.PCContainer</p>
<p>System.Client.SystemConfiguration</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Firmware</p>
<p>System.Fundamentals.Graphics</p>
<p>System.Fundamentals.Graphics.DisplayRender</p>
<p>System.Fundamentals.Reliability</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Digital Media Renderer</p></td>
<td><p>Device.Media.DMR.Audio</p>
<p>Device.Media.DMR.AV</p>
<p>Device.Media.DMR.Base</p>
<p>Device.Media.DMR.Image</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Digital Still Cameras</p></td>
<td><p>Device.Portable.Core</p>
<p>Device.Portable.DigitalCamera</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Digital Video Cameras</p></td>
<td><p>Device.Portable.Core</p>
<p>Device.Portable.DigitalVideoCamera</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Enterprise WSD Multi-Function Printer</p></td>
<td><p>Device.Imaging.Printer.Base</p>
<p>Device.Imaging.Printer.WSD</p>
<p>Device.Imaging.Scanner.Base</p></td>
</tr>
<tr class="odd">
<td><p>Filter</p></td>
<td><p>Active</p></td>
<td><p>File System</p></td>
<td><p>Filter.Driver.FileSystem</p></td>
</tr>
<tr class="even">
<td><p>Filter</p></td>
<td><p>Active</p></td>
<td><p>File System Anti Virus</p></td>
<td><p>Filter.Driver.AntiVirus</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Finger Print Reader</p></td>
<td><p>Device.Input.FingerPrintReader</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Game Controller</p></td>
<td><p>Device.Input.GameController.CommonController</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Generic Controller</p></td>
<td><p>Device.Input.GameController.GenericController</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Generic Portable Device</p></td>
<td><p>Device.Portable.Core</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Adapter WDDM1.0</p></td>
<td><p>Device.Graphics.AdapterBase</p>
<p>Device.Graphics.AdapterRender</p>
<p>Device.Graphics.WDDM</p>
<p>Device.Graphics.WDDM.Display</p>
<p>Device.Graphics.WDDM.DisplayRender</p>
<p>Device.Graphics.WDDM.Render</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Adapter WDDM1.1</p></td>
<td><p>Device.Graphics.AdapterBase</p>
<p>Device.Graphics.AdapterRender</p>
<p>Device.Graphics.WDDM</p>
<p>Device.Graphics.WDDM.Display</p>
<p>Device.Graphics.WDDM.DisplayRender</p>
<p>Device.Graphics.WDDM.Render</p>
<p>Device.Graphics.WDDM11</p>
<p>Device.Graphics.WDDM11.Display</p>
<p>Device.Graphics.WDDM11.DisplayRender</p>
<p>Device.Graphics.WDDM11.Render</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Adapter WDDM1.2</p></td>
<td><p>Device.Graphics.AdapterBase</p>
<p>Device.Graphics.AdapterRender</p>
<p>Device.Graphics.WDDM</p>
<p>Device.Graphics.WDDM.Display</p>
<p>Device.Graphics.WDDM.DisplayRender</p>
<p>Device.Graphics.WDDM.Render</p>
<p>Device.Graphics.WDDM11</p>
<p>Device.Graphics.WDDM11.Display</p>
<p>Device.Graphics.WDDM11.DisplayRender</p>
<p>Device.Graphics.WDDM11.Render</p>
<p>Device.Graphics.WDDM12</p>
<p>Device.Graphics.WDDM12.Display</p>
<p>Device.Graphics.WDDM12.DisplayRender</p>
<p>Device.Graphics.WDDM12.Render</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Adapter WDDM1.2 DisplayOnly</p></td>
<td><p>Device.Graphics.AdapterBase</p>
<p>Device.Graphics.WDDM</p>
<p>Device.Graphics.WDDM.Display</p>
<p>Device.Graphics.WDDM11</p>
<p>Device.Graphics.WDDM11.Display</p>
<p>Device.Graphics.WDDM12</p>
<p>Device.Graphics.WDDM12.Display</p>
<p>Device.Graphics.WDDM12.DisplayOnly</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Adapter WDDM1.2 RenderOnly</p></td>
<td><p>Device.Graphics.AdapterBase</p>
<p>Device.Graphics.AdapterRender</p>
<p>Device.Graphics.WDDM</p>
<p>Device.Graphics.WDDM.Render</p>
<p>Device.Graphics.WDDM11</p>
<p>Device.Graphics.WDDM11.Render</p>
<p>Device.Graphics.WDDM12</p>
<p>Device.Graphics.WDDM12.Render</p>
<p>Device.Graphics.WDDM12.RenderOnly</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Adapter WDDM1.3</p></td>
<td><p>Device.Graphics.AdapterBase</p>
<p>Device.Graphics.AdapterRender</p>
<p>Device.Graphics.WDDM</p>
<p>Device.Graphics.WDDM.Display</p>
<p>Device.Graphics.WDDM.DisplayRender</p>
<p>Device.Graphics.WDDM.Render</p>
<p>Device.Graphics.WDDM11</p>
<p>Device.Graphics.WDDM11.Display</p>
<p>Device.Graphics.WDDM11.DisplayRender</p>
<p>Device.Graphics.WDDM11.Render</p>
<p>Device.Graphics.WDDM12</p>
<p>Device.Graphics.WDDM12.Display</p>
<p>Device.Graphics.WDDM12.DisplayRender</p>
<p>Device.Graphics.WDDM12.Render</p>
<p>Device.Graphics.WDDM13</p>
<p>Device.Graphics.WDDM13.DisplayRender</p>
<p>Device.Graphics.WDDM13.Render</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Adapter WDDM1.3 DisplayOnly</p></td>
<td><p>Device.Graphics.AdapterBase</p>
<p>Device.Graphics.WDDM</p>
<p>Device.Graphics.WDDM.Display</p>
<p>Device.Graphics.WDDM11</p>
<p>Device.Graphics.WDDM11.Display</p>
<p>Device.Graphics.WDDM12</p>
<p>Device.Graphics.WDDM12.Display</p>
<p>Device.Graphics.WDDM12.DisplayOnly</p>
<p>Device.Graphics.WDDM13</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Adapter WDDM1.3 RenderOnly</p></td>
<td><p>Device.Graphics.AdapterBase</p>
<p>Device.Graphics.AdapterRender</p>
<p>Device.Graphics.WDDM</p>
<p>Device.Graphics.WDDM.Render</p>
<p>Device.Graphics.WDDM11</p>
<p>Device.Graphics.WDDM11.Render</p>
<p>Device.Graphics.WDDM12</p>
<p>Device.Graphics.WDDM12.Render</p>
<p>Device.Graphics.WDDM12.RenderOnly</p>
<p>Device.Graphics.WDDM13</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Tablet</p></td>
<td><p>Device.Input.Digitizer.Pen</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Gyroscope Sensor</p></td>
<td><p>Device.Input.Sensor.Base</p>
<p>Device.Input.Sensor.Gyroscope</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Hard Drive</p></td>
<td><p>Device.Storage.Hd</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Hardware Multifunction Transforms</p></td>
<td><p>Device.Streaming.HMFT</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Keyboard</p></td>
<td><p>Device.Input.Keyboard</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Keyboard Video Mouse Switch</p></td>
<td><p>Device.Input.Keyboard</p>
<p>Device.Input.PointDraw</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>LAN</p></td>
<td><p>Device.Network.DevFund</p>
<p>Device.Network.LAN.Base</p>
<p>Device.Network.LAN.PM</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>LAN (Server)</p></td>
<td><p>Device.Network.DevFund</p>
<p>Device.Network.LAN.Base</p>
<p>Device.Network.LAN.ChecksumOffload</p>
<p>Device.Network.LAN.LargeSendOffload</p>
<p>Device.Network.LAN.RSS</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>LAN CS</p></td>
<td><p>Device.Network.DevFund</p>
<p>Device.Network.LAN.Base</p>
<p>Device.Network.LAN.CS</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>LAN Virtual Machine (Server)</p></td>
<td><p>Device.Network.DevFund</p>
<p>Device.Network.LAN.Base</p>
<p>Device.Network.LAN.ChecksumOffload</p>
<p>Device.Network.LAN.LargeSendOffload</p>
<p>Device.Network.LAN.RSS</p>
<p>Device.Network.LAN.SRIOV</p>
<p>Device.Network.LAN.SRIOV.VF</p>
<p>Device.Network.LAN.VMQ</p></td>
</tr>
<tr class="odd">
<td><p>System</p></td>
<td><p>Active</p></td>
<td><p>Laptop</p></td>
<td><p>System.Client.Graphics</p>
<p>System.Client.PCContainer</p>
<p>System.Client.SystemConfiguration</p>
<p>System.Client.SystemImage</p>
<p>System.Client.SystemPartition</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Firmware</p>
<p>System.Fundamentals.Graphics</p>
<p>System.Fundamentals.Graphics.DisplayRender</p>
<p>System.Fundamentals.Graphics.InternalDisplay</p>
<p>System.Fundamentals.Input</p>
<p>System.Fundamentals.Reliability</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p></td>
</tr>
<tr class="even">
<td><p>System</p></td>
<td><p>Active</p></td>
<td><p>Laptop with Touch</p></td>
<td><p>System.Client.Digitizer.Touch</p>
<p>System.Client.Graphics</p>
<p>System.Client.PCContainer</p>
<p>System.Client.SystemConfiguration</p>
<p>System.Client.SystemImage</p>
<p>System.Client.SystemPartition</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Firmware</p>
<p>System.Fundamentals.Graphics</p>
<p>System.Fundamentals.Graphics.DisplayRender</p>
<p>System.Fundamentals.Graphics.InternalDisplay</p>
<p>System.Fundamentals.Input</p>
<p>System.Fundamentals.Reliability</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>LCD</p></td>
<td><p>Device.Display.Monitor</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Light Sensor</p></td>
<td><p>Device.Input.Sensor.ALS</p>
<p>Device.Input.Sensor.Base</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Location Sensor</p></td>
<td><p>Device.Input.Sensor.Base</p>
<p>Device.Input.Sensor.Location</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Media Player</p></td>
<td><p>Device.Portable.Core</p>
<p>Device.Portable.MediaPlayer</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Mobile Broadband CDMA</p></td>
<td><p>Device.Network.DevFund</p>
<p>Device.Network.MobileBroadband.CDMA</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Mobile Broadband GSM</p></td>
<td><p>Device.Network.DevFund</p>
<p>Device.Network.MobileBroadband.GSM</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Mobile Phone</p></td>
<td><p>Device.Portable.Core</p>
<p>Device.Portable.MobilePhone</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Monitor</p></td>
<td><p>Device.Display.Monitor</p></td>
</tr>
<tr class="odd">
<td><p>System</p></td>
<td><p>Active</p></td>
<td><p>Motherboard</p></td>
<td><p>System.Client.PCContainer</p>
<p>System.Fundamentals.DebugPort</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Motion Sensor Fusion</p></td>
<td><p>Device.Input.Sensor.Accelerometer</p>
<p>Device.Input.Sensor.Compass</p>
<p>Device.Input.Sensor.DeviceOrientation</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Multi-Function Printer</p></td>
<td><p>Device.Imaging.Printer.Base</p>
<p>Device.Imaging.Scanner.Base</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Near Field Proximity</p></td>
<td><p>Device.BusController.NFC</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Network Media Device DMR Audio</p></td>
<td><p>Device.Media.DMR.Audio</p>
<p>Device.Media.DMR.Base</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Network Media Device DMR AV</p></td>
<td><p>Device.Media.DMR.Audio</p>
<p>Device.Media.DMR.AV</p>
<p>Device.Media.DMR.Base</p>
<p>Device.Media.DMR.Image</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Optical Drive</p></td>
<td><p>Device.Storage.Optical</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Orientation Sensor</p></td>
<td><p>Device.Input.Sensor.Base</p>
<p>Device.Input.Sensor.DeviceOrientation</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Pen Digitizer</p></td>
<td><p>Device.Input.Digitizer.Pen</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Pointing Drawing</p></td>
<td><p>Device.Input.PointDraw</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Precision Touchpad</p></td>
<td><p>Device.Input.Digitizer.PrecisionTouchpad</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Presence Sensor</p></td>
<td><p>Device.Input.Sensor.Base</p>
<p>Device.Input.Sensor.Presence</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Printer</p></td>
<td><p>Device.Imaging.Printer.Base</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Projector</p></td>
<td><p>Device.Display.Monitor</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Removable Storage</p></td>
<td><p>Device.Storage.Hd.RemovableMedia</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Router</p></td>
<td><p>Device.Connectivity.Network.VerticalPairing</p>
<p>Device.Network.Router</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Scanner</p></td>
<td><p>Device.Imaging.Scanner.Base</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>SDIO Controller</p></td>
<td><p>Device.BusController.SdioController</p></td>
</tr>
<tr class="odd">
<td><p>System</p></td>
<td><p>Active</p></td>
<td><p>Server</p></td>
<td><p>System.Client.PCContainer</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Security</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p>
<p>System.Server.Base</p>
<p>System.Server.SMBIOS</p>
<p>System.Server.SystemStress</p>
<p>System.Server.Virtualization</p></td>
</tr>
<tr class="even">
<td><p>System</p></td>
<td><p>Active</p></td>
<td><p>Server Virtualization Validation Program</p></td>
<td><p>System.Client.PCContainer</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Security</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p>
<p>System.Server.Base</p>
<p>System.Server.SMBIOS</p>
<p>System.Server.SystemStress</p>
<p>System.Server.Virtualization</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Signature Tablet</p></td>
<td><p>Device.Input.PointDraw</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Smart Cards</p></td>
<td><p>Device.Input.SmartCardMiniDriver</p>
<p>Device.Input.SmartCardReader</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Smartcard Reader</p></td>
<td><p>Device.Input.SmartCardReader</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Specialized PC</p></td>
<td><p>System.Client.SpecializedPC</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Storage Array</p></td>
<td><p>Device.Storage.Hd</p>
<p>Device.Storage.Hd.RaidArray</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Storage Controller</p></td>
<td><p>Device.Storage.Controller</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Storage Spaces Adapter</p></td>
<td><p>Device.Storage.Controller</p>
<p>Device.Storage.Controller.Flush</p>
<p>Device.Storage.Controller.PassThroughSupport</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Storage Spaces Drive</p></td>
<td><p>Device.Storage.Hd</p>
<p>Device.Storage.Hd.DataVerification</p>
<p>Device.Storage.Hd.Flush</p>
<p>Device.Storage.Hd.MultipleAccess</p>
<p>Device.Storage.Hd.MultipleAccess.PersistentReservation</p>
<p>Device.Storage.Hd.PortAssociation</p>
<p>Device.Storage.Hd.Scsi.ReliabilityCounters</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Storage Spaces Enclosure</p></td>
<td><p>Device.Storage.Enclosure</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>Switch</p></td>
<td><p>Device.Network.Switch.DAL-TOR</p></td>
</tr>
<tr class="odd">
<td><p>System</p></td>
<td><p>Active</p></td>
<td><p>Tablet</p></td>
<td><p>System.Client.Digitizer.Touch</p>
<p>System.Client.Graphics</p>
<p>System.Client.PCContainer</p>
<p>System.Client.SystemPartition</p>
<p>System.Client.Tablet.Graphics</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Firmware</p>
<p>System.Fundamentals.Graphics</p>
<p>System.Fundamentals.Graphics.DisplayRender</p>
<p>System.Fundamentals.Graphics.InternalDisplay</p>
<p>System.Fundamentals.Input</p>
<p>System.Fundamentals.Reliability</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Touch</p></td>
<td><p>Device.Input.Digitizer.Touch</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Touch Monitor</p></td>
<td><p>Device.Input.Digitizer.Touch</p>
<p>Device.Display.Monitor</p></td>
</tr>
<tr class="even">
<td><p>System</p></td>
<td><p>Deprecated</p></td>
<td><p>Ultra-Mobile PC</p></td>
<td><p>System.Client.Firewall</p>
<p>System.Client.Graphics</p>
<p>System.Client.PCContainer</p>
<p>System.Client.SystemConfiguration</p>
<p>System.Client.SystemPartition</p>
<p>System.Client.UMPC.Graphics</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Graphics</p>
<p>System.Fundamentals.Graphics.Display</p>
<p>System.Fundamentals.Graphics.DisplayRender</p>
<p>System.Fundamentals.Graphics.InternalDisplay</p>
<p>System.Fundamentals.HAL</p>
<p>System.Fundamentals.MarkerFile</p>
<p>System.Fundamentals.PowerManagement</p>
<p>System.Fundamentals.PXE</p>
<p>System.Fundamentals.Reliability</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p></td>
</tr>
<tr class="odd">
<td><p>System</p></td>
<td><p>Deprecated</p></td>
<td><p>Ultra-Mobile PC with Touch</p></td>
<td><p>System.Client.Digitizer.Base</p>
<p>System.Client.Digitizer.Touch</p>
<p>System.Client.Firewall</p>
<p>System.Client.Graphics</p>
<p>System.Client.PCContainer</p>
<p>System.Client.SystemConfiguration</p>
<p>System.Client.SystemPartition</p>
<p>System.Client.UMPC.Graphics</p>
<p>System.Fundamentals.DebugPort</p>
<p>System.Fundamentals.Graphics</p>
<p>System.Fundamentals.Graphics.Display</p>
<p>System.Fundamentals.Graphics.DisplayRender</p>
<p>System.Fundamentals.Graphics.InternalDisplay</p>
<p>System.Fundamentals.HAL</p>
<p>System.Fundamentals.MarkerFile</p>
<p>System.Fundamentals.PowerManagement</p>
<p>System.Fundamentals.PXE</p>
<p>System.Fundamentals.Reliability</p>
<p>System.Fundamentals.SignedDrivers</p>
<p>System.Fundamentals.SMBIOS</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>USB Controller</p></td>
<td><p>Device.BusController.UsbController</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>USB Hub</p></td>
<td><p>Device.Connectivity.UsbHub</p></td>
</tr>
<tr class="even">
<td><p>Filter</p></td>
<td><p>Active</p></td>
<td><p>vSwitch Extension</p></td>
<td><p>Filter.Driver.vSwitchExtension</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>WebCam</p></td>
<td><p>Device.Streaming.Webcam.Base</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Windows Filtering Platform</p></td>
<td><p>Filter.Driver.WindowsFilteringPlatform</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>WLAN</p></td>
<td><p>Device.Network.DevFund</p>
<p>Device.Network.WLAN.SupportConnectionToAP</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Deprecated</p></td>
<td><p>WLAN CSB</p></td>
<td><p>Device.Network.DevFund</p>
<p>Device.Network.WLAN.CSBBase</p>
<p>Device.Network.WLAN.CSBNLO</p>
<p>Device.Network.WLAN.CSBSoftAP</p>
<p>Device.Network.WLAN.CSBWiFiDirect</p>
<p>Device.Network.WLAN.CSBWoWLAN</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>WSD Multi-Function Printer</p></td>
<td><p>Device.Imaging.Printer.Base</p>
<p>Device.Imaging.Printer.WSD</p>
<p>Device.Imaging.Scanner.Base</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>WSD Printer</p></td>
<td><p>Device.Imaging.Printer.Base</p>
<p>Device.Imaging.Printer.WSD</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>WSD Scanner</p></td>
<td><p>Device.Imaging.Scanner.Base</p>
<p>Device.Imaging.Scanner.WSD</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Graphics Adapter WDDM2.0</p></td>
<td><p>Device.Graphics.AdapterBase</p>
<p>Device.Graphics.AdapterRender</p>
<p>Device.Graphics.WDDM</p>
<p>Device.Graphics.WDDM.Display</p>
<p>Device.Graphics.WDDM.DisplayRender</p>
<p>Device.Graphics.WDDM.Render</p>
<p>Device.Graphics.WDDM11</p>
<p>Device.Graphics.WDDM11.Display</p>
<p>Device.Graphics.WDDM11.DisplayRender</p>
<p>Device.Graphics.WDDM11.Render</p>
<p>Device.Graphics.WDDM12</p>
<p>Device.Graphics.WDDM12.Display</p>
<p>Device.Graphics.WDDM12.DisplayRender</p>
<p>Device.Graphics.WDDM12.Render</p>
<p>Device.Graphics.WDDM13</p>
<p>Device.Graphics.WDDM13.DisplayRender</p>
<p>Device.Graphics.WDDM13.Render</p>
<p>Device.Graphics.WDDM20</p>
<p>Device.Graphics.WDDM20.DisplayRender</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Mobile Printer</p></td>
<td><p>Device.Imaging.Printer.Mobile</p>
<p>Device.Imaging.Printer.Mobile.WSD20</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Net Switch</p></td>
<td><p>Device.Network.Switch.Manageability</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>BMC</p></td>
<td><p>Device.Connectivity.Server</p></td>
</tr>
<tr class="even">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Cluster</p></td>
<td><p>Device.Cluster</p></td>
</tr>
<tr class="odd">
<td><p>Device</p></td>
<td><p>Active</p></td>
<td><p>Camera</p></td>
<td><p>Device.Streaming.Camera.Base</p></td>
</tr>
</tbody>
</table>

 

 

 






