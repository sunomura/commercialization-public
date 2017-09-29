---
title: Graphic Adapter or Chipset Testing Prerequisites
description: Graphic Adapter or Chipset Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 112cb1c7-cfe7-447d-8285-ff333f5afd83
---

# Graphic Adapter or Chipset Testing Prerequisites


This section describes the tasks that you must complete before you test a graphic adapter or chipset by using the Windows Hardware Lab Kit (Windows HLK).

-   [Hardware requirements](#bkmk-hardwarerequirements).

-   [Software requirements](#bkmk-softwarerequirements).

-   [Test computer configuration](#bkmk-configure).

## <span id="BKMK_HardwareRequirements"></span><span id="bkmk-hardwarerequirements"></span><span id="BKMK_HARDWAREREQUIREMENTS"></span>Hardware requirements


The following hardware is required for testing a graphics adapter or chipset. This specific hardware fulfills the diversity requirements that demonstrate the stability of display drivers and chipsets. You might need additional hardware if the test device offers other features. To determine whether additional hardware requirements apply, see the test description for each test that appears for the device in Windows HLK Studio.

-   At least two test computers for every discrete device family in the INF file that is being certified. These test computers must meet the Windows HLK prerequisites and must be included in the same machine pool. For more information, see [Windows HLK Prerequisites](..\getstarted\windows-hlk-prerequisites.md). These systems must contain the following:

    -   If your device family supports a stand-alone feature, you must include at least one adapter with that capability per device family in the machine pool. For example, if your adapter supports Stereo 3D, you must include at least one of these adapters (per device family) in the machine pool along with a stereo capable monitor as the primary display set to a stereo-capable mode.

    -   If you support LDA configuration, you will need to include relevant display adapters in the machine pool.

-   A minimum of two adapters for every device family that the INF file supports. One of the adapters must support multi-display capabilities and have a monitor attached and enabled.

-   One multi-sync display data channel standard, level 2B (DDC2B)-capable monitor that has extended display identification data (EDID) 1.3 support on the test computer.

Depending on the type of submission, you might need the following features or configurations:

-   TV-out support

-   Multi-monitor support

-   Hot-plug detection support

>[!NOTE]
>  
To certify your product for use on servers, the test computer must support four processors and a minimum of 1 GB of RAM. These system capabilities are required to test the Rebalance, D3 State, and Multiple Processor Group functionality of the device and driver. You do not need a computer that actually has more than 64 processors to test your device. Additionally, the server system(s) being used for device or driver testing must have Server Core installed prior to testing. For more information see [Windows Server Installation Options](http://go.microsoft.com/fwlink/p/?LinkID=251454).

If you use a pool of test computers to test devices, at least one computer in the pool must contain four processors and a minimum of 1 GB of RAM. Additionally, that computer must contain the device and the driver that you want to test. As long as the driver is the same on all the computers in the pool, the system creates a schedule to run against all test computers.

For tests that do not include a driver to test, such as hard disk drive tests, the Windows HLK scheduler constrains the tests that validate the device’s and driver’s Rebalance, D3 State and Multiple Processor Groups functionality to run on the default test computer. You must manually configure this computer to have multiple processor groups. The default computer is the first test computer in the list. Test personnel must make sure that the first test computer in the list meets the minimum hardware requirements.

>[!NOTE]
>  
Except for para-virtualization drivers (as defined by the [WHCP Policies and Processes](http://go.microsoft.com/fwlink/p/?LinkID=615222) document), you may not use any form of virtualization when you test physical devices and their associated drivers for server certification or signature. All virtualization products do not support the underlying functionality that is required to pass the tests that relate to multiple processor groups, device power management, device PCI functionality, and other tests.

>[!NOTE]
>  Multiple Processor Groups Setting
>You must set the value for the processor group size for Hardware Lab Kit testing of Windows Server 2008 R2 and later device drivers for certification. This is done by running bcdedit in an elevated command prompt window, using the /set option.
>
>The commands for adding the group settings and restarting are as follows:
>
``` syntax
bcdedit.exe /set groupsize 2
bcdedit.exe /set groupaware on
shutdown.exe -r -t 0 -f
```
>
>
>The commands for removing the group settings and rebooting are as follows:
>
``` syntax
bcdedit.exe /deletevalue groupsize
bcdedit.exe /deletevalue groupaware
shutdown.exe -r -t 0 -f
```
>

>[!NOTE]
>  
**Code Integrity Setting**

>The Virtualization Based Security feature (VBS) of Windows Server 2016 must be enabled using Server Manager first.
>
>Once that has occurred, the following Registry key must be created and set:
>
``` syntax
HKLM\System\CurrentControlSet\Control\DeviceGuard
HypervisorEnforcedCodeIntegrity:REG_DWORD
0 or 1 (disabled, enabled)
```

 

## <span id="BKMK_SoftwareRequirements"></span><span id="bkmk-softwarerequirements"></span><span id="BKMK_SOFTWAREREQUIREMENTS"></span>Software requirements


The following software is required for testing a graphics adapter or chipset:

-   The drivers for the test device.

    >[!NOTE]
    >  
    OPM/COPP requirements are implemented based on feature detection; Full WDDM drivers must support OPM/COPP if they have a capable connector/monitor.

     

-   **Supplemental Content for Windows HLK Tests for DXVA and HMFT Multimedia Tests** is required to pass the DXVA (DirectX Video Acceleration) tests. Download and install this supplemental test content from the MSDN® website at: <http://msdn.microsoft.com/en-us/windows/hardware/hh852358>.

    >[!IMPORTANT]
    >  
    Before running the DXVA tests on x86 or amd64 systems, you must install the Windows 8 Professional SKU and then install the Windows Anytime Upgrade for Media Center; otherwise, the MPEG2 tests will fail.

    The Media Foundation Feature must be installed on Server 2012 for DXVA testing.

     

-   The latest Windows HLK filters or updates.

-   All operating system updates, service packs and compatibility packs

>[!NOTE]
>  
The Displaygroups.xml (required in previous version of the kit) is not present in the Windows HLK. The declaration of ASIC families has been replaced by device families which must be declared using scripts in the Windows Hardware Lab Kit Object Model. Refer to WHLK OM documentation for more details.

 

Many Windows HLK graphics tests use a **HLKShowClassicDesktop.exe** tool to forcibly switch from the tailored app start menu to the classic desktop. Be aware that **HLKShowClassicDesktop** does not work if User Account Control (UAC) is disabled.

Many people disable UAC so that its prompts do not interfere with test automation. However, **HLKShowClassicDesktop** requires a higher privilege level than most Windows HLK tests. If you disable UAC, all applications run at the same default level.

We recommend you use the **Never Notify** option to silence prompts instead of disabling UAC. To do this, configure the following registry keys settings: .

``` syntax
Set HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\EnableLUA = 1 to turn UAC on
Set HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\ConsentPromptBehaviorAdmin = 0 to turn on Never Notify mode
```

## <span id="BKMK_Configure"></span><span id="bkmk-configure"></span><span id="BKMK_CONFIGURE"></span>Test computer configuration


Display adapter or chipset testing requires at least one test computer for every device family in the INF file that is being certified.

To configure the test computer for the display adapter testing, follow these steps:

1.  Install the appropriate Windows operating system on the test computers and then join the computers to your test network.

    For each graphics device family:

    -   Configure at least one computer with multiple display adapters (two monitors at a minimum)

    -   If supported configure at least one system with:

        1.  Stereo-capable display as the primary display set to a stereo-capable mode

        2.  Composite display or S-Video display

        3.  HDCP capable display

2.  Attach one multi-sync display data channel standard, level 2B (DDC2B)-capable monitor that has EDID 1.3 support to each test computer.

    >[!NOTE]
    >  
    The secondary head of a multiple-headed display adapter and chipset must be connected to a monitor and enabled before you start testing. Not all devices that support multiple heads must be enabled, but at least one device for each device family that is listed in the INF file must be enabled. To test outside of the submission process, make sure that all secondary heads are connected to a monitor and enabled. Otherwise, when a test is selected for the unattached secondary head, the test runs on the primary head.

     

3.  If you have to install the manufacturer-supplied device driver on the test computer or computers, do this now.

4.  Make sure that the display monitor or projector functions correctly on both the test computers.

5.  Disable power management and password protection before you start the testing.

6.  Install the Windows HLK client application on the test computers.

7.  Use Windows HLK Studio to create a machine pool, and then move the test computer to that pool.

8.  (Optional) Define device families to test (requires the Windows HLK object model

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the specific test topic for more information.

Some Windows HLK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

Before you start a display test, close any active applications, including File Explorer and Internet Explorer, on the test computer. Disable any active applications that, by default, are the top window. Examples of such applications are pop-up balloons or on-screen keyboards for Tablet PCs.

To run the Fast User Switching (FUS) tests, make sure that the test system is not part of a domain. To do this, right-click **My Computer**, and then click **Properties**. On the **Computer Name** tab, see if the computer is a part of a domain. If the computer is part of a domain, click **Change**, and then add the computer to a workgroup.

 

 






