---
title: Target.RedistributeScheduledTests Method
description: Target.RedistributeScheduledTests Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0F9E2122-1C9C-44CA-AA02-DE53B32DD005
---

# Target.RedistributeScheduledTests Method


Method to redistribute tests across targets which have been added to a project.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public static void RedistributeScheduledTests (`

          `IEnumerable<Target> newTargets,`

          `out IList<TestResult> cancelFailedResults,`

          `out IList<TestResult> cancelledResults,`

          `out IList<TestResult> scheduledResults,`

          `out IList<Test> rescheduleFailedTests`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*newTargets*

List of targets to redistribute test across.

*cancelFailedResults*

List of results that failed to be cancelled before a reschedule.

*cancelledResults*

List of results that were cancelled and then rescheduled.

*scheduledResults*

List of newly scheduled results that replaced the results that a cancel was attempted on regardless of success.

*rescheduleFailedTests*

List of tests that failed to be rescheduled.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






