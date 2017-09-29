---
title: Use kernel debugging to debug Device Fundamentals Reliability test failures
description: Use kernel debugging to debug Device Fundamentals Reliability test failures
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1bb7ac5e-c492-4d45-8b06-e2f97e578456
---

# Use kernel debugging to debug Device Fundamentals Reliability test failures


This describes how to use common kernel debugging commands to debug Device Fundamentals Reliability test failures.

**In this topic:**

-   [Set symbols](#sym)

-   [!analyze -v](#analyze)

-   [Inspect stack traces of the test process](#stacktrx)

-   [Switch context to threads and frames to view locals](#switch)

-   [!pnptriage](#pnptriage)

-   [Driver debugging extensions](#drvdebugext)

-   [Debugger extensions](#debugext)

## <span id="sym"></span><span id="SYM"></span>Set symbols


You can find Windows Hardware Lab Kit content symbols on the Microsoft Public Symbols Server site. See [Use the Microsoft Symbol Server to obtain debug symbol files](http://go.microsoft.com/fwlink/?LinkID=299516) for more information about the Microsoft Public Symbols Server. You can set symbols in the kernel debugger by running the [.sympath (Set Symbol Path)](http://go.microsoft.com/fwlink/?LinkID=299519) command.

*Example:*

In this example,the .sympath command sets the public symbols server path in the debugger.

``` syntax
.sympath SRV*c:\localsymbols*http://msdl.microsoft.com/download/symbols
```

## <span id="analyze"></span><span id="ANALYZE"></span>!analyze -v


When you investigate test failures that are caused by system bug checks from the kernel debugger, the first command that should you should issue after you set symbols is **!analyze**. This command identifies the bug check code, the reason for the bug check, and the stack trace that shows the faulting component. See [Using the !analyze Extension](http://go.microsoft.com/fwlink/?LinkID=293845) for more information about this command.

## <span id="stacktrx"></span><span id="STACKTRX"></span>Inspect stack traces of the test process


Device Fundamentals Reliability tests often run as **Te.ProcessHost.exe** or **Te.exe** on the test computer. It is useful to review stack traces from these test processes when you investigate system bug checks or test hangs. In the case of bug checks, stack traces can help identify the test case that was being tested at the time of the crash. In the case of test hangs, stack traces identify any test threads that prevent the test from progressing.

You can use the **!process 0 0** extension to list all processes that are running on the test computer, to find the test process EPROCESS block address.

You can then use the **!process /p /r** extension to get full stack traces from the test processes.

For more information about the **!process** extension, see [!process](http://go.microsoft.com/fwlink/?LinkID=299524) and [.process (Set Process Context)](http://go.microsoft.com/fwlink/?LinkID_299529).

Note that **!process** output contains tick counts for each thread that is running in the process. When you investigate test hangs, threads that have a high tick count that contain WDTF components on the stack (that is, module names that start with “WDTF” on the stack) should be reviewed carefully because these threads can cause the tests to permanently hang and eventually fail because of a timeout.

*Example:*

In this example, **!process 0 0**, **!process /p /r**, and **!process** extensions identify a test thread that has a very high tick count, that prevents the test from progressing:

``` syntax
!process 0 0 Te.ProcessHost.exe 
    PROCESS fffffa80093c6340
    SessionId: 1 Cid: 1320 Peb: 7f6595b3000 ParentCid: 12a0
    DirBase: 21eee000 ObjectTable: fffff8a0035b0a00 HandleCount: 327. 
    Image: TE. ProcessHost.exe
.process /p /r fffffa80093c6340
```

``` syntax
!process fffffa80093c6340 


        THREAD fffffa800b2be8c0  Cid 0964.0eac  Teb: 000007f601ba6000 Win32Thread: 0000000000000000 WAIT: (UserRequest) UserMode Non-Alertable
            fffffa800b2a11d0  SynchronizationEvent
            fffffa800b300640  SynchronizationEvent
        Not impersonating
        DeviceMap                 fffff8a0014b9c80
        Owning Process            fffffa800b302940       Image:         TE.exe
        Attached Process          N/A            Image:         N/A
        Wait Start TickCount      210995         Ticks: 405945 (0:01:45:32.782)
        Context Switch Count      51             IdealProcessor: 2             
        UserTime                  00:00:00.015
        KernelTime                00:00:00.015
        Win32 Start Address WDTFInterfaces!TsSingleWorkerThread (0x000007fe3a567f28)
        Stack Init fffff8800eb5edd0 Current fffff8800eb5dee0
        Base fffff8800eb5f000 Limit fffff8800eb59000 Call 0
        Priority 9 BasePriority 8 UnusualBoost 0 ForegroundBoost 0 IoPriority 2 PagePriority 5
        Kernel stack not resident.
        Child-SP          RetAddr           Call Site
        fffff880`0eb5df20 fffff803`78b27f7c nt!KiSwapContext+0x76
        (Inline Function) --------`-------- nt!KiSwapThread+0xf4 (Inline Function @ fffff803`78b27f7c)
        fffff880`0eb5e060 fffff803`78aaf4ab nt!KiCommitThreadWait+0x23c
        fffff880`0eb5e120 fffff803`78b257a0 nt!KiWaitForAllObjects+0x3bb
        fffff880`0eb5e3c0 fffff803`78ecb3dc nt!KeWaitForMultipleObjects+0x4ae
        fffff880`0eb5e470 fffff803`78ecb853 nt!ObWaitForMultipleObjects+0x29c
        fffff880`0eb5e980 fffff803`78aff053 nt!NtWaitForMultipleObjects+0xe3
        fffff880`0eb5ebd0 000007fe`45d2315b nt!KiSystemServiceCopyEnd+0x13 (TrapFrame @ fffff880`0eb5ec40)
        00000083`7cdef148 000007fe`430912c6 ntdll!ZwWaitForMultipleObjects+0xa
        00000083`7cdef150 000007fe`368641b5 KERNELBASE!WaitForMultipleObjectsEx+0xe5
        00000083`7cdef430 000007fe`3a566793 WDTFAudioSimpleIoAction!CAudioImpl::RunIO+0x3d1
        00000083`7cdef520 000007fe`3a566ea0 WDTFInterfaces!CSimpleIOEx::PerformIO+0x10f
        00000083`7cdef5b0 000007fe`3a56706b WDTFInterfaces!CSimpleIOExWrap::PerformIO+0x28
        00000083`7cdef5e0 000007fe`3a553fe5 WDTFInterfaces!CMTest_Receiver::Run+0x77
        00000083`7cdefe20 000007fe`3a5578ac WDTFInterfaces!CSimpleIO_MTestEx::ActionThread+0x105
        00000083`7cdefeb0 000007fe`3a567f3e WDTFInterfaces!CMTEXThread::ThreadWorker+0xc
        00000083`7cdefee0 000007fe`4319167e WDTFInterfaces!TsSingleWorkerThread+0x16
        00000083`7cdeff20 000007fe`45d3c3f1 KERNEL32!BaseThreadInitThunk+0x1a
        00000083`7cdeff50 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

## <span id="switch"></span><span id="SWITCH"></span>Switch context to threads and frames to view locals


To view local variables from a stack frame, you must perform the following actions:

1.  Switch context to the thread by using the [.thread (Set Register Context)](http://go.microsoft.com/fwlink/?LinkID=299551) command.

2.  Dump the stack together with frame numbers by using the **kn** command (see [Stack and Dump Logging](http://go.microsoft.com/fwlink/?LinkID=299552).

3.  Switch to frame context by using the [.frame (Set Local Context)](http://go.microsoft.com/fwlink/?LinkID=299553) command.

4.  View locals by using the [dv (Display Local Variables)](http://go.microsoft.com/fwlink/?LinkID=299554) command.

>[!NOTE]
>  
You must use private symbols to dump local variables.

 

*Example:*

This example uses **.thread**, **kn**, **.frame**, and **dv** commands to dump local variables from a stack frame:

``` syntax
3: kd> .thread fffffa8009da7b00
Implicit thread is now fffffa80`09da7b00

3: kd> kn
  *** Stack trace for last set context - .thread/.cxr resets it
# Child-SP          RetAddr           Call Site
00 fffff880`054a03a0 fffff801`05caaf7c nt!KiSwapContext+0x76
01 fffff880`054a04e0 fffff801`05ca8d9f nt!KiCommitThreadWait+0x23c
02 fffff880`054a05a0 fffff801`05f98841 nt!KeWaitForSingleObject+0x1cf
03 fffff880`054a0630 fffff801`061f253d nt!IopCancelAlertedRequest+0x71
04 fffff880`054a0670 fffff801`0604fc5d nt! ?? ::NNGAKEGL::`string'+0x1caaf
05 fffff880`054a0860 fffff801`060552b8 nt!ObpLookupObjectName+0x7a1
06 fffff880`054a0990 fffff801`06066ebe nt!ObOpenObjectByName+0x258
07 fffff880`054a0a60 fffff801`06067609 nt!IopCreateFile+0x37c
08 fffff880`054a0b00 fffff801`05c82053 nt!NtCreateFile+0x79
09 fffff880`054a0b90 000007fa`1a4930fa nt!KiSystemServiceCopyEnd+0x13
0a 00000038`d21bb478 000007fa`0677feef ntdll!NtCreateFile+0xa
0b 00000038`d21bb480 000007fa`0678e9a2 WDTFFuzzTestAction!DPETryOpenDevice+0x2b3
0c 00000038`d21bcde0 000007fa`0678e892 WDTFFuzzTestAction!CWDTFFuzz_MTestImpl::AttemptToOpenSurface+0x66
0d 00000038`d21bce50 000007fa`0678b84c WDTFFuzzTestAction!CWDTFFuzz_MTestImpl::FindAttackSurfaces+0x16e
0e 00000038`d21bf6c0 000007fa`0678a4d9 WDTFFuzzTestAction!CWDTFFuzz_MTestImpl::ActionThread+0x200
0f 00000038`d21bf760 000007fa`1a17167e WDTFFuzzTestAction!ActionThreadStart+0x9
10 00000038`d21bf790 000007fa`1a4ac3f1 KERNEL32!BaseThreadInitThunk+0x1a
11 00000038`d21bf7c0 00000000`00000000 ntdll!RtlUserThreadStart+0x1d

3: kd> .frame b
0b 00000038`d21bb480 000007fa`0678e9a2 WDTFFuzzTestAction!DPETryOpenDevice+0x2b3

3: kd> dv
szName = 0x00000038`d21bce90
bSync = 0n0
ppdevice = 0x00000038`d21bce10
messageBuffer = wchar_t [2048] "Attempting to open device : \DosDevices\root#multiportserial#0000#{05caff94-7b1e-420c-8c70-d8361bc4ee0a}"
oa = struct _OBJECT_ATTRIBUTES
```

## <span id="pnptriage"></span><span id="PNPTRIAGE"></span>!pnptriage


When you debug Device Fundamentals Reliability test hangs, you can use the **!pnptriage** command to list active PNP threads. Note that **!pnptriage** output contains tick counts for each PNP thread that is running in the system. When you investigate test hangs, threads that have high tick counts should be carefully reviewed because these threads can cause the tests to permanently hang and eventually fail because of a timeout.

## <span id="drvdebugext"></span><span id="DRVDEBUGEXT"></span>Driver debugging extensions


The following kernel debugger extensions can debug driver issues that can occur when you run Device Fundamentals Reliability tests: **!drvobj**, **!devnode**, **!devobj**, **!devstack**, and **!irp**. For more information about these extensions, see [Kernel-Mode Extensions](http://go.microsoft.com/fwlink/?LinkID=299555).

## <span id="debugext"></span><span id="DEBUGEXT"></span>Debugger extensions


**Debugging Tools for Windows** ships with additional debugger extensions that are useful to troubleshoot failures that can occur when you run tests against the following types of drivers: USB, Storage, NDIS, Graphics, Kernel-Mode Driver Framework (KMDF), and User-Mode Driver Framework (UMDF). For more information about these extensions, see [Specialized Extensions](http://go.microsoft.com/fwlink/?LinkID=299557). For more information about debugging tools for Windows, see [Download and Install Debugging Tools for Windows](http://go.microsoft.com/fwlink/?LinkID=299373).

## <span id="related_topics"></span>Related topics


[Troubleshooting Device Fundamentals Reliability Testing by using the Windows HLK](troubleshooting-device-fundamentals-reliability-testing-by-using-the-windows-hck.md)

 

 







