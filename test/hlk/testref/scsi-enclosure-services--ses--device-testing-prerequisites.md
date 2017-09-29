---
title: SCSI Enclosure Services (SES) Device Testing Prerequisites
description: SCSI Enclosure Services (SES) Device Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f810c7d7-842d-4be8-85d4-faafbe4b58fc
---

# SCSI Enclosure Services (SES) Device Testing Prerequisites


This topic describes the tasks that you must complete before you test a SES device by using the Windows Hardware Lab Kit (Windows HLK):

-   [Hardware Requirements](#bkmk-hardwarerequirements)

-   [Software Requirements](#bkmk-softwarerequirements)

-   [Configuring the Test Computer](#bkmk-configure)

## <span id="BKMK_HardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware Requirements


To test a SES device, you need following hardware:

-   SES device with at least two ports that can be used to connected to servers

-   Two identical Host Bus Adapters (HBAs), each with at least one port

-   Two cables, each connected to one HBA port and to the SCSI Enclosure Storage target device

-   Must be fully loaded with hard disk drives in the SES device that can be accessed via the SES device

-   The CiB (Cluster in a Box) Continuously Available test requires a cluster configuration

## <span id="BKMK_SoftwareRequirements"></span><span id="bkmk-softwarerequirements"></span><span id="BKMK_SOFTWAREREQUIREMENTS"></span>Software Requirements


To test a SES device, you need the following software:

-   Drivers for hardware devices, if required

-   The latest Windows HLK filters or updates

## <span id="BKMK_Configure"></span><span id="bkmk-configure"></span><span id="BKMK_CONFIGURE"></span>Configuring the Test Computer


To configure the test computer for your test device, follow these steps:

1.  Use an appropriate OS installation.

2.  Install HLK Controller and HLK Studio on the Test Server.

3.  Install HLK Client on computers where you intend to run the test.

4.  Select the SES device that you want to test.

5.  Select a disk device contained in the SES device.

6.  On the Test Computer, go to **Disk Management** to ensure that the disk you have selected in the HLK is online. You need a formatted volume on the disk you have selected to successfully pass all tests.

7.  Ensure that the test computer is in **Ready** state before you begin testing. If you do not change the machine status to **Ready**, the tests will not run. You cannot change the machine status to **Ready** while it is in the Default Pool. You need to move the machine to the new pool that you have created before you can do this.

 

 






