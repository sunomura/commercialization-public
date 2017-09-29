---
title: Troubleshooting LAN Testing
description: Troubleshooting LAN Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b8392b64-b746-4bed-bb44-279826b57f40
---

# Troubleshooting LAN Testing


To troubleshoot issues that occur with Device.Network tests, follow these steps:

1.  Review [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

2.  Review the [Windows HLK release notes](http://go.microsoft.com/fwlink/?LinkID=236110) for current test issues.

3.  For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

If the two machines LAN test jobs fail it is probable that the tests are not able to detect the message and/or support devices on either of the two machines.

To quickly diagnose this type of problem, run the “NDISTest 6.5 – \[2 Machine\] – CheckConnectivity” job. This job only takes a couple minutes to run but will tell you if the machines can communicate and are ready to run the rest of the two machine jobs.

If there is a connectivity issue, the job will fail in the “Run NDISTest Client” task. The job’s log files will list failures when the test and support NICs cannot communicate bidirectionally. Review the results in the job’s log files, check the machines’ connections, and try running the job again.

You should also check that you are selecting the correct machine as the support machine. With multiport NICs and multiple machine setups, it is very easy to select the wrong NIC or wrong machine. We suggest keeping the two machines running LAN tests in their own machine pool to avoid accidentally selecting the wrong machine.

## <span id="the_ndistest_6.5____2_machine____checkconnectivity_job"></span><span id="THE_NDISTEST_6.5____2_MACHINE____CHECKCONNECTIVITY_JOB"></span>The NDISTest 6.5 – \[2 Machine\] – CheckConnectivity job


The NDISTest 6.5 – \[2 Machine\] – CheckConnectivity job ensures that the test and support devices can communicate correctly by doing a basic send and receive.

If the “Run script to detect devices and populate parameters” task is marked as failed, the device autodetection failed. Double click detect.wtl to open the autodetection log to determine which device was not detected.

Autodetection of the devices will only work if machines are set up in the recommended topology. The test machine needs to contain the target NIC and the message NIC. The support machine needs to contain a support NIC and a message NIC. Any additional connected Ethernet devices will make autodetection impossible and will require the devices to be renamed to denote their roles.

The support NIC needs to be connected to the test NIC using a direct connection (no switch or hub) in order to avoid interference. The message NICs are the same NIC used for connectivity to the controller machine and the rest of the lab or corporate network.

### <span id="The_CheckConnectivity_script_logic"></span><span id="the_checkconnectivity_script_logic"></span><span id="THE_CHECKCONNECTIVITY_SCRIPT_LOGIC"></span>The CheckConnectivity script logic

The autodetection script logic is as follows:

1.  Find the message NIC.

    1.  Search for devices named “MessageDevice”.

    2.  If not found, search for the Ethernet NIC with a DHCP assigned IP address.

    3.  If still not found, search for the Ethernet NIC with a statically assigned IP address.

    4.  If nothing is found, fail and exit.

2.  If running on the support machine, find the support NIC.

    1.  Search for devices named “SupportDevice0”.

    2.  If not found, search for a physical, enabled Ethernet NIC that is not the message NIC.

    3.  If nothing is found, fail and exit.

Full details of the autodetection script logic can be found by examining the script which is located at: \\\\\[CONTROLLER\]\\Tests\\\[ARCH\]\\NDIS\\Scripts\\detect.wsf

Where:

*\[CONTROLLER\].* The name of the controller computer.

*\[ARCH\].* Either x86 (for x86-based processors) or amd64 (for x64-based processors).

### <span id="Reading_the_NDISTest_Logs"></span><span id="reading_the_ndistest_logs"></span><span id="READING_THE_NDISTEST_LOGS"></span>Reading the NDISTest Logs

One way to read NDISTest logs is to double click “ndistest.wtl” or right click the task result and go to “Additional files” for the job result you want to view. This will open the DTM Manager log viewer.

NDISTest also produces HTML logs which are often much more readable. To view the HTML log for a result, right click the task result and go to “Additional files”. There will be several files listed; open the checkconnectivity.htm file under the “Client” folder.

Additionally open “ndistest.htm” from the “Client” folder to view failures from the preconfig and postconfig tasks that run before and after each NDISTest 6.5 test.

## <span id="related_topics"></span>Related topics


[Device.Network Testing](device-network-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







