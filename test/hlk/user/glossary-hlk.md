---
title: HLK Glossary
description: HLK Glossary
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: eed2ab3d-dae7-4d74-962d-dee0a61f03c2
---

# HLK Glossary


This section provides definitions of commonly used words or terms within the Windows Hardware Lab Kit (Windows HLK)

## <span id="C"></span><span id="c"></span>C


**child machine pool**

A machine pool that is contained within another ("parent") machine pool. Several child machine pools can be created as part of a parent machine pool in the machine pool hierarchy.

**client computer**

A computer that the HLK client has been installed on. You use HLK to run tests on client computers.

**configuration job**

A job that sets the value of a dimension. Configuration jobs can be executed automatically to satisfy the constraints of another job that is executing.

**constraint**

A triplet that consists of a dimension, an operator, and a value. A constraint is part of the job definition. A job can only execute on client computers that match the job's constraints. For example, a job that had the following constraint could only be executed on client computers that have an x86 processor. See also **dimension**.

**context**

A set of constraints that are specified in a job. For example, if a job included the constraints "WTT\\OS equals Windows XP" and "WTT\\RAM-MB greater than 512", then these two constraints would form the job's context. See also **dimension**, **mix**.

**controller**

A computer that the HLK controller has been installed on. The controller stores data about jobs, client computers, and HLK users, and it manages job scheduling.

**Copy File task**

A task that copies files from a remote location to the client computer.

**Copy Result task**

A task that copies files from the client computer to a remote location.

**custom dependencies**

User-defined relationships between tasks in a job that specify the order in which the tasks execute.

## <span id="D"></span><span id="d"></span>D


**Dashboard**

The website that you use to submit or manage your packages as part of the Windows Certification Program. This site replaces Winqual.

**daemon task**

A task that begins running either before all other tasks in a phase, or after all other tasks in a phase. A daemon task can run in parallel with other tasks.

**DCT**

See Display Compatibility Test.

**default pool**

The **machine pool** that computers are initially placed in when the HLK client is installed.

**dimension**

A key/value pair that identifies a characteristic of a client computer. For example, a dimension with the key "ProcessorCount" might have the value "1" on one client computer and the value "4" on another client computer.

A job can include constraints, which indicate that the job can run only on client computers that have a specific value for a dimension.

**Display Compatibility Test**

A test that verifies display functionality on computers running Windows.

**HLK administrator**

An HLK user account that has administrator privileges. An HLK administrator can create machine pools, create HLK user accounts, and grant privileges to the HLK user accounts.

An HLK administrator often has an account with administrative privileges on the computer that is running the HLK controller, but this type of account is not required.

When you install the HLK controller, an HLK user account is automatically created for you, and your account is automatically given administrator privileges.

## <span id="E"></span><span id="e"></span>E


**EA**

See also execution agent (EA).

**execution agent (EA)**

A component of the HLK client that executes the tasks of a job.

**Execute task**

A task that executes a command line.

## <span id="F"></span><span id="f"></span>F


**Feature**

An attribute of a job that organizes jobs within a hierarchy.

Within Job Explorer, you expand nodes of the feature hierarchy to locate jobs.

## <span id="G"></span><span id="g"></span>G


**gatherer**

A program that collects information about a client computer.

**global parameter**

A **parameter** that can be used by all jobs on the HLK controller. You can define global parameters by using the **Management Console**.

## <span id="H"></span><span id="h"></span>H


**HLK Client**

A test computer that the HLK client application has been installed on. You use HLK Studio to run tests on client (test) computers.

**HLK Controller**

The HLK Controller stores data about jobs, client computers, and HLK users, and it manages job scheduling.

A collection of string values which should provide sufficient information to correlate to see if a driver should be loaded for any specific device.

**HLK Manager**

This item was previous known as the DTM Studio. Use the HLK Manager to access Windows Logo Kit functionality that is included in the Windows HLK.

**HLK Studio**

The user interface for Windows HLK. By using HLK Studio, you can run tests, monitor the progress of jobs, and review test logs.

## <span id="J"></span><span id="j"></span>J


**job**

