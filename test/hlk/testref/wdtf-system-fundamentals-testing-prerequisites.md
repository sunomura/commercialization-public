---
title: WDTF System Fundamentals Testing Prerequisites
description: WDTF System Fundamentals Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 083e5516-cebc-45d5-b8b5-07f37aa446bc
---

# WDTF System Fundamentals Testing Prerequisites


This section describes the tasks that you must complete before you test a client or server system using the Windows Hardware Lab Kit (Windows HLK). System Fundamentals is a collection of tests that apply to both client and server systems and must be run in addition to the system type you want to certify. Review the respective prerequisite topic for the system you are building.

-   For client systems, see [System Client Testing Prerequisites](system-client-testing-prerequisites.md)

-   For server systems, see [System Server Testing Prerequisites](system-server-testing-prerequisites.md)

## <span id="BKMK_HCK_Devfund_gR"></span><span id="bkmk-hck-devfund-gr"></span><span id="BKMK_HCK_DEVFUND_GR"></span>General Requirements


**Audio**

-   Device has at least one render type endpoint connected (speakers, headphones, etc.)

**BitLocker Drive Encryption**

-   Disable fast boot in BIOS prior to running any BitLocker test.

**CD ROM**

-   Drive letter is assigned

-   Media is present in the device

-   Files are present on the media inserted

**Disk**

-   Disk has at least one associated volume

-   Drive letter is assigned

**GPS devices**

-   The device must be tested in a location where a GPS signal is available

**LAN**

-   Device has an IPv6 address

-   Device has an IPv6 default gateway address.

    >[!NOTE]
    >  
    If the network adapters do not have an IPv6 address, you should use the WDTFREMOTESYSTEM parameter to pass an IPv6 address that is valid on your network, such as the IPv6 address of the HLK controller.

     

-   Device’s network operation status is IfOperStatusUp

**WLAN/WiFi devices**

-   The device must be tested in a location where a wireless access point is available

**Smartcard readers**

-   Device has Athena T0 test card inserted

**Volume**

-   Drive letter is assigned

-   Media is present in the device

**USB Host Controller**

-   A SuperSpeed HUB should be connected downstream of each exposed port, and at least one SuperMUTT must be connected to one of these hubs.

## <span id="related_topics"></span>Related topics


[System.Fundamentals Tests](system-fundamentals-tests.md)

 

 







