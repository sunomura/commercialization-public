---
title: GetDiagnosticSummaryLog Method
description: GetDiagnosticSummaryLog Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9E8934BE-3281-4235-AF11-CAD82EDEE0F1
---

# GetDiagnosticSummaryLog Method


This method retrieves an instance of the diagnostic summary object for the test run, if one is available.

A diagnostic summary log is copied to the controller only after the test run is complete (the test could pass or fail).

The diagnostic summary log captures any bugcheck(s) that occur during the test run.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


For sample usage, see the [Diagnostic Bugcheck Summary](..\developer\diagnostic-bugcheck-summary.md) sample.

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public DiagnosticSummaryLog GetDiagnosticSummaryLog()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns [DiagnosticSummaryLog](diagnosticsummarylog-class.md), an object representation of a diagnostic summary log, if one is available. Otherwise, returns **null**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