A collection of **tasks** that can be run on a client computer. A job describes the order in which to execute the tasks. A job can identify conditions that a client computer must meet to run the job.

## <span id="L"></span><span id="l"></span>L


**library job**

A job that has been stored and can be used by another job.

**LLU**

See **Local Logical User**.

**Local Logical User (LLU)**

A mapping from a variable to a user account on each client computer.

For example, the Local Logical User (LLU) with the name *AdminUser* might map to the user account *MyDomain\\User6* with a password of *My^Password%23* on one client computer, and to the user account *MyDomain\\User32* with a password of *My\#Password@97* on another client computer.

## <span id="M"></span><span id="m"></span>M


**machine**

A **client computer** that is a member of a **machine pool**. Client computers that are not in the System machine pool are test clients that you can execute jobs on.

**machine pool**

A virtual collection of computers, devices, or both that is created by a user to help manage the testing process.

**Machine Set**

A set of computers that play the same role in a job that requires multiple computers. For example, a job that required more than one computer might have a client machine set and a server machine set.

**Manual Prompt task**

A task that displays a prompt and options to the user and waits for the user to make a selection.

**Master client**

The test computer that issues commands to another test computer on a test network.

**MC**

See Master client.

**mix**

A set of contexts that is specified in a job. The job can be executed on a computer that matches any of the contexts. For example, a job could specify a mix that consisted of two contexts. Context 1 could consist of the constraints "WTT\\OS equals Windows XP" and "WTT\\RAM-MB greater than 512". Context 2 could consist of the constraints "WTT\\OS equals Windows Server 2003" and "WTT\\RAM-MB greater than 1000". In this case, the job's mix would specify that the job could run on client computers with Windows XP and more than 512 MB of RAM, or client computers with Windows Server 2003 and more than 1GB of RAM. See also **constraint**.

## <span id="P"></span><span id="p"></span>P


**package**

A container that can include **jobs** and the other data that is required to run the jobs. Packages are used for grouping, storing, and sharing jobs.

**Parameter**

A variable that provides information to a task. Global parameters are defined by using the Management Console. Local variables are defined within a job. Default values for parameters can be overridden when a job is scheduled.

**PD**

Push Daemon. A component of the HLK controller that sends a job to the client computer to execute.

## <span id="R"></span><span id="r"></span>R


**result**

The information that is created when you execute a job. Each instance of a job creates a result that contains the start time, end time, and completion status of the job's tasks; any error messages; a link to the job's log files; and more detailed information.

**result collection**

A group of results. When you execute a job, a result collection is created to contain the job's results. If more than one instance of a job is created when a job is executed, the results of all of the job instances are stored in one result collection. You can specify your own result collection to hold results, and you can add, modify, delete, or move results within result collections.

**Run Job task**

A task that runs a library job.

## <span id="S"></span><span id="s"></span>S


**SC**

See Subordinate client.

**schedule**

Adds a job to the list of jobs that are ready to run. A job that has been scheduled will run when a client computer that meets the job's constraints is available.

**scheduler**

A component of the HLK controller that assigns a job to execute on a specific client computer.

**System under test**

The computer being tested.

**Subordinate client**

A computer that acts as a client during testing on a network.

**SUT**

See System under test.

## <span id="T"></span><span id="t"></span>T


**task**

A unit of work to be done on a client computer. The most common tasks execute a command line, copy files, or prompt the user to perform a manual action.

**test harness**

A software application that is used to automate testing.

## <span id="W"></span><span id="w"></span>W


**Windows Certification Program**

A previous program that supported hardware submission for Windows 8.1.

**Windows Compatibility Program**

The new program that supported hardware submission for Windows 10.

**Windows Hardware Certification Kit**

The application provided as part of the previous Windows Certification Program that enables you to test your Windows 8.1 device or computer for Windows certification. Also known as the Windows HLK.

**Windows Hardware Lab Kit**

The kit provided as part of the Windows Hardware Compatibility Program. Also know as the Windows HLK.

**Winqual**

The previous web service that supported hardware submission for Windows 7. This site is replaced by the Hardware Dashboard in the Windows Dev Center.

 

 






