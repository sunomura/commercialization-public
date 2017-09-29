---
title: System Server Testing Prerequisites
description: System Server Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8ef5cdc1-5802-48a5-b3f4-7e511840bc9b
---

# System Server Testing Prerequisites


This section describes the tasks that you must complete before you test a device by using the Windows Hardware Lab Kit (Windows HLK):

## <span id="BKMK_HCK_Server_hR"></span><span id="bkmk-hck-server-hr"></span><span id="BKMK_HCK_SERVER_HR"></span>Hardware requirements


The following hardware is required for Windows Server System testing. Additional hardware may be required if the test device provides bus-specific support. See the test description for each bus-specific test to determine if there are additional hardware requirements.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Component</th>
<th>Requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Processor</p></td>
<td><p>Server System Certification testing requires that the Server Under Test be populated w/ the maximum number of processors the system supports.</p></td>
</tr>
<tr class="even">
<td><p>Memory</p></td>
<td><p>Server System Certification testing requires that the Server Under Test be populated w/ the maximum amount of memory the system supports for the fastest clock speed supported by the system.</p></td>
</tr>
<tr class="odd">
<td><p>Disk space</p></td>
<td><p>Minimum: 10 GB</p>
<p>Recommended: 40 GB or greater</p>
<div class="alert">
<strong>Note</strong>  
<p>Computers with more than 16 GB of RAM will require more disk space for paging, hibernation, and dump files</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>Drive</p></td>
<td><p>DVD-ROM drive</p></td>
</tr>
</tbody>
</table>

 

### <span id="Infrastructure_Requirement_and_Setup_for_the_Server_Stress_Test"></span><span id="infrastructure_requirement_and_setup_for_the_server_stress_test"></span><span id="INFRASTRUCTURE_REQUIREMENT_AND_SETUP_FOR_THE_SERVER_STRESS_TEST"></span>Infrastructure Requirement and Setup for the Server Stress Test

The Server Stress test requires all test machines to be in a network with a domain controller. The machines themselves must be joined to that domain and have a domain user account created. The reliability of the network is critical to the stress test, if your network is not reliable or setup improperly, the test will either fail or won't start. Make sure the test environment is on a stable and reliable network. Use dynamic IP addressing for all machines. All systems used in testing, such as DHCP, DNS, or Active Directory Domain Controller, must be the latest version and service pack of the operating system.

### <span id="Server_System_under_Test__SUT__Requirements"></span><span id="server_system_under_test__sut__requirements"></span><span id="SERVER_SYSTEM_UNDER_TEST__SUT__REQUIREMENTS"></span>Server System under Test (SUT) Requirements

-   Physical machine (see previous table)

-   Maximum number of processors that the SUT supports.

-   The maximum memory capacity that the SUT supports.

-   At least one Gigabit network adapter, or additional network adapters, being used for testing.

-   One hard disk drive to be used for installing the operating system. This hard disk drive should have two partitions. Partition 1 should have at least 1.5 GB, and less than 5 GB, of space that is configured as Active, System. Partition 2 should have at least 40 GB of space (or the Windows Server minimum requirement) that is configured as Boot, Page File, Crash Dump.

-   One Gigabit Ethernet network hub.

-   SUT computer name must be 154 characters or less.

### <span id="Client_System_Requirements"></span><span id="client_system_requirements"></span><span id="CLIENT_SYSTEM_REQUIREMENTS"></span>Client System Requirements

The system failure of even a single client will cause the entire test to fail. To minimize the likelihood of client system failures, use the following criteria to help you choose computers and other hardware for this test:

-   Make sure that your computers have resources that exceed the minimum CPU and RAM requirements for the version of Windows Server that is being tested on the SUT and installed on the stress client systems.

-   Make sure that all NICs and device drivers have already been Certified for the Windows Server that is being tested. The bandwidth of the NICs in the client computers must be equal to the bandwidth of the NIC in the SUT.

-   Plug all client computers into UPS power protection units.

-   Connect all client computers with high quality cabling, routers, and switches.

-   Use highly redundant storage and memory components: For example, ECC or better memory protection, MPIO Duplexing for storage, RAID hard disks, Teaming for NICs etc.

## <span id="BKMK_HCK_Server_sR"></span><span id="bkmk-hck-server-sr"></span><span id="BKMK_HCK_SERVER_SR"></span>Software requirements


The following software is required to run the Windows Server System tests:

-   Use Windows Server Datacenter to enable all the processors and exercise all possible features in the system being tested (SUT). This applies for Certification testing or for any possible additional feature tests such as those for Fault Tolerance or Enhanced Power Management.

-   Use the Windows Server that is being tested for the master client and the stress client systems

-   Any drivers that are not shipped with Windows Server.

-   The optional Windows Server BitLocker Drive Encryption component must be installed on the server if it is supported by the vendor pre-installed.

>[!WARNING]
>  
The System Tests topic provides more information about the system requirements for the BitLocker Drive Encryption tests.

 

## <span id="Tester_knowledge_requirements"></span><span id="tester_knowledge_requirements"></span><span id="TESTER_KNOWLEDGE_REQUIREMENTS"></span>Tester knowledge requirements


To run the Windows Server System tests, you must know how to perform the following tasks:

-   Create, format, and remove partitions on a hard disk drive.

-   Set power management options.

-   Install and configure a network.

-   Install the operating system from the product DVD.

-   Download a service pack for an operating system.

-   Install the Active Directory Domain Services Role.

-   Create a domain.

-   Set up the systems to be used in testing at the BIOS/FW/UEFI level.

## <span id="Test_server_configuration"></span><span id="test_server_configuration"></span><span id="TEST_SERVER_CONFIGURATION"></span>Test server configuration


To certify your product for use on servers, the test computer must support four processors and a minimum of 1 GB of RAM. These system capabilities are required to test the Rebalance, D3 State, and Multiple Processor Group functionality of the device and driver. You do not need a computer that actually has more than 64 processors to test your device. Additionally, the server system(s) being used for device or driver testing must have Server Core installed prior to testing. For more information see [Windows Server Installation Options](http://go.microsoft.com/fwlink/p/?LinkID=251454).

If you use a pool of test computers to test devices, at least one computer in the pool must contain four processors and a minimum of 1 GB of RAM. Additionally, that computer must contain the device and the driver that you want to test. As long as the driver is the same on all the computers in the pool, the system creates a schedule to run against all test computers.

For tests that do not include a driver to test, such as hard disk drive tests, the Windows HLK scheduler constrains the tests that validate the device’s and driver’s Rebalance, D3 State and Multiple Processor Groups functionality to run on the default test computer. You must manually configure this computer to have multiple processor groups. The default computer is the first test computer in the list. Test personnel must make sure that the first test computer in the list meets the minimum hardware requirements.

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

 

 

 






