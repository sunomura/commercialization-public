---
title: Server Testing Overview
description: Server Testing Overview
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 83f84931-6bdd-42cc-96b6-4ac4b08d7368
---

# Server Testing Overview


Windows Server testing is primarily stress-oriented testing that include client/server I/O, network stress, CPU consumption, and memory consumption. The specific tests you must run depends on the features that you implement on the server.

This section only describes System.Server tests. A complete Windows Server Certification requires several tests that are comprised of System.Client, System.Fundamentals and System.Server tests. Windows Hardware Lab Kit (Windows HLK) Studio detects all features on a server.

## <span id="General_server_stress_testing"></span><span id="general_server_stress_testing"></span><span id="GENERAL_SERVER_STRESS_TESTING"></span>General server stress testing


Several kinds of stress tests get run against a server, including basic system functionality, system stress and shutdown/restart tests. *LoadGen* is a test tool that generates load on a system under test (SUT). LoadGen is started on the master client and can use multiple stress client computers to generate network load on the SUT.

### <span id="System_functionality_tests"></span><span id="system_functionality_tests"></span><span id="SYSTEM_FUNCTIONALITY_TESTS"></span>System functionality tests

The system functionality tests are individual tests of the capabilities of the system. Some tests are run for every system, and some tests only run if the capability exists in the system.

### <span id="System_stress_test"></span><span id="system_stress_test"></span><span id="SYSTEM_STRESS_TEST"></span>System stress test

The System Stress Test consists of several server scenario workloads that operate from the user level address space that is applied to the system to exercise the system hardware, system-specific devices and drivers, network and storage adapters and drivers, and any filter drivers that might be part of the system configuration, such as multipath storage drivers, storage or file system filter drivers, or intermediate layer network drivers.

The workloads applied are

-   SQL I/O Simulation

-   Local Storage I/O

-   Disk Stress with Verification

-   Client-Server Storage I/O

-   Winsock Network Traffic

These workloads automatically scale to the number of network and storage adapters in the system that have connected clients or storage devices, respectively. For example, if the test discovers one network adapter and one storage adapter (together with the necessary connected clients or storage devices, respectively), the test creates workload processes for that number of adapters to provide the stress workload. If the system has multiple network and storage adapters, test processes are created for each of those adapters, drivers, and connected resources (clients or storage devices) to provide the same relative stress workload. Additionally, the network and storage adapters and their respective resources do not need to be the same type. For example, Gigabit Ethernet and 10 Gigabit Ethernet adapters can be tested at the same time, as long as network clients are connected to both devices. Similarly, Fibre Channel and iSCSI storage adapters can be tested at the same time, as long as the appropriate storage media is attached. Any HBA units that are attached to the SUT must be connected to the appropriate type of storage media.

The system test achieves the same relative amount of stress on the system, regardless of the number or type of processors, amount of memory, or the number of network and storage adapters in the system. The test detects the number of processors/cores in the system, as well as the amount of memory in the system. The test then creates as many processor-specific and memory-specific stress processes as are needed to achieve a predetermined level of processor and memory utilization and will terminate those processes if the utilization level exceeds the predetermined level of stress. Therefore, the level of utilization for those resources is always commensurate with the capabilities of the system. A system that supports only a few processors/cores and an appropriate amount of memory for the system has the same relative levels of stress as a larger system with more processors/cores and a greater amount of memory.

### <span id="Shutdown_Restart_Test"></span><span id="shutdown_restart_test"></span><span id="SHUTDOWN_RESTART_TEST"></span>Shutdown/Restart Test

