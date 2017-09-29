---
title: Windows Precision Touchpad HLK Requirements
description: Windows Precision Touchpad HLK Requirements
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 83c48e99-1466-4376-b9df-5c9b97f59dd4
---

# Windows Precision Touchpad HLK Requirements


**Precision Touchpad Fundamentals** (*Device.Input.PrecisionTouchpad.*)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>HLK requirement</th>
<th>Device</th>
<th>System</th>
<th>Associated JSON(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>.Buffering (USB only)</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.Edge.json</p></td>
</tr>
<tr class="even">
<td><p>.BusType</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.StaticValidation.json</p></td>
</tr>
<tr class="odd">
<td><p>.ThirdPartyDrivers</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.StaticValidation.json</p></td>
</tr>
<tr class="even">
<td><p>.WakeFunctionality</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.PowerStateReliability.json</p>
<p>Test.StaticValidation.json</p></td>
</tr>
<tr class="odd">
<td><p>.WakeSource</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.PowerStateReliability.json</p>
<p>Test.StaticValidation.json</p></td>
</tr>
<tr class="even">
<td><p>.FieldFirmwareUpdateable</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.FFU.json</p></td>
</tr>
</tbody>
</table>

 

**Precision Touchpad I2C Specific** (*Device.Input.PrecisionTouchpad.I2C.*)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>HLK requirement</th>
<th>Device</th>
<th>System</th>
<th>Associated JSON(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>.I2C.BusSpeed</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.StaticValidation.json</p></td>
</tr>
<tr class="even">
<td><p>.I2C.ActivePowerConsumption</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No test</p></td>
</tr>
<tr class="odd">
<td><p>.I2C.IdlePowerConsumption</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No test</p></td>
</tr>
<tr class="even">
<td><p>.I2C.ConnectedStandbyPowerConsumption</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No test</p></td>
</tr>
<tr class="odd">
<td><p>.I2C.ColdBootLatency</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.PowerStateReliability.json</p></td>
</tr>
<tr class="even">
<td><p>.I2C.ActiveToIdleTimeout</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No test</p></td>
</tr>
</tbody>
</table>

 

**Precision Touchpad USB Specific** (*Device.Input.PrecisionTouchpad.USB*.)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>HLK requirement</th>
<th>Device</th>
<th>System</th>
<th>Associated JSON(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>.USB.BusSpeed</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.StaticValidation.json</p></td>
</tr>
<tr class="even">
<td><p>.USB.ActivePowerConsumption</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No test</p></td>
</tr>
<tr class="odd">
<td><p>.USB.IdlePowerConsumption</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No test</p></td>
</tr>
<tr class="even">
<td><p>.USB.SleepPowerConsumption</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No test</p></td>
</tr>
<tr class="odd">
<td><p>.USB.ColdBootLatency</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.PowerStateReliability.json</p></td>
</tr>
<tr class="even">
<td><p>.USB.SelectiveSuspend</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.StaticValidation.json</p></td>
</tr>
</tbody>
</table>

 

**Precision Touchpad Mechanical Specific** (*Device.Input.PrecisionTouchpad.Hardware*.)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>HLK requirement</th>
<th>Device</th>
<th>System</th>
<th>Associated JSON(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>.Hardware.Clickpad</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.DeviceButton.json</p></td>
</tr>
<tr class="even">
<td><p>.Hardware.ClickpadPress</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.DeviceClickPressure.json</p></td>
</tr>
<tr class="odd">
<td><p>.Hardware.Length</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.DeviceHeight.json</p></td>
</tr>
<tr class="even">
<td><p>.Hardware.PressurePadPress</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.DeviceClickPressure.json</p></td>
</tr>
<tr class="odd">
<td><p>.Hardware.Width</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.DeviceWidth.json</p></td>
</tr>
<tr class="even">
<td><p>.Hardware.Bezel</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.DeviceBezel.json</p></td>
</tr>
</tbody>
</table>

 

**Precision Touchpad HID Specific** (*Device.Input.PrecisionTouchpad.HID.*)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>HLK requirement</th>
<th>Device</th>
<th>System</th>
<th>Associated JSON(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>.HIDCompliance.DefaultMode</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.DefaultMode.json</p></td>
</tr>
<tr class="even">
<td><p>.HIDCompliance.DeviceType</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.DeviceType.json</p></td>
</tr>
<tr class="odd">
<td><p>.HIDCompliance.HIDCompliance</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.PositionalAccuracyManual.json</p>
<p>Test.Confidence.json</p></td>
</tr>
<tr class="even">
<td><p>.HIDCompliance.MouseMode</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.MouseMode.json</p></td>
</tr>
<tr class="odd">
<td><p>.HIDCompliance.PTPQHA</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.PTPHQA.json</p></td>
</tr>
<tr class="even">
<td><p>.HIDCompliance.SelectiveReporting</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.SelectiveReporting.json</p></td>
</tr>
<tr class="odd">
<td><p>.HIDCompliance.SwitchableMode</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.MouseMode.json</p></td>
</tr>
<tr class="even">
<td><p>.HIDCompliance.Timestamp</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.PositionalAccuracyManual.json</p></td>
</tr>
<tr class="odd">
<td><p>.HIDCompliance.TouchpadMode</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.MouseMode.json</p></td>
</tr>
<tr class="even">
<td><p>.HIDCompliance.ValidRange</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.PositionalAccuracyManual.json</p></td>
</tr>
</tbody>
</table>

 

**Precision Touchpad Performance Specific** (*Device.Input.PrecisionTouchpad.Performance*.)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>HLK requirement</th>
<th>Device</th>
<th>System</th>
<th>Associated JSON(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>.Performance.ActiveTouchdownLatency</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.AudioTouch.json</p></td>
</tr>
<tr class="even">
<td><p>.Performance.IdleTouchdownLatency</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.PowerStateReliability.json</p></td>
</tr>
<tr class="odd">
<td><p>.Performance.MinMaxContacts</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.MinMaxContacts.json</p></td>
</tr>
<tr class="even">
<td><p>.Performance.MinSeparation</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.Aliasing.json</p></td>
</tr>
<tr class="odd">
<td><p>.Performance.PanLatency</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.StepMotor.json</p></td>
</tr>
<tr class="even">
<td><p>.Performance.ReportRate</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.ReportRate.json</p>
<p>Test.ReportRateMultiple.json</p></td>
</tr>
</tbody>
</table>

 

**Precision Touchpad Precision Specific** (*Device.Input.PrecisionTouchpad.Precision*.)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>HLK requirement</th>
<th>Device</th>
<th>System</th>
<th>Associated JSON(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>.Precision.ContactDivergence</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.ConvergeDivergeHorizontal.json</p>
<p>Test.ConvergeDivergeVertical.json</p>
<p>Test.ConvergeDivergeDiagonal.json</p></td>
</tr>
<tr class="even">
<td><p>.Precision.HVInputSeparation</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.LinearityHorizontalMultiple.json</p>
<p>Test.LinearityVerticalMultiple.json</p></td>
</tr>
<tr class="odd">
<td><p>.Precision.DiagonalInputSeparation</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.LinearityDiagonalMultiple.json</p></td>
</tr>
<tr class="even">
<td><p>.Precision.EdgeDetection</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.Edge.json</p></td>
</tr>
<tr class="odd">
<td><p>.Precision.Geometry (Optional)</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.Geometry.json</p></td>
</tr>
<tr class="even">
<td><p>.Precision.Linearity</p>
<p>.Precision.MotionJitter</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.LinearityHorizontal.json</p>
<p>Test.LinearityVertical.json</p>
<p>Test.LinearityDiagonal.json</p>
<p>Test.LinearityHorizontalMultiple.json</p>
<p>Test.LinearityVerticalMultiple.json</p>
<p>Test.LinearityDiagonalMultiple.json</p></td>
</tr>
<tr class="odd">
<td><p>.Precision.MaxReportZHeight</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.ZHeight.json</p></td>
</tr>
<tr class="even">
<td><p>.Precision.Position</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.PositionalAccuracy.json</p>
<p>Test.PositionalAccuracyManual.json</p></td>
</tr>
<tr class="odd">
<td><p>.Precision.StationaryJitter</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.StationaryJitter.json</p>
<p>Test.StationaryJitterMultiple.json</p></td>
</tr>
<tr class="even">
<td><p>.Precision.InputResolution</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.InputResolution.json</p></td>
</tr>
</tbody>
</table>

 

**Precision Touchpad Reliability Specific** (*Device.Input.PrecisionTouchpad.Reliability*.)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>HLK requirement</th>
<th>Device</th>
<th>System</th>
<th>Associated JSON(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>.Reliability.ContactsReported</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.AllAreas.json</p></td>
</tr>
<tr class="even">
<td><p>.Reliability.ContactSuppression</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Test.GreaterMaxContacts.json</p></td>
</tr>
<tr class="odd">
<td><p>.Reliability.FalseContacts</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.GhostReporting.json</p></td>
</tr>
<tr class="even">
<td><p>.Reliability.PowerStates</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Test.PowerStateReliability.json</p></td>
</tr>
</tbody>
</table>

 

## <span id="related_topics"></span>Related topics


[Windows Precision Touchpad Certification Process](windows-precision-touchpad-certification-process.md)

[Windows Precision Touchpad Device Validation Guide](windows-precision-touchpad-device-validation-guide.md)

 

 







