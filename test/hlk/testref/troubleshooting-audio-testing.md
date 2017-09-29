---
title: Troubleshooting Audio Testing
description: Troubleshooting Audio Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1a97fce7-dd6e-483b-a890-1c318d1573cd
---

# Troubleshooting Audio Testing


This article describes how to troubleshoot problems that can occur during Windows Hardware Lab Kit (Windows HLK) Device.Audio and System.Fundamentals audio tests.

**In this article:**

-   [General audio test issues](#gen)

-   [Jack detection issues](#jack)

-   [Wireless display issues](#wireless)

## <span id="gen"></span><span id="GEN"></span>General audio test issues


To troubleshoot general audio test issues, start with the following steps:

1.  Make sure that all audio endpoints are connected and capable of streaming. This includes but is not limited to headphones, high definition multimedia interface (HDMI), DisplayPort, Sony/Philips digital interface (S/PDIF), and other endpoints.

    1.  To verify that all devices are connected, open the sound control panel by typing **mmsys.cpl** from a command prompt window. All devices on both the playback and recording tabs should show as being connected.

    2.  Sometimes devices do not display if they were disconnected or disabled. To make sure that all devices are visible, right-click the background of the control panel and verify that both **Show Disabled Devices** and **Show Disconnected Devices** are checked.

    3.  To check endpoints on the playback tab for streaming capability, right-click the endpoint and select **Test**. You should hear audio from the endpoint and see the corresponding meter move.

    4.  To check endpoints in the recording tab for streaming capability, speak into the microphone and confirm that the meter moves.

2.  The fidelity test has a complex setup. Confirm that the test environment is set up correctly. Make sure that you have the cables connected properly. Improperly connected or missing cables result in failures, such as very low THD+N.

3.  The audio logo tests include several test cases that validate the zero glitch requirement. If a test fails on a glitch test case, we recommend that you review the hardware and driver for issues that can cause glitches. In particular, look for the following causes:

    -   Improper thread priority in drivers together with long DPC / ISRs.

    -   Improper hardware power management.

4.  If a test fails, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

5.  Verify that you have installed the latest Windows HLK filters and kit updates. For more information, see [Windows Hardware Lab Kit Filters](..\user\windows-hardware-lab-kit-filters.md).

6.  Review the following Windows HLK topics:

    -   [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md)

    -   [Audio Device Testing Prerequisites](audio-device-testing-prerequisites.md)

## <span id="jack"></span><span id="JACK"></span>Jack detection issues


Some audio-device vendors use a four-ring combo jack, which uses headsets that similar to the headsets that are used for the iPhone. Normal microphone or head phone plugs have the following three contacts (TRS): tip: left, ring: right, and sleeve: ground. The combo headset has the following four contacts (TRRS): tip: left, ring1: right, ring2: ground, and sleeve: microphone. These combo jacks are connected to two ports on the Codec simultaneously. Therefore, they must trigger two jack-detection signals simultaneously.

There is a known issue with the HDAudio.sys driver on Windows 7 and Windows Vista. It does not correctly handle simultaneous, or nearly simultaneous, jack-detection signals. You can work around this issue by plugging the device into the jack more slowly.

## <span id="wireless"></span><span id="WIRELESS"></span>Wireless display issues


The audio tests listed below are not suitable for testing devices supporting Wireless Display functionality. It is possible for the tests to fail the devices due to unreachable audio endpoints while a wireless endpoint is connected.

**Affected Audio Tests**

-   Audio Logo Test
-   Class Driver Audio Logo Test
-   Class Driver KS Topology
-   Class Driver Round Trip Test
-   Round Trip Test

The error message is **FAIL: Endpoint (XXXXXX) is unplugged**, where **XXXXXX** is the name of Wireless Audio Endpoint.

**Workaround**

Prior to running the affected audio tests, disconnect wirelessly-connected endpoints, such as wireless monitors, from the test device. You can reconnect the wireless endpoints after testing.

## <span id="related_topics"></span>Related topics


[Device.Audio Tests](device-audio-tests.md)

[System.Fundamentals Tests](system-fundamentals-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