The server test also includes a shutdown and restart test. This test signals the system to shut down and restart. The test records the event log information related to shutting down and restarting the system, such as vetoes that prevent shutdown, the startup event, and any driver errors that are received after restarting the system. This test makes sure that all device drivers in the system comply with system shutdown, do not veto, and cleanly restart in the system without conflicting with other drivers. For more information, see [I/O Completion Cancellation Guidelines](http://go.microsoft.com/fwlink/?linkid=51436).

There are 3 specific tests:

-   LoadGen Server Stress - Run First - Set Machine Policies (run time &lt; 30 minutes)

-   LoadGen Server Stress - Run First - Start Test for Server (run time = 24 hours)

-   LoadGen Server Stress - Run Last - Reset Machine Policies (run time &lt; 30 minutes)

You must schedule the [LoadGen Server Stress - Run First - Set Machine Policies](318d804e-aa8f-4ffb-8ce2-963cea2f1a40.md)" job before you run the "[LoadGen Server Stress - Start Test for Server](6e9adb95-fca5-4e15-a255-bc96c0d12aa9.md)" job. You must schedule the "[LoadGen Server Stress - Run Last - Reset Machine Policies](8cb4f87c-d2a4-4d90-92a7-edd016ccdeac.md)" job after the **Start Test for Server** job has finished.You must schedule the **Run First** and **Run Last** jobs only one time for each submission, but you must schedule and run the **Start Test** job multiple times until it passes. You must also schedule the **Run Last - Reset Machine Policies** job if you are going to schedule other different jobs in the same machine pool.

## <span id="Server_virtualization_validation_program__SVVP__testing"></span><span id="server_virtualization_validation_program__svvp__testing"></span><span id="SERVER_VIRTUALIZATION_VALIDATION_PROGRAM__SVVP__TESTING"></span>Server virtualization validation program (SVVP) testing


Two kinds of virtualization tests are run against a server, including virtual machine functionality tests and SVVP System functionality tests. The system can be a standalone server or a virtual machine. LoadGen is started on the master client and can use multiple stress client computers to generate network load on the system under test.

### <span id="Virtual_machine_functionality_tests"></span><span id="virtual_machine_functionality_tests"></span><span id="VIRTUAL_MACHINE_FUNCTIONALITY_TESTS"></span>Virtual machine functionality tests

The functionality tests are individual tests of the capabilities of the product's virtual machine implementation.

### <span id="SVVP_System_functionality_tests"></span><span id="svvp_system_functionality_tests"></span><span id="SVVP_SYSTEM_FUNCTIONALITY_TESTS"></span>SVVP System functionality tests

The SVVP System functionality tests validate the functionality of the following aspects and components of the virtual machine:

-   Virtual PCI I/O

-   Virtual SMBIOS

-   Virtual Timers

-   Virtual ACPI and PNP functions

-   The correct operation of the storage capabilities of the virtual machine

-   The appropriate signing by Microsoft of all the drivers included

-   Virtualization products correctly expose to the instance of the running operating system, the fact that the operating system is running in a virtual environment.

## <span id="Additional_features_testing"></span><span id="additional_features_testing"></span><span id="ADDITIONAL_FEATURES_TESTING"></span>Additional features testing


Server systems might have additional functionality beyond that which is required for Windows Server Certification. The additional features for which a system can test and qualify are as follows:

These additional feature tests are in the Windows HLK test harness together with the tests that are listed for systems. Vendors whose systems can meet the requirements for these additional features must select and run the required tests. The Fault Tolerant tests exercise and confirm the ability of a fault-tolerant system hardware, devices, and drivers to have a hardware failure and continue to operate without impacting clients that are connected to the server over on the network. The Enhanced Power Management tests validate that the systems supports the CPUID feature flag, processor p-states, and other functionality needed for Windows Serverto manage the power of the system.

For more information, see the "Power Supply, Metering, and Budgeting Interface" section in the [ACPI 4.0 or later specification](http://www.acpi.info/spec.md) and “[Processor Power Management in Windows Vista and Windows Server](http://go.microsoft.com/fwlink/?LinkID=296636).

Note that a system can support none, some or all of the above features, such as both enhanced power management. For a vendor to validate that the system meets the requirements for one or more additional features, one or more of the additional feature tests must be selected and run. Those results are then submitted together with the results of the Server Certification tests. The additional feature test results cannot be submitted separately from Server Certification test results.

Run time for these additional feature tests varies, depending on the selected tests. If the Server Certification test is selected only, testing takes approximately two days, with the Loadgen test taking one day to run and the remaining tests using the remaining time.Additionally, if the system being tested includes audio, video or other devices and drivers, those will be exercised and increase test time.

## <span id="Minimum_required_server_test"></span><span id="minimum_required_server_test"></span><span id="MINIMUM_REQUIRED_SERVER_TEST"></span>Minimum required server test


The following is a minimum list of tests that you must run on all servers. For minimum test listed under System.Client or System.Fundamentals, you must review the appropriate prerequisite section for each test.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Required Server Test</th>
<th>Test Category</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ACPI Logo Test</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="even">
<td><p>Boot Test (SYSTEM)</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="odd">
<td><p>Debug Capability Test (Logo)</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="even">
<td><p>Disk Stress (SYSTEM)</p></td>
<td><p>System.Server</p></td>
</tr>
<tr class="odd">
<td><p>Hal timer tests (HCT)</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="even">
<td><p>NX Test</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="odd">
<td><p>PCI Hardware Compliance Test For Systems</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="even">
<td><p>Secure Boot Logo Test</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="odd">
<td><p>Secure Boot Manual Logo Test</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="even">
<td><p>Signed Driver Check (CheckLogo)</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="odd">
<td><p>SMBIOS HCT</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="even">
<td><p>System - PNP (disable and enable) with IO Before and After (Certification)</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="odd">
<td><p>System - Sleep and PNP (disable and enable) with IO Before and After (Certification)</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="even">
<td><p>System - Sleep with IO Before and After (Certification)</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="odd">
<td><p>USB Boot test (SYSTEM)</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="even">
<td><p>USB Exposed Port System Test</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="odd">
<td><p>USB xHCI Register System test</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="even">
<td><p>USB3 Termination</p></td>
<td><p>System.Fundamentals</p></td>
</tr>
<tr class="odd">
<td><p>Verify virtualized environment</p></td>
<td><p>System.Server</p></td>
</tr>
<tr class="even">
<td><p>Verify processor virtualization support</p></td>
<td><p>System.Server</p></td>
</tr>
<tr class="odd">
<td><p>WHEAHCT Logo</p></td>
<td><p>System.Server</p></td>
</tr>
<tr class="even">
<td><p>Win8 LoadGen Server Stress - Run First - Set Machine Policies</p></td>
<td><p>System.Server</p></td>
</tr>
<tr class="odd">
<td><p>Win8 LoadGen Server Stress - Run Last - Reset Machine Policies</p></td>
<td><p>System.Server</p></td>
</tr>
<tr class="even">
<td><p>Win8 LoadGen Server Stress - Start Test for Server</p></td>
<td><p>System.Server</p></td>
</tr>
</tbody>
</table>

 

## <span id="related_topics"></span>Related topics


[System.Server Testing](system-server-tests.md)

 

 







