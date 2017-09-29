---
title: MBN WHLK Content for a CDMA Device
description: MBN WHLK Content for a CDMA Device
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cad5855a-9366-423d-aa84-11597b3b737d
---

# MBN WHLK Content for a CDMA Device


The purpose of this document is to provide a comprehensive view of the MBN WHLK requirements, operations and expectations, by showing the summary log results of a successful test run.

## <span id="How_to_read_MBN_Logs"></span><span id="how_to_read_mbn_logs"></span><span id="HOW_TO_READ_MBN_LOGS"></span>How to read MBN Logs


The MBN operations are listed in chronological order. The beginning of an operation will be shown in black and the successful completion of an operation will be shown with a leading "PASS:". If an operation has sub operations, the entries will be indented and be between the beginning and end operation. If the operation fails in test, it will be shown with a leading "FAIL:".

## <span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example


``` syntax
Attempt to read NDIS Coinstaller values
   Attempt to read IfType
   PASS: Attempt to read IfType, succeeded
   Attempt to read MediaType
   PASS: Attempt to read MediaType, succeeded
   Attempt to read PhysicalMediaType
   PASS: Attempt to read PhysicalMediaType, succeeded
   Attempt to read EnableDhcp
      Attempt to read UpperRange
      PASS: Attempt to read UpperRange, succeeded
      Attempt to read LowerRange
      PASS: Attempt to read LowerRange, succeeded
   PASS: Attempt to read EnableDhcp, succeeded
PASS: Attempt to read NDIS Coinstaller values, succeeded
```

## <span id="How_to_get_a_tracing_from_MBN_Tests"></span><span id="how_to_get_a_tracing_from_mbn_tests"></span><span id="HOW_TO_GET_A_TRACING_FROM_MBN_TESTS"></span>How to get a tracing from MBN Tests


The MBN Tests utilize Windows Software trace preprocessor (WPP). A trace can be obtained by using the following commands:

1.  tracelog.exe -b 64 -cir 10 -start MBNWHLK -ft 0 -guid \#{d58c1268-b309-11d1-969e-0000f875a532} -flag 0x7fffffff -level 5 -f MBNWHLK.bin

2.  Execute Test

3.  tracelog.exe -stop MBNWHLK

4.  MBNWHLK.bin will then be available in the current directory

## <span id="Using_MBN_Tests_outside_of_WHLK"></span><span id="using_mbn_tests_outside_of_whlk"></span><span id="USING_MBN_TESTS_OUTSIDE_OF_WHLK"></span>Using MBN Tests outside of WHLK


MBN Tests are built on Windows Test Authoring and Execution Framework (TAEF). The tests can be easily executed from the command line.

### <span id="To_view_available_MBN_tests"></span><span id="to_view_available_mbn_tests"></span><span id="TO_VIEW_AVAILABLE_MBN_TESTS"></span>To view available MBN tests

te.exe &lt;Test Dll&gt; /list

### <span id="To_execute_MBN_tests"></span><span id="to_execute_mbn_tests"></span><span id="TO_EXECUTE_MBN_TESTS"></span>To execute MBN tests

te.exe &lt;Test Dll&gt; /name:&lt;Test Name&gt; &lt;Test Parameters&gt;

### <span id="Test_Parameters"></span><span id="test_parameters"></span><span id="TEST_PARAMETERS"></span>Test Parameters

-   INTF – Specifies which device to target testing. The value can be either interface MAC or GUID. This parameter is optional, if not specified the tests will use any WWAN Interface on the machine.

-   PIN1 – Specifies the PIN1 associated with the device. This value is only required for the PIN tests and only if the device supports PIN1. If not specified the test will execute and fail if appropriate.

-   PUK1 – Specifies the PUK1 associated with the device. This value is only required for the PIN tests and only if the device supports PUK1. If not specified the test will execute and fail if appropriate. Be very careful about providing the PUK1 on a real device. If an incorrect PUK1 is provided or the device does not support PUK1 the device could be irreversibly locked.

-   WEBDOC8K – Specifies a web doc over 8K in size. This parameter is optional, if provided the test will use this URL rather than the default URL.

-   WEBDOC1024K – Specifies a web doc over 1024K in size. This parameter is optional, if provided the test will use this URL rather than the default URL.

-   DevPhoneNumber – Specifies the phone number of the device. This parameter is optional and used only by the SMS Tests. If the parameter is not specified the test will attempt to retrieve the phone number from the device.

### <span id="Command_Line_Examples"></span><span id="command_line_examples"></span><span id="COMMAND_LINE_EXAMPLES"></span>Command Line Examples

``` syntax
te.exe Win8.MBN.CDMA.TestConnect.dll /name:Win8::MBN::TestConnect::ConnectDisconnectte.exe Win8.MBN.CDMA.TestConnect.dll /name:Win8::MBN::TestConnect* /p:INTF=00-A0-D5-FF-FF-A9te.exe Win8.MBN.CDMA.TestConnect.dll /name:Win8::MBN::TestConnect* /p:INTF=00A0D5FFFFA9 te.exe Win8.MBN.CDMA.TestPin.dll /name:Win8::MBN::TestPin* /p:INTF=00:A0:D5:FF:FF:A9 /p:PIN1=1234 /p:PUK1=12345678te.exe Win8.MBN.CDMA.TestSms.dll /name:Win8::MBN::TestSms* /p:DevPhoneNumber=4254437000te.exe Win8.MBN.CDMA.TestConnect.dll /p:WEBDOC8K=http://www.microsoft.com/windows/using/tools/igd/StaticContent/igdprobedocs/ws/test13.txt
```

## <span id="Mobile_Broadband_CDMA_Test_List"></span><span id="mobile_broadband_cdma_test_list"></span><span id="MOBILE_BROADBAND_CDMA_TEST_LIST"></span>Mobile Broadband CDMA Test List


<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestClassDriver::VerifyClassDriver](#s1)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestConnect::ConnectDisconnect](#s2)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestConnect::ConnectAndTraffic](#s3)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestConnect::ConnectWhenPacketServiceIsDetached](#s4)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestSetup::NDISSetup](#s5)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestGenOids::PhysicalMediumQuery](#s6)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestGenOids::MediaSupportedQuery](#s7)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestGenOids::SupportedOidQueryWin8](#s8)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestDriverCaps::Query](#s9)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestDeviceCaps::Query](#s10)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestDeviceServices::Query](#s11)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestDisableEnable::DisableEnableWhileIdle](#s12)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestDisableEnable::ConnectDisableEnableConnect](#s13)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestSetup::NDISSetup](#s14)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestGenOids::PhysicalMediumQuery](#s15)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestGenOids::MediaSupportedQuery](#s16)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestGenOids::SupportedOidQueryWin8](#s17)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestDriverCaps::Query](#s18)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestGenOids::PhysicalMediumQuery](#s19)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestGenOids::MediaSupportedQuery](#s20)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestGenOids::SupportedOidQueryWin8](#s21)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestHomeProvider::Query](#s22)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestLoopBack::TestVerifyTrafficFixed](#s23)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestLoopBack::TestVerifyTrafficIncrement](#s24)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestMultiCarrier::SetHomeProvider](#s25)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestPacketService::AttachDetach](#s26)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestPin::PinListQueryRadioOn](#s27)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestPin::PinListQueryRadioOff](#s28)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestPin::NoPinSupport](#s29)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestPin::PinExSetEnableDisableWithValidPin](#s30)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestPin::PinExSetDisableIncorrectPinWithValidLength](#s31)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestPin::PukEnableDisableThroughIncorrectPinExDisable](#s32)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestPowerStates::SleepAndWake](#s33)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestPowerStates::HibernateAndWake](#s34)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestPreferredProvider::Query](#s35)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestPreferredProvider::AddRemovePreferredProvider](#s36)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestPreferredProvider::AddRemoveForbiddenProvider](#s37)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestPreferredProvider::AddRemovePreferredForbiddenProvider](#s38)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestRadioStateHw::TurnHwRadioOffOnWhenRegistered](#s39)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestRadioStateHw::TurnHwRadioOffOnWhenPacketServiceAttached](#s40)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestRadioStateHw::TurnHwRadioOffOnWhenConnected](#s41)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestRadioStateSw::TurnSwRadioOffOnWhenRegistered](#s42)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestRadioStateSw::TurnSwRadioOffOnWhenPacketServiceAttached](#s43)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestRadioStateSw::TurnSwRadioOffOnWhenConnected](#s44)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestReadyInfo::Query](#s45)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestRegisterState::Query](#s46)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestRegisterState::RegisterAutomatic](#s47)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestRegisterState::RegisterManualToHomeProvider](#s48)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestRemoval::RemovalWhenRegistered](#s49)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestRemoval::RemovalWhenPacketSvcAttached](#s50)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestRemoval::RemovalWhenConnected](#s51)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestSelectiveSuspend::SelectiveSuspendConnected](#s52)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestSetup::NDISSetup](#s53)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestSignalState::Query](#s54)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestSms::SmsConfigQuery](#s55)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestSms::SmsStatusQuery](#s56)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestSms::SmsSendMessageToSelf](#s57)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestSms::SmsDeleteAllMessages](#s58)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestSms::SmsReadAllMessages](#s59)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestSms::SmsReadNewMessages](#s60)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestVisibleProvider::RadioOff](#s61)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestVisibleProvider::Registered](#s62)</p></td>
</tr>
<tr class="odd">
<td><p>[Test Summary: Win8MBN::TestVisibleProvider::Connected](#s63)</p></td>
</tr>
<tr class="even">
<td><p>[Test Summary: Win8MBN::TestWake::WakeMachineFromConnectedStandbyWithSmsMessage](#s64)</p></td>
</tr>
</tbody>
</table>

 

### <span id="s1"></span><span id="S1"></span>Test Summary: Win8MBN::TestClassDriver::VerifyClassDriver

The test verifies a USB device uses class driver.

``` syntax
If device is usb, verify classdriver is implemented
   Attempt to query interface device info data
   PASS: Attempt to query interface device info data, succeeded
   Determine if device is using MB Class Driver
   PASS: Device is not using class driver
   Recursively check for usb
      Verify device is not using usb [{F02F01C1-CE76-49B2-8035-898DB8328951}\CDMAVMP\1&79F5D87&0&03]
      PASS: Device is not using usb
      Recursively check for usb
         Verify device is not using usb [ROOT\SYSTEM\0001]
         PASS: Device is not using usb
         Recursively check for usb
         PASS: Recursively check for usb, succeeded
      PASS: Recursively check for usb, succeeded
   PASS: Recursively check for usb, succeeded
PASS: Driver verified
```

### <span id="s2"></span><span id="S2"></span>Test Summary: Win8MBN::TestConnect::ConnectDisconnect

The test verifies the test can sucessfully connect and disconnect.

``` syntax
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n16 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n639 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0x4e
      PASS: Connection id of returned context state is 0x4e
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n78 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0x4e
PASS: Connection id of returned context state is 0x4e
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s3"></span><span id="S3"></span>Test Summary: Win8MBN::TestConnect::ConnectAndTraffic

The test connects to the home network and downloads a file from the Internet.

``` syntax
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n15 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n94 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0x59
      PASS: Connection id of returned context state is 0x59
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Verify TCP/IP shows interface as connected in 0x3a98 ms
PASS: TCP/IP shows interface as connected in 0x196 ms
Attempt to remove non wwan default routes
PASS: Attempt to remove non wwan default routes, succeeded
Attempt to download web doc
PASS: Attempt to download web doc, succeeded
Attempt to restore non wwan default routes
PASS: Attempt to restore non wwan default routes, succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n31 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0x59
PASS: Connection id of returned context state is 0x59
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s4"></span><span id="S4"></span>Test Summary: Win8MBN::TestConnect::ConnectWhenPacketServiceIsDetached

The test verifies connection fails with WWAN\_STATUS\_PACKET\_SVC\_DETACHED when packet serivce is detached.

``` syntax
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n16 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Verify device does not support auto packet service attach
      PASS: Device does not support auto packet service attach
      Attempt to set packet service (WwanPacketServiceActionDetach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionDetach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_PACKET_SVC_DETACHED[0xc004000d]
         PASS: Status is WWAN_STATUS_PACKET_SVC_DETACHED[0xc004000d]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
```

### <span id="s5"></span><span id="S5"></span>Test Summary: Win8MBN::TestSetup::NDISSetup

The test verifies the NDIS CoInstaller values.

``` syntax
Attempt to NDIS Coinstaller values
   Attempt to read IfType
   PASS: Attempt to read IfType, succeeded
   Attempt to read MediaType
   PASS: Attempt to read MediaType, succeeded
   Attempt to read PhysicalMediaType
   PASS: Attempt to read PhysicalMediaType, succeeded
   Attempt to read EnableDhcp
      Attempt to read UpperRange
      PASS: Attempt to read UpperRange, succeeded
      Attempt to read LowerRange
      PASS: Attempt to read LowerRange, succeeded
   PASS: Attempt to read EnableDhcp, succeeded
PASS: Attempt to read NDIS Coinstaller values, succeeded
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify MediaType is NdisMediumWirelessWan
PASS: MediaType is NdisMediumWirelessWan
Verify PhysicalMediaType is NdisPhysicalMediumWirelessWan
PASS: PhysicalMediaType is NdisPhysicalMediumWirelessWan
Verify EnableDhcp is 0
PASS: EnableDhcp is 0
Verify UpperRange contains flpp4
PASS: UpperRange (flpp4, flpp6) contains flpp4
Verify LowerRange is ppip
PASS: LowerRange is ppip
```

### <span id="s6"></span><span id="S6"></span>Test Summary: Win8MBN::TestGenOids::PhysicalMediumQuery

The test queries physical medium and verifies the value.

``` syntax
Attempt OID_GEN_PHYSICAL_MEDIUM query
PASS: OID_GEN_PHYSICAL_MEDIUM succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
Verify indication length is 0x4
PASS: Indication length is 0x4
Verify OID_GEN_PHYSICAL_MEDIUM returned NdisPhysicalMediumWirelessWan
PASS: Ndis physical medium (NdisPhysicalMediumWirelessWan[0x8]) is valid
```

### <span id="s7"></span><span id="S7"></span>Test Summary: Win8MBN::TestGenOids::MediaSupportedQuery

The test queries media supported and verifies the value.

``` syntax
Attempt OID_GEN_MEDIA_SUPPORTED query
PASS: OID_GEN_MEDIA_SUPPORTED succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
Verify indication length is 0x4
PASS: Indication length is 0x4
Verify OID_GEN_MEDIA_SUPPORTED returned NdisMediumWirelessWan
PASS: Ndis medium (NdisMediumWirelessWan[0x9]) is valid
```

### <span id="s8"></span><span id="S8"></span>Test Summary: Win8MBN::TestGenOids::SupportedOidQueryWin8

The test queries supported oid and verifies the value.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt OID_GEN_SUPPORTED_LIST query
PASS: OID_GEN_SUPPORTED_LIST succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
Verify OID_GEN_PHYSICAL_MEDIUM is supported
PASS: OID_GEN_PHYSICAL_MEDIUM is supported
Verify OID_GEN_MEDIA_SUPPORTED is supported
PASS: OID_GEN_MEDIA_SUPPORTED is supported
Verify OID_GEN_SUPPORTED_LIST is supported
PASS: OID_GEN_SUPPORTED_LIST is supported
Verify OID_WWAN_DEVICE_CAPS is supported
PASS: OID_WWAN_DEVICE_CAPS is supported
Verify OID_WWAN_READY_INFO is supported
PASS: OID_WWAN_READY_INFO is supported
Verify OID_WWAN_REGISTER_STATE is supported
PASS: OID_WWAN_REGISTER_STATE is supported
Verify OID_WWAN_RADIO_STATE is supported
PASS: OID_WWAN_RADIO_STATE is supported
Verify OID_WWAN_PIN_LIST is supported
PASS: OID_WWAN_PIN_LIST is supported
Verify OID_WWAN_HOME_PROVIDER is supported
PASS: OID_WWAN_HOME_PROVIDER is supported
Verify OID_WWAN_PACKET_SERVICE is supported
PASS: OID_WWAN_PACKET_SERVICE is supported
Verify OID_WWAN_SIGNAL_STATE is supported
PASS: OID_WWAN_SIGNAL_STATE is supported
Verify OID_WWAN_CONNECT is supported
PASS: OID_WWAN_CONNECT is supported
Verify OID_WWAN_PROVISIONED_CONTEXTS is supported
PASS: OID_WWAN_PROVISIONED_CONTEXTS is supported
Verify OID_WWAN_SMS_CONFIGURATION is supported
PASS: OID_WWAN_SMS_CONFIGURATION is supported
Verify OID_WWAN_SMS_READ is supported
PASS: OID_WWAN_SMS_READ is supported
Verify OID_WWAN_SMS_SEND is supported
PASS: OID_WWAN_SMS_SEND is supported
Verify OID_WWAN_SMS_DELETE is supported
PASS: OID_WWAN_SMS_DELETE is supported
Verify OID_WWAN_PIN_EX is supported
PASS: OID_WWAN_PIN_EX is supported
```

### <span id="s9"></span><span id="S9"></span>Test Summary: Win8MBN::TestDriverCaps::Query

The test queries driver caps and verifies data members.

``` syntax
Attempt to query driver capabilities
   Attempt OID_WWAN_DRIVER_CAPS query
   PASS: OID_WWAN_DRIVER_CAPS succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
PASS: Attempt to query driver capabilities succeeded
Verify indication length is equal to or greater than 0x10
PASS: Indication length is valid
Verify ulMajorVersion is valid
PASS: ulMajorVersion (0x2) is valid
Verify ulMinorVersion is valid
PASS: ulMinorVersion (0x0) is valid
Verify ulDriverCaps is valid
PASS: ulDriverCaps (0x0) is valid
```

### <span id="s10"></span><span id="S10"></span>Test Summary: Win8MBN::TestDeviceCaps::Query

The test queries device caps and verifies data members.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify indication length is equal to or greater than 0x160
PASS: Indication length (0x160) is valid
Header.Revision is NDIS_WWAN_DEVICE_CAPS_REVISION_2
PASS: Header.Revision is NDIS_WWAN_DEVICE_CAPS_REVISION_2
Verify uStatus is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify CellularClassListHeader.ElementType is WwanStructCellularClass
PASS: CellularClassListHeader.ElementType is WwanStructCellularClass
Verify CellularClassListHeader.ElementCount is less than WwanCellularClassMax
PASS: CellularClassListHeader.ElementCount (0x0) is less than WwanCellularClassMax
Verify WwanDeviceType is valid
PASS: WwanDeviceType is valid
Verify WwanCellularClass is valid
PASS: WwanCellularClass is valid
Verify WwanVoiceClass is valid
PASS: WwanVoiceClass is valid
Verify WwanSimClass is valid
PASS: WwanSimClass is valid
Verify WwanDataClass are valid
PASS: WwanDataClass are valid for this device
Verify CustomDataClass is NULL terminated
PASS: CustomDataClass is NULL terminated
Verify WwanCdmaBandClass are valid
PASS: WwanCdmaBandClass are valid for this device
Verify WwanGsmBandClass are valid
PASS: WwanBandClass are valid for this device
Verify CustomBandClass is NULL terminated
PASS: CustomBandClass is NULL terminated
Verify WwanSmsCaps are valid
PASS: WwanSmsCaps are valid for this device
Verify WwanControlCaps are valid
PASS: WwanControlCaps are valid for this device
Verify DeviceId is NULL terminated
PASS: DeviceId is NULL terminated
Verify Manufacturer is NULL Terminated
PASS: Manufacturer is NULL terminated
Verify Model is NULL terminated
PASS: Model is NULL terminated
Verify FirmwareInfo is NULL terminated
PASS: FirmwareInfo is NULL terminated
Verify MaxActivatedContexts > 0
PASS: MaxActivatedContexts is > 0
```

### <span id="s11"></span><span id="S11"></span>Test Summary: Win8MBN::TestDeviceServices::Query

The test queries device services and verifies data members.

``` syntax
Attempt to query enumerate device services
   Attempt OID_WWAN_ENUMERATE_DEVICE_SERVICES query
   PASS: OID_WWAN_ENUMERATE_DEVICE_SERVICES succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query enumerate device services succeeded
Attempt to query device service commands
   Attempt OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS query
   PASS: OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device service commands succeeded
Attempt to query device service commands
   Attempt OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS query
   PASS: OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device service commands succeeded
Attempt to query device service commands
   Attempt OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS query
   PASS: OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device service commands succeeded
Attempt to query device service commands
   Attempt OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS query
   PASS: OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device service commands succeeded
Attempt to query device service commands
   Attempt OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS query
   PASS: OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device service commands succeeded
Attempt to query device service commands
   Attempt OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS query
   PASS: OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device service commands succeeded
Attempt to query device service commands
   Attempt OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS query
   PASS: OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device service commands succeeded
Attempt to query device service commands
   Attempt OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS query
   PASS: OID_WWAN_ENUMERATE_DEVICE_SERVICE_COMMANDS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device service commands succeeded
```

### <span id="s12"></span><span id="S12"></span>Test Summary: Win8MBN::TestDisableEnable::DisableEnableWhileIdle

The test disables and enables the device while idle.

``` syntax
Attempt to disable interface ({F7C10FC7-4FBD-4BD1-A38A-64B5659A8C6A})
PASS: Attempt to disable interface ({F7C10FC7-4FBD-4BD1-A38A-64B5659A8C6A}), succeeded
Attempt to enable interface ({F7C10FC7-4FBD-4BD1-A38A-64B5659A8C6A})
PASS: Attempt to enable interface ({F7C10FC7-4FBD-4BD1-A38A-64B5659A8C6A}), succeeded
Wait 0xea60 ms for device to enter WwanReadyStateInitialized
PASS: Wait for device to enter WwanReadyStateInitialized, succeeded
Performance Check:Verify WwanReadyStateInitialized occured under 0n60000 ms
PASS: WwanReadyStateInitialized occured in 0n452 ms
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
```

### <span id="s13"></span><span id="S13"></span>Test Summary: Win8MBN::TestDisableEnable::ConnectDisableEnableConnect

The test connects, disables, enables, and connects the device.

``` syntax
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n94 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0x26
      PASS: Connection id of returned context state is 0x26
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to disable interface ({F7C10FC7-4FBD-4BD1-A38A-64B5659A8C6A})
PASS: Attempt to disable interface ({F7C10FC7-4FBD-4BD1-A38A-64B5659A8C6A}), succeeded
Attempt to enable interface ({F7C10FC7-4FBD-4BD1-A38A-64B5659A8C6A})
PASS: Attempt to enable interface ({F7C10FC7-4FBD-4BD1-A38A-64B5659A8C6A}), succeeded
Wait 0xea60 ms for device to enter WwanReadyStateInitialized
PASS: Wait for device to enter WwanReadyStateInitialized, succeeded
Performance Check:Verify WwanReadyStateInitialized occured under 0n60000 ms
PASS: WwanReadyStateInitialized occured in 0n780 ms
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n15 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n94 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0xc0
      PASS: Connection id of returned context state is 0xc0
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n47 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0xc0
PASS: Connection id of returned context state is 0xc0
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s14"></span><span id="S14"></span>Test Summary: Win8MBN::TestSetup::NDISSetup

The test verifies the NDIS CoInstaller values.

``` syntax
Attempt to NDIS Coinstaller values
   Attempt to read IfType
   PASS: Attempt to read IfType, succeeded
   Attempt to read MediaType
   PASS: Attempt to read MediaType, succeeded
   Attempt to read PhysicalMediaType
   PASS: Attempt to read PhysicalMediaType, succeeded
   Attempt to read EnableDhcp
      Attempt to read UpperRange
      PASS: Attempt to read UpperRange, succeeded
      Attempt to read LowerRange
      PASS: Attempt to read LowerRange, succeeded
   PASS: Attempt to read EnableDhcp, succeeded
PASS: Attempt to read NDIS Coinstaller values, succeeded
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify MediaType is NdisMediumWirelessWan
PASS: MediaType is NdisMediumWirelessWan
Verify PhysicalMediaType is NdisPhysicalMediumWirelessWan
PASS: PhysicalMediaType is NdisPhysicalMediumWirelessWan
Verify EnableDhcp is 0
PASS: EnableDhcp is 0
Verify UpperRange contains flpp4
PASS: UpperRange (flpp4, flpp6) contains flpp4
Verify LowerRange is ppip
PASS: LowerRange is ppip
```

### <span id="s15"></span><span id="S15"></span>Test Summary: Win8MBN::TestGenOids::PhysicalMediumQuery

The test queries physical medium and verifies the value.

``` syntax
Attempt OID_GEN_PHYSICAL_MEDIUM query
PASS: OID_GEN_PHYSICAL_MEDIUM succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
Verify indication length is 0x4
PASS: Indication length is 0x4
Verify OID_GEN_PHYSICAL_MEDIUM returned NdisPhysicalMediumWirelessWan
PASS: Ndis physical medium (NdisPhysicalMediumWirelessWan[0x8]) is valid
```

### <span id="s16"></span><span id="S16"></span>Test Summary: Win8MBN::TestGenOids::MediaSupportedQuery

The test queries media supported and verifies the value.

``` syntax
Attempt OID_GEN_MEDIA_SUPPORTED query
PASS: OID_GEN_MEDIA_SUPPORTED succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
Verify indication length is 0x4
PASS: Indication length is 0x4
Verify OID_GEN_MEDIA_SUPPORTED returned NdisMediumWirelessWan
PASS: Ndis medium (NdisMediumWirelessWan[0x9]) is valid
```

### <span id="s17"></span><span id="S17"></span>Test Summary: Win8MBN::TestGenOids::SupportedOidQueryWin8

The test queries supported oid and verifies the value.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt OID_GEN_SUPPORTED_LIST query
PASS: OID_GEN_SUPPORTED_LIST succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
Verify OID_GEN_PHYSICAL_MEDIUM is supported
PASS: OID_GEN_PHYSICAL_MEDIUM is supported
Verify OID_GEN_MEDIA_SUPPORTED is supported
PASS: OID_GEN_MEDIA_SUPPORTED is supported
Verify OID_GEN_SUPPORTED_LIST is supported
PASS: OID_GEN_SUPPORTED_LIST is supported
Verify OID_WWAN_DEVICE_CAPS is supported
PASS: OID_WWAN_DEVICE_CAPS is supported
Verify OID_WWAN_READY_INFO is supported
PASS: OID_WWAN_READY_INFO is supported
Verify OID_WWAN_REGISTER_STATE is supported
PASS: OID_WWAN_REGISTER_STATE is supported
Verify OID_WWAN_RADIO_STATE is supported
PASS: OID_WWAN_RADIO_STATE is supported
Verify OID_WWAN_PIN_LIST is supported
PASS: OID_WWAN_PIN_LIST is supported
Verify OID_WWAN_HOME_PROVIDER is supported
PASS: OID_WWAN_HOME_PROVIDER is supported
Verify OID_WWAN_PACKET_SERVICE is supported
PASS: OID_WWAN_PACKET_SERVICE is supported
Verify OID_WWAN_SIGNAL_STATE is supported
PASS: OID_WWAN_SIGNAL_STATE is supported
Verify OID_WWAN_CONNECT is supported
PASS: OID_WWAN_CONNECT is supported
Verify OID_WWAN_PROVISIONED_CONTEXTS is supported
PASS: OID_WWAN_PROVISIONED_CONTEXTS is supported
Verify OID_WWAN_SMS_CONFIGURATION is supported
PASS: OID_WWAN_SMS_CONFIGURATION is supported
Verify OID_WWAN_SMS_READ is supported
PASS: OID_WWAN_SMS_READ is supported
Verify OID_WWAN_SMS_SEND is supported
PASS: OID_WWAN_SMS_SEND is supported
Verify OID_WWAN_SMS_DELETE is supported
PASS: OID_WWAN_SMS_DELETE is supported
Verify OID_WWAN_PIN_EX is supported
PASS: OID_WWAN_PIN_EX is supported
```

### <span id="s18"></span><span id="S18"></span>Test Summary: Win8MBN::TestDriverCaps::Query

The test queries driver caps and verifies data members.

``` syntax
Attempt to query driver capabilities
   Attempt OID_WWAN_DRIVER_CAPS query
   PASS: OID_WWAN_DRIVER_CAPS succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
PASS: Attempt to query driver capabilities succeeded
Verify indication length is equal to or greater than 0x10
PASS: Indication length is valid
Verify ulMajorVersion is valid
PASS: ulMajorVersion (0x2) is valid
Verify ulMinorVersion is valid
PASS: ulMinorVersion (0x0) is valid
Verify ulDriverCaps is valid
PASS: ulDriverCaps (0x0) is valid
```

### <span id="s19"></span><span id="S19"></span>Test Summary: Win8MBN::TestGenOids::PhysicalMediumQuery

The test queries physical medium and verifies the value.

``` syntax
Attempt OID_GEN_PHYSICAL_MEDIUM query
PASS: OID_GEN_PHYSICAL_MEDIUM succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
Verify indication length is 0x4
PASS: Indication length is 0x4
Verify OID_GEN_PHYSICAL_MEDIUM returned NdisPhysicalMediumWirelessWan
PASS: Ndis physical medium (NdisPhysicalMediumWirelessWan[0x8]) is valid
```

### <span id="s20"></span><span id="S20"></span>Test Summary: Win8MBN::TestGenOids::MediaSupportedQuery

The test queries media supported and verifies the value.

``` syntax
Attempt OID_GEN_MEDIA_SUPPORTED query
PASS: OID_GEN_MEDIA_SUPPORTED succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
Verify indication length is 0x4
PASS: Indication length is 0x4
Verify OID_GEN_MEDIA_SUPPORTED returned NdisMediumWirelessWan
PASS: Ndis medium (NdisMediumWirelessWan[0x9]) is valid
```

### <span id="s21"></span><span id="S21"></span>Test Summary: Win8MBN::TestGenOids::SupportedOidQueryWin8

The test queries supported oid and verifies the value.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt OID_GEN_SUPPORTED_LIST query
PASS: OID_GEN_SUPPORTED_LIST succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
Verify OID_GEN_PHYSICAL_MEDIUM is supported
PASS: OID_GEN_PHYSICAL_MEDIUM is supported
Verify OID_GEN_MEDIA_SUPPORTED is supported
PASS: OID_GEN_MEDIA_SUPPORTED is supported
Verify OID_GEN_SUPPORTED_LIST is supported
PASS: OID_GEN_SUPPORTED_LIST is supported
Verify OID_WWAN_DEVICE_CAPS is supported
PASS: OID_WWAN_DEVICE_CAPS is supported
Verify OID_WWAN_READY_INFO is supported
PASS: OID_WWAN_READY_INFO is supported
Verify OID_WWAN_REGISTER_STATE is supported
PASS: OID_WWAN_REGISTER_STATE is supported
Verify OID_WWAN_RADIO_STATE is supported
PASS: OID_WWAN_RADIO_STATE is supported
Verify OID_WWAN_PIN_LIST is supported
PASS: OID_WWAN_PIN_LIST is supported
Verify OID_WWAN_HOME_PROVIDER is supported
PASS: OID_WWAN_HOME_PROVIDER is supported
Verify OID_WWAN_PACKET_SERVICE is supported
PASS: OID_WWAN_PACKET_SERVICE is supported
Verify OID_WWAN_SIGNAL_STATE is supported
PASS: OID_WWAN_SIGNAL_STATE is supported
Verify OID_WWAN_CONNECT is supported
PASS: OID_WWAN_CONNECT is supported
Verify OID_WWAN_PROVISIONED_CONTEXTS is supported
PASS: OID_WWAN_PROVISIONED_CONTEXTS is supported
Verify OID_WWAN_SMS_CONFIGURATION is supported
PASS: OID_WWAN_SMS_CONFIGURATION is supported
Verify OID_WWAN_SMS_READ is supported
PASS: OID_WWAN_SMS_READ is supported
Verify OID_WWAN_SMS_SEND is supported
PASS: OID_WWAN_SMS_SEND is supported
Verify OID_WWAN_SMS_DELETE is supported
PASS: OID_WWAN_SMS_DELETE is supported
Verify OID_WWAN_PIN_EX is supported
PASS: OID_WWAN_PIN_EX is supported
```

### <span id="s22"></span><span id="S22"></span>Test Summary: Win8MBN::TestHomeProvider::Query

The test queries home provider and verifies data members.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt to query home provider
   Attempt OID_WWAN_HOME_PROVIDER query
   PASS: OID_WWAN_HOME_PROVIDER succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query home provider succeeded
Verify indication length is equal to or greater than 0x4c
PASS: Indication length (0x4c) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify ProviderId is NULL terminated
PASS: ProviderId is NULL terminated
Verify ProviderId contains only digits
PASS: ProviderId (12301) contains only digits
Verify ProviderId is 5 digits in length for CDMA devices
PASS: ProviderId length (0x5) is valid
Verify ProviderState only uses WWAN_PROVIDER_STATE_HOME,WWAN_PROVIDER_STATE_FORBIDDEN,WWAN_PROVIDER_STATE_PREFERRED,WWAN_PROVIDER_STATE_VISIBLE, and\or WWAN_PROVIDER_STATE_REGISTERED
PASS: ProviderState (0x1) is valid
Verify ProviderName is NULL terminated
PASS: ProviderName is NULL terminated
Verify ProviderName is populated
PASS: ProviderName (MS MBN) is populated
Verify ProviderState has WWAN_PROVIDER_STATE_HOME set
PASS: ProviderState (0x1) has WWAN_PROVIDER_STATE_HOME set
```

### <span id="s23"></span><span id="S23"></span>Test Summary: Win8MBN::TestLoopBack::TestVerifyTrafficFixed

The test connects to loopback and send receives traffic.

``` syntax
Attempt to query interface device info data
PASS: Attempt to query interface device info data, succeeded
Determine if device is using MB Class Driver
PASS: Device is using class driver
Attempt to set connect context WwanActivationCommandActivate loopback (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandActivate loopback (null) (null), succeeded
Verify activation state of returned context state is WwanActivationStateActivated
PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
Attempt to add IPv4 Address
PASS: Attempt to add Loopback IPv4 Address, succeeded
Attempt to add Loopback IPv4 Route
   Attempt to get address from interface
   PASS: Attempt to get address (10.10.10.1) from interface, succeeded
PASS: Attempt to add Loopback IPv4 Route, succeeded
Start sending data
PASS: Start sending data, success
Wait 0n60000 ms for data to be sent
PASS: Wait for data to be sent, success
Verify data loss is less than 5%
PASS: Data loss (0.000000%) is less than 5%
Verify bandwidth is greater than 100 Mbps
PASS: Bandwidth (290.122667) is more than 100 Mbps
Attempt to delete IPv4 Address
PASS: Attempt to delete Loopback IPv4 Address, succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0xe0
PASS: Connection id of returned context state is 0xe0
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s24"></span><span id="S24"></span>Test Summary: Win8MBN::TestLoopBack::TestVerifyTrafficIncrement

The test connects to loopback and send receives traffic.

``` syntax
Attempt to query interface device info data
PASS: Attempt to query interface device info data, succeeded
Determine if device is using MB Class Driver
PASS: Device is using class driver
Attempt to set connect context WwanActivationCommandActivate loopback (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandActivate loopback (null) (null), succeeded
Verify activation state of returned context state is WwanActivationStateActivated
PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
Attempt to add IPv4 Address
PASS: Attempt to add Loopback IPv4 Address, succeeded
Attempt to add Loopback IPv4 Route
   Attempt to get address from interface
   PASS: Attempt to get address (10.10.10.1) from interface, succeeded
PASS: Attempt to add Loopback IPv4 Route, succeeded
Start sending data
PASS: Start sending data, success
Wait for data to be sent
PASS: Wait for data to be sent, success
Verify data loss is less than 5%
PASS: Data loss (0.612382%) is less than 5%
Attempt to delete IPv4 Address
PASS: Attempt to delete Loopback IPv4 Address, succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0xd0
PASS: Connection id of returned context state is 0xd0
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s25"></span><span id="S25"></span>Test Summary: Win8MBN::TestMultiCarrier::SetHomeProvider

The test sets the home provider.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify WWAN_CTRL_CAPS_MODEL_MULTI_CARRIER is supported
NA: Device does not support WWAN_CTRL_CAPS_MODEL_MULTI_CARRIER
```

### <span id="s26"></span><span id="S26"></span>Test Summary: Win8MBN::TestPacketService::AttachDetach

The test attaches and detaches the packet service.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt to packet service attach
   Attempt to auto register
      Attempt to query device capabilities
         Attempt OID_WWAN_DEVICE_CAPS query
         PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query device capabilities succeeded
      Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
         Attempt OID_WWAN_REGISTER_STATE set
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n50000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
   PASS: Attempt to auto register, succeeded
   Attempt to set packet service (WwanPacketServiceActionAttach)
      Attempt OID_WWAN_PACKET_SERVICE set
      PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
   Verify packet service state is WwanPacketServiceStateAttached
   PASS: Packet service state is WwanPacketServiceStateAttached
PASS: Attempt to packet service attach, succeeded
Verify indication length is equal to or greater than 0x18
PASS: Indication length (0x18) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify PacketServiceState is valid
PASS: PacketServiceState (WwanPacketServiceStateAttached[0x2]) is valid
Verify WwanDataClass are valid
PASS: WwanDataClass are valid for this device
Verify WwanDataClass are valid
PASS: WwanDataClass are valid for this device
Attempt to query packet service
   Attempt OID_WWAN_PACKET_SERVICE query
   PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query packet service succeeded
Verify indication length is equal to or greater than 0x18
PASS: Indication length (0x18) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify PacketServiceState is valid
PASS: PacketServiceState (WwanPacketServiceStateAttached[0x2]) is valid
Verify WwanDataClass are valid
PASS: WwanDataClass are valid for this device
Verify WwanDataClass are valid
PASS: WwanDataClass are valid for this device
Attempt to set packet service (WwanPacketServiceActionDetach)
   Attempt OID_WWAN_PACKET_SERVICE set
   PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set packet service (WwanPacketServiceActionDetach) succeeded
Verify indication length is equal to or greater than 0x18
PASS: Indication length (0x18) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify PacketServiceState is valid
PASS: PacketServiceState (WwanPacketServiceStateDetached[0x4]) is valid
Verify WwanDataClass are valid
PASS: WwanDataClass are valid for this device
Verify WwanDataClass are valid
PASS: WwanDataClass are valid for this device
Attempt to query packet service
   Attempt OID_WWAN_PACKET_SERVICE query
   PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query packet service succeeded
Verify indication length is equal to or greater than 0x18
PASS: Indication length (0x18) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify PacketServiceState is valid
PASS: PacketServiceState (WwanPacketServiceStateDetached[0x4]) is valid
Verify WwanDataClass are valid
PASS: WwanDataClass are valid for this device
Verify WwanDataClass are valid
PASS: WwanDataClass are valid for this device
```

### <span id="s27"></span><span id="S27"></span>Test Summary: Win8MBN::TestPin::PinListQueryRadioOn

The test attempts a pin list query with the radio on.

``` syntax
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
Attempt to query pin list
   Attempt OID_WWAN_PIN_LIST query
   PASS: OID_WWAN_PIN_LIST succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin list succeeded
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
```

### <span id="s28"></span><span id="S28"></span>Test Summary: Win8MBN::TestPin::PinListQueryRadioOff

The test attempts a pin list query with the radio off.

``` syntax
Attempt to set SwRadioState (WwanRadioOff[0x0])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOff[0x0]) succeeded
Attempt to query pin list
   Attempt OID_WWAN_PIN_LIST query
   PASS: OID_WWAN_PIN_LIST succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin list succeeded
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
```

### <span id="s29"></span><span id="S29"></span>Test Summary: Win8MBN::TestPin::NoPinSupport

The test verifes a device that does not support PIN1.

``` syntax
Attempt to query pin list
   Attempt OID_WWAN_PIN_LIST query
   PASS: OID_WWAN_PIN_LIST succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin list succeeded
Verify WwanPinTypePin1 is WwanPinModeNotSupported
NA: WwanPinTypePin1 is not WwanPinModeNotSupported
```

### <span id="s30"></span><span id="S30"></span>Test Summary: Win8MBN::TestPin::PinExSetEnableDisableWithValidPin

The test enables and disables PIN1 with a valid pin.

``` syntax
Attempt to query pin list
   Attempt OID_WWAN_PIN_LIST query
   PASS: OID_WWAN_PIN_LIST succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin list succeeded
Verify WwanPinTypePin1 is not WwanPinModeNotSupported
PASS: WwanPinTypePin1 is not WwanPinModeNotSupported
Verify PIN1 parameter was provided
PASS: PIN1 (1111) parameter was provided
Verify WwanPinTypePin1 is WwanPinModeDisabled
PASS: WwanPinTypePin1 is WwanPinModeDisabled
Attempt to query pin ex
   Attempt OID_WWAN_PIN_EX query
   PASS: OID_WWAN_PIN_EX succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin ex succeeded
Attempt to set pin ex (WwanPinTypePin1 WwanPinOperationEnable Pin:1111 NewPin:(null))
   Attempt OID_WWAN_PIN_EX set
   PASS: OID_WWAN_PIN_EX succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set pin ex (WwanPinTypePin1 WwanPinOperationEnable Pin:1111 NewPin:(null)) succeeded
Attempt to query pin list
   Attempt OID_WWAN_PIN_LIST query
   PASS: OID_WWAN_PIN_LIST succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin list succeeded
Verify NDIS_WWAN_PIN_LIST has WwanPinTypePin1 as WwanPinModeEnabled
PASS: NDIS_WWAN_PIN_LIST has WwanPinTypePin1 as WwanPinModeEnabled
Attempt to set pin ex (WwanPinTypePin1 WwanPinOperationDisable Pin:1111 NewPin:(null))
   Attempt OID_WWAN_PIN_EX set
   PASS: OID_WWAN_PIN_EX succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set pin ex (WwanPinTypePin1 WwanPinOperationDisable Pin:1111 NewPin:(null)) succeeded
Attempt to query pin list
   Attempt OID_WWAN_PIN_LIST query
   PASS: OID_WWAN_PIN_LIST succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin list succeeded
Verify NDIS_WWAN_PIN_LIST has WwanPinTypePin1 as WwanPinModeDisabled
PASS: NDIS_WWAN_PIN_LIST has WwanPinTypePin1 as WwanPinModeDisabled
```

### <span id="s31"></span><span id="S31"></span>Test Summary: Win8MBN::TestPin::PinExSetDisableIncorrectPinWithValidLength

The test attempts to enable PIN1 with incorrect pin with valid length.

``` syntax
Attempt to query pin list
   Attempt OID_WWAN_PIN_LIST query
   PASS: OID_WWAN_PIN_LIST succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin list succeeded
Verify WwanPinTypePin1 is not WwanPinModeNotSupported
PASS: WwanPinTypePin1 is not WwanPinModeNotSupported
Verify PIN1 parameter was provided
PASS: PIN1 (1111) parameter was provided
Verify WwanPinTypePin1 is WwanPinModeDisabled
PASS: WwanPinTypePin1 is WwanPinModeDisabled
Attempt to query pin ex
   Attempt OID_WWAN_PIN_EX query
   PASS: OID_WWAN_PIN_EX succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin ex succeeded
Attempt to set pin ex (WwanPinTypePin1 WwanPinOperationEnable Pin:1111 NewPin:(null))
   Attempt OID_WWAN_PIN_EX set
   PASS: OID_WWAN_PIN_EX succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set pin ex (WwanPinTypePin1 WwanPinOperationEnable Pin:1111 NewPin:(null)) succeeded
Attempt to set WwanPinTypePin1 WwanPinOperationDisable with incorrect pin [pin:4321]
   Attempt OID_WWAN_PIN_EX set
   PASS: OID_WWAN_PIN_EX succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
PASS: WWAN_STATUS == WWAN_STATUS_FAILURE
Attempt to set pin ex (WwanPinTypePin1 WwanPinOperationDisable Pin:1111 NewPin:(null))
   Attempt OID_WWAN_PIN_EX set
   PASS: OID_WWAN_PIN_EX succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set pin ex (WwanPinTypePin1 WwanPinOperationDisable Pin:1111 NewPin:(null)) succeeded
```

### <span id="s32"></span><span id="S32"></span>Test Summary: Win8MBN::TestPin::PukEnableDisableThroughIncorrectPinExDisable

The test enables PUK1 by entering incorrect PIN1 multiple times and then disables PUK1.

``` syntax
Attempt to query pin list
   Attempt OID_WWAN_PIN_LIST query
   PASS: OID_WWAN_PIN_LIST succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query pin list succeeded
Verify WwanPinTypePin1 is not WwanPinModeNotSupported
PASS: WwanPinTypePin1 is not WwanPinModeNotSupported
Verify PIN1 parameter was provided
PASS: PIN1 (1111) parameter was provided
Verify PUK1 parameter was provided
NA: PUK1 parameter was not provided
```

### <span id="s33"></span><span id="S33"></span>Test Summary: Win8MBN::TestPowerStates::SleepAndWake

The test connects, puts the machine into sleep mode, wakes the machine, and connects.

``` syntax
Verify machine processor is supported
PASS: Machine processor (0x0) is supported
Attempt to connect using provided context
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n31 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate 
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n2667 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate , succeeded
      Verify connection id of returned context state is 0xdb
      PASS: Connection id of returned context state is 0xdb
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provided context succeeded
Attempt to put computer into Sleep mode for 0x3c seconds
PASS: Attempt to put computer into Sleep mode for 0x3c seconds, succeeded)
Wait 0xea60 ms for device to enter WwanReadyStateInitialized
PASS: Wait for device to enter WwanReadyStateInitialized, succeeded
Performance Check:Verify WwanReadyStateInitialized occured under 0n60000 ms
PASS: WwanReadyStateInitialized occured in 0n5662 ms
Attempt to connect using provided context
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n31 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n5788 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n31 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate 
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n3464 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate , succeeded
      Verify connection id of returned context state is 0x5b
      PASS: Connection id of returned context state is 0x5b
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provided context succeeded
Verify TCP/IP shows interface as connected in 0x3a98 ms
PASS: TCP/IP shows interface as connected in 0x24bf ms
Attempt to remove non wwan default routes
PASS: Attempt to remove non wwan default routes, succeeded
Attempt to download web doc
PASS: Attempt to download web doc, succeeded
Attempt to restore non wwan default routes
PASS: Attempt to restore non wwan default routes, succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n281 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0x5b
PASS: Connection id of returned context state is 0x5b
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s34"></span><span id="S34"></span>Test Summary: Win8MBN::TestPowerStates::HibernateAndWake

The test connects, puts the machine into hiberantion mode, wakes the machine, and connects.

``` syntax
Verify machine processor is supported
PASS: Machine processor (0x0) is supported
Attempt to connect using provided context
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n31 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate 
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n2667 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate , succeeded
      Verify connection id of returned context state is 0xfa
      PASS: Connection id of returned context state is 0xfa
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provided context succeeded
Attempt to put computer into Hibernate mode for 0x3c seconds
PASS: Attempt to put computer into Hibernate mode for 0x3c seconds, succeeded)
Wait 0xea60 ms for device to enter WwanReadyStateInitialized
PASS: Wait for device to enter WwanReadyStateInitialized, succeeded
Performance Check:Verify WwanReadyStateInitialized occured under 0n60000 ms
PASS: WwanReadyStateInitialized occured in 0n140 ms
Attempt to connect using provided context
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n16 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n358 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n47 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate 
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n3588 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate , succeeded
      Verify connection id of returned context state is 0x4e
      PASS: Connection id of returned context state is 0x4e
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provided context succeeded
Verify TCP/IP shows interface as connected in 0x3a98 ms
PASS: TCP/IP did not show interface as connected in 0x3a98 ms
Attempt to remove non wwan default routes
PASS: Attempt to remove non wwan default routes, succeeded
Attempt to download web doc
PASS: Attempt to download web doc, succeeded
Attempt to restore non wwan default routes
PASS: Attempt to restore non wwan default routes, succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n249 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0x4e
PASS: Connection id of returned context state is 0x4e
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s35"></span><span id="S35"></span>Test Summary: Win8MBN::TestPreferredProvider::Query

The test queries preferred providers and verifies data members.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify the device is GSM
NA: Device is not GSM
```

### <span id="s36"></span><span id="S36"></span>Test Summary: Win8MBN::TestPreferredProvider::AddRemovePreferredProvider

The test adds and removes a preferred provider.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify the device is GSM
NA: Device is not GSM
```

### <span id="s37"></span><span id="S37"></span>Test Summary: Win8MBN::TestPreferredProvider::AddRemoveForbiddenProvider

The test adds and removes a forbidden provider.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify the device is GSM
NA: Device is not GSM
```

### <span id="s38"></span><span id="S38"></span>Test Summary: Win8MBN::TestPreferredProvider::AddRemovePreferredForbiddenProvider

The test adds and removes both forbidden and forbidden providers.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify the device is GSM
NA: Device is not GSM
```

### <span id="s39"></span><span id="S39"></span>Test Summary: Win8MBN::TestRadioStateHw::TurnHwRadioOffOnWhenRegistered

The test turns the hardware radio off and on when registered.

``` syntax
Verify device has hardware radio switch
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
PASS: Device has hardware radio switch
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
Attempt to turn hardware radio off
   Verify unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication was received
   Performance Check:Verify unsolicited indication was received under 0n60000 ms
   PASS: Unsolicited indication was received in 0n35708 ms
PASS: Attempt to turn hardware radio off, succeeded
Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication for 0x7530 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication
Performance Check:Verify unsolicited indication was received under 0n30000 ms
PASS: Unsolicited indication was received in 0n0 ms
Attempt to turn hardware radio on
   Verify unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication was received
   Performance Check:Verify unsolicited indication was received under 0n60000 ms
   PASS: Unsolicited indication was received in 0n3416 ms
PASS: Attempt to turn hardware radio on, succeeded
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
```

### <span id="s40"></span><span id="S40"></span>Test Summary: Win8MBN::TestRadioStateHw::TurnHwRadioOffOnWhenPacketServiceAttached

The test turns the hardware radio off and on when packet service attached.

``` syntax
Verify device has hardware radio switch
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
PASS: Device has hardware radio switch
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
Attempt to packet service attach
   Attempt to auto register
      Attempt to query device capabilities
         Attempt OID_WWAN_DEVICE_CAPS query
         PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query device capabilities succeeded
      Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
         Attempt OID_WWAN_REGISTER_STATE set
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n50000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
   PASS: Attempt to auto register, succeeded
   Attempt to set packet service (WwanPacketServiceActionAttach)
      Attempt OID_WWAN_PACKET_SERVICE set
      PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
   Verify packet service state is WwanPacketServiceStateAttached
   PASS: Packet service state is WwanPacketServiceStateAttached
PASS: Attempt to packet service attach, succeeded
Attempt to turn hardware radio off
   Verify unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication was received
   Performance Check:Verify unsolicited indication was received under 0n60000 ms
   PASS: Unsolicited indication was received in 0n2636 ms
PASS: Attempt to turn hardware radio off, succeeded
Wait for unsolicited NDIS_STATUS_WWAN_PACKET_SERVICE (WwanPacketServiceStateDetached) indication for 0x3a98 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_PACKET_SERVICE (WwanPacketServiceStateDetached) indication
Performance Check:Verify unsolicited indication was received under 0n15000 ms
PASS: Unsolicited indication was received in 0n0 ms
Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication for 0x7530 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication
Performance Check:Verify unsolicited indication was received under 0n30000 ms
PASS: Unsolicited indication was received in 0n0 ms
Attempt to turn hardware radio on
   Verify unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication was received
   Performance Check:Verify unsolicited indication was received under 0n60000 ms
   PASS: Unsolicited indication was received in 0n2262 ms
PASS: Attempt to turn hardware radio on, succeeded
Attempt to packet service attach
   Attempt to auto register
      Attempt to query device capabilities
         Attempt OID_WWAN_DEVICE_CAPS query
         PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query device capabilities succeeded
      Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
         Attempt OID_WWAN_REGISTER_STATE set
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n50000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateHome | WwanRegisterStatePartner | WwanRegisterStateRoaming) indication for 0xc350 seconds
      PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateHome | WwanRegisterStatePartner | WwanRegisterStateRoaming) indication
      Performance Check:Verify unsolicited indication was received under 0n50000 ms
      PASS: Unsolicited indication was received in 0n514 ms
   PASS: Attempt to auto register, succeeded
   Attempt to set packet service (WwanPacketServiceActionAttach)
      Attempt OID_WWAN_PACKET_SERVICE set
      PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
   Verify packet service state is WwanPacketServiceStateAttached
   PASS: Packet service state is WwanPacketServiceStateAttached
PASS: Attempt to packet service attach, succeeded
```

### <span id="s41"></span><span id="S41"></span>Test Summary: Win8MBN::TestRadioStateHw::TurnHwRadioOffOnWhenConnected

The test turns the hardware radio off and on when connected.

``` syntax
Verify device has hardware radio switch
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
PASS: Device has hardware radio switch
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n15 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n16 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n63 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0xd8
      PASS: Connection id of returned context state is 0xd8
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to turn hardware radio off
   Verify unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication was received
   Performance Check:Verify unsolicited indication was received under 0n60000 ms
   PASS: Unsolicited indication was received in 0n2528 ms
PASS: Attempt to turn hardware radio off, succeeded
Wait for unsolicited NDIS_STATUS_WWAN_CONTEXT_STATE (WwanActivationStateDeactivated) indication for 0x3a98 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_CONTEXT_STATE (WwanActivationStateDeactivated) indication
Performance Check:Verify unsolicited indication was received under 0n15000 ms
PASS: Unsolicited indication was received in 0n0 ms
Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication for 0x7530 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication
Performance Check:Verify unsolicited indication was received under 0n30000 ms
PASS: Unsolicited indication was received in 0n0 ms
Attempt to turn hardware radio on
   Verify unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_RADIO_STATE indication was received
   Performance Check:Verify unsolicited indication was received under 0n60000 ms
   PASS: Unsolicited indication was received in 0n1654 ms
PASS: Attempt to turn hardware radio on, succeeded
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n15 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
         Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateHome | WwanRegisterStatePartner | WwanRegisterStateRoaming) indication for 0xc350 seconds
         PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateHome | WwanRegisterStatePartner | WwanRegisterStateRoaming) indication
         Performance Check:Verify unsolicited indication was received under 0n50000 ms
         PASS: Unsolicited indication was received in 0n31 ms
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n62 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0x52
      PASS: Connection id of returned context state is 0x52
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0x52
PASS: Connection id of returned context state is 0x52
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s42"></span><span id="S42"></span>Test Summary: Win8MBN::TestRadioStateSw::TurnSwRadioOffOnWhenRegistered

The test turns the software radio off and on when registered.

``` syntax
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
Attempt to set SwRadioState (WwanRadioOff[0x0])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOff[0x0]) succeeded
Verify indication shows correct state
PASS: SwRadioState is correct WwanRadioOff[0x0]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOff[0x0]) is valid
Attempt to query radio state
   Attempt OID_WWAN_RADIO_STATE query
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query radio state succeeded
Verify SwRadioState is WwanRadioOff[0x0]
PASS: SwRadioState is WwanRadioOff[0x0]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOff[0x0]) is valid
Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication for 0x7530 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication
Performance Check:Verify unsolicited indication was received under 0n30000 ms
PASS: Unsolicited indication was received in 0n16 ms
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
Verify indication shows correct state
PASS: SwRadioState is correct WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
Attempt to query radio state
   Attempt OID_WWAN_RADIO_STATE query
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query radio state succeeded
Verify SwRadioState is WwanRadioOn[0x1]
PASS: SwRadioState is WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
Verify indication shows correct state
PASS: SwRadioState is correct WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
Attempt to query radio state
   Attempt OID_WWAN_RADIO_STATE query
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query radio state succeeded
Verify SwRadioState is WwanRadioOn[0x1]
PASS: SwRadioState is WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
```

### <span id="s43"></span><span id="S43"></span>Test Summary: Win8MBN::TestRadioStateSw::TurnSwRadioOffOnWhenPacketServiceAttached

The test turns the software radio off and on when packet service is attached.

``` syntax
Attempt to packet service attach
   Attempt to auto register
      Attempt to query device capabilities
         Attempt OID_WWAN_DEVICE_CAPS query
         PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query device capabilities succeeded
      Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
         Attempt OID_WWAN_REGISTER_STATE set
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n50000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
   PASS: Attempt to auto register, succeeded
   Attempt to set packet service (WwanPacketServiceActionAttach)
      Attempt OID_WWAN_PACKET_SERVICE set
      PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
   Verify packet service state is WwanPacketServiceStateAttached
   PASS: Packet service state is WwanPacketServiceStateAttached
PASS: Attempt to packet service attach, succeeded
Attempt to set SwRadioState (WwanRadioOff[0x0])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOff[0x0]) succeeded
Verify indication shows correct state
PASS: SwRadioState is correct WwanRadioOff[0x0]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOff[0x0]) is valid
Attempt to query radio state
   Attempt OID_WWAN_RADIO_STATE query
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query radio state succeeded
Verify SwRadioState is WwanRadioOff[0x0]
PASS: SwRadioState is WwanRadioOff[0x0]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOff[0x0]) is valid
Wait for unsolicited NDIS_STATUS_WWAN_PACKET_SERVICE (WwanPacketServiceStateDetached) indication for 0x3a98 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_PACKET_SERVICE (WwanPacketServiceStateDetached) indication
Performance Check:Verify unsolicited indication was received under 0n15000 ms
PASS: Unsolicited indication was received in 0n16 ms
Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication for 0x7530 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication
Performance Check:Verify unsolicited indication was received under 0n30000 ms
PASS: Unsolicited indication was received in 0n0 ms
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
Verify indication shows correct state
PASS: SwRadioState is correct WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
Attempt to query radio state
   Attempt OID_WWAN_RADIO_STATE query
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query radio state succeeded
Verify SwRadioState is WwanRadioOn[0x1]
PASS: SwRadioState is WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
Attempt to packet service attach
   Attempt to auto register
      Attempt to query device capabilities
         Attempt OID_WWAN_DEVICE_CAPS query
         PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query device capabilities succeeded
      Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
         Attempt OID_WWAN_REGISTER_STATE set
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n50000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
   PASS: Attempt to auto register, succeeded
   Attempt to set packet service (WwanPacketServiceActionAttach)
      Attempt OID_WWAN_PACKET_SERVICE set
      PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
   Verify packet service state is WwanPacketServiceStateAttached
   PASS: Packet service state is WwanPacketServiceStateAttached
PASS: Attempt to packet service attach, succeeded
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
Verify indication shows correct state
PASS: SwRadioState is correct WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
Attempt to query radio state
   Attempt OID_WWAN_RADIO_STATE query
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query radio state succeeded
Verify SwRadioState is WwanRadioOn[0x1]
PASS: SwRadioState is WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
```

### <span id="s44"></span><span id="S44"></span>Test Summary: Win8MBN::TestRadioStateSw::TurnSwRadioOffOnWhenConnected

The test turns the software radio off and on when connected.

``` syntax
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n93 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0xc
      PASS: Connection id of returned context state is 0xc
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to set SwRadioState (WwanRadioOff[0x0])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n47 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOff[0x0]) succeeded
Verify indication shows correct state
PASS: SwRadioState is correct WwanRadioOff[0x0]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOff[0x0]) is valid
Attempt to query radio state
   Attempt OID_WWAN_RADIO_STATE query
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query radio state succeeded
Verify SwRadioState is WwanRadioOff[0x0]
PASS: SwRadioState is WwanRadioOff[0x0]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOff[0x0]) is valid
Wait for unsolicited NDIS_STATUS_WWAN_CONTEXT_STATE (WwanActivationStateDeactivated) indication for 0x3a98 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_CONTEXT_STATE (WwanActivationStateDeactivated) indication
Performance Check:Verify unsolicited indication was received under 0n15000 ms
PASS: Unsolicited indication was received in 0n0 ms
Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication for 0x7530 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication
Performance Check:Verify unsolicited indication was received under 0n30000 ms
PASS: Unsolicited indication was received in 0n16 ms
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
Verify indication shows correct state
PASS: SwRadioState is correct WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
Attempt to query radio state
   Attempt OID_WWAN_RADIO_STATE query
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query radio state succeeded
Verify SwRadioState is WwanRadioOn[0x1]
PASS: SwRadioState is WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n16 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n15 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n78 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0xbc
      PASS: Connection id of returned context state is 0xbc
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0xbc
PASS: Connection id of returned context state is 0xbc
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
Verify indication shows correct state
PASS: SwRadioState is correct WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
Attempt to query radio state
   Attempt OID_WWAN_RADIO_STATE query
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query radio state succeeded
Verify SwRadioState is WwanRadioOn[0x1]
PASS: SwRadioState is WwanRadioOn[0x1]
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify HwRadioState
PASS: HwRadioState (WwanRadioOn[0x1]) is valid
Verify SwRadioState
PASS: SwRadioState (WwanRadioOn[0x1]) is valid
```

### <span id="s45"></span><span id="S45"></span>Test Summary: Win8MBN::TestReadyInfo::Query

The test queries ready info and verifies data members.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt to query ready info
   Attempt OID_WWAN_READY_INFO query
   PASS: OID_WWAN_READY_INFO succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
PASS: Attempt to query ready info succeeded
Verify indication length is equal to or greater than 0x80
PASS: Indication length is 0x80
Verify ReadyState is valid
PASS: ReadyState (0x1) is valid
Verify EmergencyMode is valid
PASS: EmergencyMode (0x0) is valid
Verify SubscriberId is NULL terminated
PASS: SubscriberId is NULL terminated
Verify SubscriberId contains only digits
PASS: SubscriberId (1234567890) contains only digits
Verify SimIccId is NULL terminated
PASS: SimIccId is NULL terminated
Verify SimIccId contains only digits
PASS: SimIccId () contains only digits
Verify SubscriberId is 10 digits in length for CDMA devices
PASS: SubscriberId length (0xa) is valid
Verify CdmaShortMsgSize is between WWAN_CDMA_SHORT_MSG_SIZE_UNKNOWN and WWAN_CDMA_SHORT_MSG_SIZE_MAX for CDMA devices
PASS: CdmaShortMsgSize (0xa0) is valid
Verify ElementType is WwanStructTN
PASS: ElementType is valid
```

### <span id="s46"></span><span id="S46"></span>Test Summary: Win8MBN::TestRegisterState::Query

The test queries register state and verifies data members.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt to query Register State
   Attempt OID_WWAN_REGISTER_STATE query
   PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query register state succeeded
Verify indication length is equal to or greater than 0xd4
PASS: Indication length (0xd4) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify RegisterState is valid
PASS: RegisterState (WwanRegisterStateHome[0x0]) is valid
Verify RegisterMode is valid
PASS: RegisterMode (WwanRegisterStateHome[0x0]) is valid
Verify ProviderId is NULL terminated
PASS: ProviderId is NULL terminated
Verify ProviderId contains only digits
PASS: ProviderId (12301) contains only digits
Verify ProviderId is 5 digits in length for CDMA devices
PASS: ProviderId length (0x5) is valid
Verify ProviderName is NULL terminated
PASS: ProviderName is NULL terminated
Verify ProviderName is populated
PASS: ProviderName (12301) is populated
Verify WwanRegFlags is valid
PASS: WwanRegFlags (0x0) is valid
```

### <span id="s47"></span><span id="S47"></span>Test Summary: Win8MBN::TestRegisterState::RegisterAutomatic

The test attempts to register in automatic mode.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt to query home provider
   Attempt OID_WWAN_HOME_PROVIDER query
   PASS: OID_WWAN_HOME_PROVIDER succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query home provider succeeded
Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
   Attempt OID_WWAN_REGISTER_STATE set
   PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n50000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
Verify register mode is WwanRegisterModeAutomatic
PASS: Register mode is WwanRegisterModeAutomatic
Verify register state is WwanRegisterStateHome, WwanRegisterStateRoaming, or WwanRegisterStatePartner
PASS: Register state is WwanRegisterStateHome
```

### <span id="s48"></span><span id="S48"></span>Test Summary: Win8MBN::TestRegisterState::RegisterManualToHomeProvider

The test attempts to register to the home provider in manual mode.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify device supports manual registration
NA: Device does not support manual registration
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
```

### <span id="s49"></span><span id="S49"></span>Test Summary: Win8MBN::TestRemoval::RemovalWhenRegistered

The test registers and prompts the user to remove the device.

``` syntax
Verify device is removable
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
PASS: Device is removable
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
Attempt to remove the device
PASS: Attempt to remove the device, succeeded
Attempt to add the device
   Wait 0xea60 ms for device to enter WwanReadyStateInitialized
   PASS: Wait for device to enter WwanReadyStateInitialized, succeeded
   Performance Check:Verify WwanReadyStateInitialized occured under 0n60000 ms
   PASS: WwanReadyStateInitialized occured in 0n16 ms
PASS: Attempt to add the device, succeeded
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
   Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateHome | WwanRegisterStatePartner | WwanRegisterStateRoaming) indication for 0xc350 seconds
   PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateHome | WwanRegisterStatePartner | WwanRegisterStateRoaming) indication
   Performance Check:Verify unsolicited indication was received under 0n50000 ms
   PASS: Unsolicited indication was received in 0n93 ms
PASS: Attempt to auto register, succeeded
```

### <span id="s50"></span><span id="S50"></span>Test Summary: Win8MBN::TestRemoval::RemovalWhenPacketSvcAttached

The test attaches the packet service and prompts the user to remove the device.

``` syntax
Verify device is removable
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
PASS: Device is removable
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
Attempt to packet service attach
   Attempt to auto register
      Attempt to query device capabilities
         Attempt OID_WWAN_DEVICE_CAPS query
         PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query device capabilities succeeded
      Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
         Attempt OID_WWAN_REGISTER_STATE set
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n50000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
   PASS: Attempt to auto register, succeeded
   Attempt to set packet service (WwanPacketServiceActionAttach)
      Attempt OID_WWAN_PACKET_SERVICE set
      PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
   Verify packet service state is WwanPacketServiceStateAttached
   PASS: Packet service state is WwanPacketServiceStateAttached
PASS: Attempt to packet service attach, succeeded
Attempt to remove the device
PASS: Attempt to remove the device, succeeded
Attempt to add the device
   Wait 0xea60 ms for device to enter WwanReadyStateInitialized
   PASS: Wait for device to enter WwanReadyStateInitialized, succeeded
   Performance Check:Verify WwanReadyStateInitialized occured under 0n60000 ms
   PASS: WwanReadyStateInitialized occured in 0n0 ms
PASS: Attempt to add the device, succeeded
Attempt to packet service attach
   Attempt to auto register
      Attempt to query device capabilities
         Attempt OID_WWAN_DEVICE_CAPS query
         PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query device capabilities succeeded
      Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
         Attempt OID_WWAN_REGISTER_STATE set
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n50000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
   PASS: Attempt to auto register, succeeded
   Attempt to set packet service (WwanPacketServiceActionAttach)
      Attempt OID_WWAN_PACKET_SERVICE set
      PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
   Verify packet service state is WwanPacketServiceStateAttached
   PASS: Packet service state is WwanPacketServiceStateAttached
PASS: Attempt to packet service attach, succeeded
```

### <span id="s51"></span><span id="S51"></span>Test Summary: Win8MBN::TestRemoval::RemovalWhenConnected

The test connects and prompts the user to remove the device.

``` syntax
Verify device is removable
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
PASS: Device is removable
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n15 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n141 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0x2f
      PASS: Connection id of returned context state is 0x2f
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to remove the device
PASS: Attempt to remove the device, succeeded
Attempt to add the device
   Wait 0xea60 ms for device to enter WwanReadyStateInitialized
   PASS: Wait for device to enter WwanReadyStateInitialized, succeeded
   Performance Check:Verify WwanReadyStateInitialized occured under 0n60000 ms
   PASS: WwanReadyStateInitialized occured in 0n15 ms
PASS: Attempt to add the device, succeeded
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n16 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n94 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0xb6
      PASS: Connection id of returned context state is 0xb6
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n32 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0xb6
PASS: Connection id of returned context state is 0xb6
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s52"></span><span id="S52"></span>Test Summary: Win8MBN::TestSelectiveSuspend::SelectiveSuspendConnected

The test block outbound IP traffic to verify the device enters selective suspend state. The test will then unblock outbound traffic and verify the device comes out of selective suspend state.

``` syntax
Attempt to connect using provided context
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n32 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x1f) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n15 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate 
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n2668 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate , succeeded
      Verify connection id of returned context state is 0xb
      PASS: Connection id of returned context state is 0xb
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provided context succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to open engine handle
PASS: Attempt to open engine handle, succeeded
Attempt to add IPv4 filter
PASS: Attempt to add IPv4 filter, succeeded
Attempt to add IPv6 filter
PASS: Attempt to add IPv6 filter, succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n1014 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0xb
PASS: Connection id of returned context state is 0xb
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
Verify NDIS Events
PASS: Number of NDIS Events (0x10c7), succeeded
Verify NDIS Selective Suspend Events
PASS: Verify NDIS Selective Suspend Events, succeeded
```

### <span id="s53"></span><span id="S53"></span>Test Summary: Win8MBN::TestSetup::NDISSetup

The test verifies the NDIS CoInstaller values.

``` syntax
Attempt to NDIS Coinstaller values
   Attempt to read IfType
   PASS: Attempt to read IfType, succeeded
   Attempt to read MediaType
   PASS: Attempt to read MediaType, succeeded
   Attempt to read PhysicalMediaType
   PASS: Attempt to read PhysicalMediaType, succeeded
   Attempt to read EnableDhcp
      Attempt to read UpperRange
      PASS: Attempt to read UpperRange, succeeded
      Attempt to read LowerRange
      PASS: Attempt to read LowerRange, succeeded
   PASS: Attempt to read EnableDhcp, succeeded
PASS: Attempt to read NDIS Coinstaller values, succeeded
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Verify MediaType is NdisMediumWirelessWan
PASS: MediaType is NdisMediumWirelessWan
Verify PhysicalMediaType is NdisPhysicalMediumWirelessWan
PASS: PhysicalMediaType is NdisPhysicalMediumWirelessWan
Verify EnableDhcp is 0
PASS: EnableDhcp is 0
Verify UpperRange contains flpp4
PASS: UpperRange (flpp4, flpp6) contains flpp4
Verify LowerRange is ppip
PASS: LowerRange is ppip
```

### <span id="s54"></span><span id="S54"></span>Test Summary: Win8MBN::TestSignalState::Query

The test queries signal state and verifies values.

``` syntax
Attempt to query signal state
   Attempt OID_WWAN_SIGNAL_STATE query
   PASS: OID_WWAN_SIGNAL_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query signal state succeeded
Verify indication length is equal to or greater than 0x18
PASS: Indication length (0x18) is valid
Verify RSSI is between 0 and 31 or WWAN_RSSI_UNKNOWN
PASS: RSSI (0x1e) is between 0 and 31 or WWAN_RSSI_UNKNOWN
Verify error rate is between 0 and 7 or WWAN_ERROR_RATE_UNKNOWN
PASS: Error rate (0x0) is between 0 and 7 or WWAN_ERROR_RATE_UNKNOWN
Verify RSSI interval is more than 5 seconds
PASS: RSSI interval (0x1e) is more than 5 seconds
```

### <span id="s55"></span><span id="S55"></span>Test Summary: Win8MBN::TestSms::SmsConfigQuery

The test queries sms config and verifies data members.

``` syntax
Attempt to initialize test
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Verify phone number of device was provided as a parameter or can be obtained from ready info
      Attempt to query ready info
         Attempt OID_WWAN_READY_INFO query
         PASS: OID_WWAN_READY_INFO succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
      PASS: Attempt to query ready info succeeded
   PASS: Phone number of device (4255551212) was obtained
   Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
      Attempt OID_WWAN_SMS_DELETE set
      PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS delete succeeded
PASS: Attempt to initialize test, succeeded
Attempt to query SMS configuration
   Attempt OID_WWAN_SMS_CONFIGURATION query
   PASS: OID_WWAN_SMS_CONFIGURATION succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query SMS configuration succeeded
Verify indication length is equal to or greater than 0x20
PASS: Indication length (0x20) is valid
Verify Status is valid
PASS: Status (WWAN_STATUS_SUCCESS[0x0]) is valid
Verify SmsFormat is WwanSmsFormatCdma or WwanSmsFormatPdu
PASS: SmsFormat is WwanSmsFormatCdma[0x4]
```

### <span id="s56"></span><span id="S56"></span>Test Summary: Win8MBN::TestSms::SmsStatusQuery

The test queries sms status and verifies data members.

``` syntax
Attempt to initialize test
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Verify phone number of device was provided as a parameter or can be obtained from ready info
      Attempt to query ready info
         Attempt OID_WWAN_READY_INFO query
         PASS: OID_WWAN_READY_INFO succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
      PASS: Attempt to query ready info succeeded
   PASS: Phone number of device (4255551212) was obtained
   Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
      Attempt OID_WWAN_SMS_DELETE set
      PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS delete succeeded
PASS: Attempt to initialize test, succeeded
Attempt to query SMS status
   Attempt OID_WWAN_SMS_STATUS query
   PASS: OID_WWAN_SMS_STATUS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query SMS status succeeded
Verify indication length is equal to or greater than 0x10
PASS: Indication length (0x10) is valid
```

### <span id="s57"></span><span id="S57"></span>Test Summary: Win8MBN::TestSms::SmsSendMessageToSelf

The test sends an SMS message to itself and verifies it receives the message.

``` syntax
Attempt to initialize test
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Verify phone number of device was provided as a parameter or can be obtained from ready info
      Attempt to query ready info
         Attempt OID_WWAN_READY_INFO query
         PASS: OID_WWAN_READY_INFO succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
      PASS: Attempt to query ready info succeeded
   PASS: Phone number of device (4255551212) was obtained
   Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
      Attempt OID_WWAN_SMS_DELETE set
      PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS delete succeeded
PASS: Attempt to initialize test, succeeded
Attempt to send message to self
   Attempt to set SMS send
      Attempt OID_WWAN_SMS_SEND set
      PASS: OID_WWAN_SMS_SEND succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n47 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS send succeeded
   Verify unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication was received
   Performance Check:Verify unsolicited indication was received under 0n300000 ms
   PASS: Unsolicited indication was received in 0n0 ms
PASS: Attempt to send message to self, succeeded
```

### <span id="s58"></span><span id="S58"></span>Test Summary: Win8MBN::TestSms::SmsDeleteAllMessages

The test deletes all messages.

``` syntax
Attempt to initialize test
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Verify phone number of device was provided as a parameter or can be obtained from ready info
      Attempt to query ready info
         Attempt OID_WWAN_READY_INFO query
         PASS: OID_WWAN_READY_INFO succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
      PASS: Attempt to query ready info succeeded
   PASS: Phone number of device (4255551212) was obtained
   Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
      Attempt OID_WWAN_SMS_DELETE set
      PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS delete succeeded
PASS: Attempt to initialize test, succeeded
Attempt to send message to self
   Attempt to set SMS send
      Attempt OID_WWAN_SMS_SEND set
      PASS: OID_WWAN_SMS_SEND succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS send succeeded
   Verify unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication was received
   Performance Check:Verify unsolicited indication was received under 0n300000 ms
   PASS: Unsolicited indication was received in 0n16 ms
PASS: Attempt to send message to self, succeeded
Attempt to send message to self
   Attempt to set SMS send
      Attempt OID_WWAN_SMS_SEND set
      PASS: OID_WWAN_SMS_SEND succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS send succeeded
   Verify unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication was received
   Performance Check:Verify unsolicited indication was received under 0n300000 ms
   PASS: Unsolicited indication was received in 0n0 ms
PASS: Attempt to send message to self, succeeded
Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
   Attempt OID_WWAN_SMS_DELETE set
   PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set SMS delete succeeded
Attempt to query SMS read (Flag:WwanSmsFlagAll Index:0x0)
   Attempt OID_WWAN_SMS_READ query
   PASS: OID_WWAN_SMS_READ succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify all indications are received under 0x3a98 seconds
   PASS: All indications are received under 0x3a98 seconds
PASS: Attempt to query SMS read, succeeded
Verify number of messages in receive list is 0x0
PASS: Number of messages in receive list (0x0) is 0x0
```

### <span id="s59"></span><span id="S59"></span>Test Summary: Win8MBN::TestSms::SmsReadAllMessages

The test reads all messages.

``` syntax
Attempt to initialize test
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Verify phone number of device was provided as a parameter or can be obtained from ready info
      Attempt to query ready info
         Attempt OID_WWAN_READY_INFO query
         PASS: OID_WWAN_READY_INFO succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
      PASS: Attempt to query ready info succeeded
   PASS: Phone number of device (4255551212) was obtained
   Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
      Attempt OID_WWAN_SMS_DELETE set
      PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS delete succeeded
PASS: Attempt to initialize test, succeeded
Attempt to send message to self
   Attempt to set SMS send
      Attempt OID_WWAN_SMS_SEND set
      PASS: OID_WWAN_SMS_SEND succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS send succeeded
   Verify unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication was received
   Performance Check:Verify unsolicited indication was received under 0n300000 ms
   PASS: Unsolicited indication was received in 0n0 ms
PASS: Attempt to send message to self, succeeded
Attempt to send message to self
   Attempt to set SMS send
      Attempt OID_WWAN_SMS_SEND set
      PASS: OID_WWAN_SMS_SEND succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS send succeeded
   Verify unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication was received
   Performance Check:Verify unsolicited indication was received under 0n300000 ms
   PASS: Unsolicited indication was received in 0n0 ms
PASS: Attempt to send message to self, succeeded
Attempt to query SMS read (Flag:WwanSmsFlagAll Index:0x0)
   Attempt OID_WWAN_SMS_READ query
   PASS: OID_WWAN_SMS_READ succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify all indications are received under 0x3a98 seconds
   PASS: All indications are received under 0x3a98 seconds
PASS: Attempt to query SMS read, succeeded
Verify number of messages in receive list of status WwanMsgStatusNew is 0x2
PASS: Number of messages (0x2) in receive list of status WwanMsgStatusNew (0x0) is 0x2
Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
   Attempt OID_WWAN_SMS_DELETE set
   PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set SMS delete succeeded
```

### <span id="s60"></span><span id="S60"></span>Test Summary: Win8MBN::TestSms::SmsReadNewMessages

The test reads all new messages.

``` syntax
Attempt to initialize test
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Verify phone number of device was provided as a parameter or can be obtained from ready info
      Attempt to query ready info
         Attempt OID_WWAN_READY_INFO query
         PASS: OID_WWAN_READY_INFO succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
      PASS: Attempt to query ready info succeeded
   PASS: Phone number of device (4255551212) was obtained
   Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
      Attempt OID_WWAN_SMS_DELETE set
      PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS delete succeeded
PASS: Attempt to initialize test, succeeded
Attempt to send message to self
   Attempt to set SMS send
      Attempt OID_WWAN_SMS_SEND set
      PASS: OID_WWAN_SMS_SEND succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS send succeeded
   Verify unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication was received
   Performance Check:Verify unsolicited indication was received under 0n300000 ms
   PASS: Unsolicited indication was received in 0n0 ms
PASS: Attempt to send message to self, succeeded
Attempt to query SMS read (Flag:WwanSmsFlagAll Index:0x0)
   Attempt OID_WWAN_SMS_READ query
   PASS: OID_WWAN_SMS_READ succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify all indications are received under 0x3a98 seconds
   PASS: All indications are received under 0x3a98 seconds
PASS: Attempt to query SMS read, succeeded
Verify number of messages in receive list of status WwanMsgStatusNew is 0x1
PASS: Number of messages (0x1) in receive list of status WwanMsgStatusNew (0x0) is 0x1
Attempt to send message to self
   Attempt to set SMS send
      Attempt OID_WWAN_SMS_SEND set
      PASS: OID_WWAN_SMS_SEND succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to set SMS send succeeded
   Verify unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication is received
   PASS: Unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication was received
   Performance Check:Verify unsolicited indication was received under 0n300000 ms
   PASS: Unsolicited indication was received in 0n0 ms
PASS: Attempt to send message to self, succeeded
Attempt to query SMS read (Flag:WwanSmsFlagNew Index:0x0)
   Attempt OID_WWAN_SMS_READ query
   PASS: OID_WWAN_SMS_READ succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify all indications are received under 0x3a98 seconds
   PASS: All indications are received under 0x3a98 seconds
PASS: Attempt to query SMS read, succeeded
Verify number of messages in receive list of status WwanMsgStatusNew is 0x1
PASS: Number of messages (0x1) in receive list of status WwanMsgStatusNew (0x0) is 0x1
Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
   Attempt OID_WWAN_SMS_DELETE set
   PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set SMS delete succeeded
```

### <span id="s61"></span><span id="S61"></span>Test Summary: Win8MBN::TestVisibleProvider::RadioOff

The test queries visible providers while radio is off.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n15 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt to query supported OIDs
   Attempt OID_GEN_SUPPORTED_LIST query
   PASS: OID_GEN_SUPPORTED_LIST succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
PASS: Attempt to query supported OIDs succeeded
Verify device supports OID_WWAN_VISIBLE_PROVIDERS
PASS: Device supports OID_WWAN_VISIBLE_PROVIDERS
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
Attempt to set SwRadioState (WwanRadioOff[0x0])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOff[0x0]) succeeded
Wait for unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication for 0x7530 seconds
PASS: Succeeded to receive unsolicited NDIS_STATUS_WWAN_REGISTER_STATE (WwanRegisterStateDeregistered) indication
Performance Check:Verify unsolicited indication was received under 0n30000 ms
PASS: Unsolicited indication was received in 0n16 ms
Attempt to query visible providers
   Attempt OID_WWAN_VISIBLE_PROVIDERS query
   PASS: OID_WWAN_VISIBLE_PROVIDERS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n200000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_RADIO_POWER_OFF[0xc0040015]
   PASS: Status is WWAN_STATUS_RADIO_POWER_OFF[0xc0040015]
PASS: Attempt to query visible providers succeeded
Attempt to set SwRadioState (WwanRadioOn[0x1])
   Attempt OID_WWAN_RADIO_STATE set
   PASS: OID_WWAN_RADIO_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS
   PASS: Status is WWAN_STATUS_SUCCESS
PASS: Attempt to set SwRadioState (WwanRadioOn[0x1]) succeeded
```

### <span id="s62"></span><span id="S62"></span>Test Summary: Win8MBN::TestVisibleProvider::Registered

The test queries visible providers while auto registered.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt to query supported OIDs
   Attempt OID_GEN_SUPPORTED_LIST query
   PASS: OID_GEN_SUPPORTED_LIST succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
PASS: Attempt to query supported OIDs succeeded
Verify device supports OID_WWAN_VISIBLE_PROVIDERS
PASS: Device supports OID_WWAN_VISIBLE_PROVIDERS
Attempt to auto register
   Attempt to query device capabilities
      Attempt OID_WWAN_DEVICE_CAPS query
      PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n0 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query device capabilities succeeded
   Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
      Attempt OID_WWAN_REGISTER_STATE set
      PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n50000 ms
      PASS: Indication was received in 0n16 ms
      Verify status is WWAN_STATUS_SUCCESS
      PASS: Status is WWAN_STATUS_SUCCESS
   PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
PASS: Attempt to auto register, succeeded
Attempt to query visible providers
   Attempt OID_WWAN_VISIBLE_PROVIDERS query
   PASS: OID_WWAN_VISIBLE_PROVIDERS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n200000 ms
   PASS: Indication was received in 0n15 ms
   Verify status
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query visible providers succeeded
Verify indication length is equal to or greater than 0x1
PASS: Indication length (0x60) is valid
Verify element type is WwanStructProvider2
PASS: Element type is WwanStructProvider2
Verify indication length is equal to or greater than 0x60
PASS: Indication length (0x60) is valid
Verify ProviderId is NULL terminated
PASS: ProviderId is NULL terminated
Verify ProviderId contains only digits
PASS: ProviderId (12301) contains only digits
Verify ProviderId is 5 digits in length for CDMA devices
PASS: ProviderId length (0x5) is valid
Verify ProviderState only uses WWAN_PROVIDER_STATE_HOME,WWAN_PROVIDER_STATE_FORBIDDEN,WWAN_PROVIDER_STATE_PREFERRED,WWAN_PROVIDER_STATE_VISIBLE, and\or WWAN_PROVIDER_STATE_REGISTERED
PASS: ProviderState (0x19) is valid
Verify ProviderName is NULL terminated
PASS: ProviderName is NULL terminated
Verify ProviderName is populated
PASS: ProviderName (MS MBN) is populated
Device is CDMA, verify only the home provider is reported
PASS: Only the home provider is reported
```

### <span id="s63"></span><span id="S63"></span>Test Summary: Win8MBN::TestVisibleProvider::Connected

The test queries visible providers while connected.

``` syntax
Attempt to query device capabilities
   Attempt OID_WWAN_DEVICE_CAPS query
   PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n16 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query device capabilities succeeded
Attempt to query supported OIDs
   Attempt OID_GEN_SUPPORTED_LIST query
   PASS: OID_GEN_SUPPORTED_LIST succeeded, NTSTATUS(NDIS_STATUS_SUCCESS[0x0])
PASS: Attempt to query supported OIDs succeeded
Verify device supports OID_WWAN_VISIBLE_PROVIDERS
PASS: Device supports OID_WWAN_VISIBLE_PROVIDERS
Attempt to connect using provisioned context
   Attempt to query provisioned contexts
      Attempt OID_WWAN_PROVISIONED_CONTEXTS query
      PASS: OID_WWAN_PROVISIONED_CONTEXTS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
      Verify indication is received
      PASS: Indication was received
      Performance Check:Verify indication was received under 0n15000 ms
      PASS: Indication was received in 0n15 ms
      Verify status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Attempt to query provisioned contexts succeeded
   Attempt to find provisioned context of WwanContextTypeInternet
   PASS: Attempt to find provisioned context of WwanContextTypeInternet succeeded
   Attempt to connect to home provider
      Attempt to query Register State
         Attempt OID_WWAN_REGISTER_STATE query
         PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n0 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to query register state succeeded
      Attempt to auto register
         Attempt to query device capabilities
            Attempt OID_WWAN_DEVICE_CAPS query
            PASS: OID_WWAN_DEVICE_CAPS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n15000 ms
            PASS: Indication was received in 0n0 ms
            Verify status is WWAN_STATUS_SUCCESS[0x0]
            PASS: Status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Attempt to query device capabilities succeeded
         Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000)
            Attempt OID_WWAN_REGISTER_STATE set
            PASS: OID_WWAN_REGISTER_STATE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
            Verify indication is received
            PASS: Indication was received
            Performance Check:Verify indication was received under 0n50000 ms
            PASS: Indication was received in 0n15 ms
            Verify status is WWAN_STATUS_SUCCESS
            PASS: Status is WWAN_STATUS_SUCCESS
         PASS: Attempt to set register state (action:WwanRegisterActionAutomatic dataclass:0x7f0000) succeeded
      PASS: Attempt to auto register, succeeded
      Attempt to set packet service (WwanPacketServiceActionAttach)
         Attempt OID_WWAN_PACKET_SERVICE set
         PASS: OID_WWAN_PACKET_SERVICE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n15000 ms
         PASS: Indication was received in 0n16 ms
         Verify status is WWAN_STATUS_SUCCESS
         PASS: Status is WWAN_STATUS_SUCCESS
      PASS: Attempt to set packet service (WwanPacketServiceActionAttach) succeeded
      Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password
         Attempt OID_WWAN_CONNECT set
         PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
         Verify indication is received
         PASS: Indication was received
         Performance Check:Verify indication was received under 0n30000 ms
         PASS: Indication was received in 0n125 ms
         Verify status is WWAN_STATUS_SUCCESS[0x0]
         PASS: Status is WWAN_STATUS_SUCCESS[0x0]
      PASS: Attempt to set connect context WwanActivationCommandActivate microsoft.com admin password, succeeded
      Verify connection id of returned context state is 0xbf
      PASS: Connection id of returned context state is 0xbf
      Verify activation state of returned context state is WwanActivationStateActivated
      PASS: Activation state (WwanActivationStateActivated) of returned context state is WwanActivationStateActivated
   PASS: Attempt to connect, succeeded
PASS: Attempt to connect using provisioned context succeeded
Attempt to query visible providers
   Attempt OID_WWAN_VISIBLE_PROVIDERS query
   PASS: OID_WWAN_VISIBLE_PROVIDERS succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n200000 ms
   PASS: Indication was received in 0n0 ms
   Verify status
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to query visible providers succeeded
Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null)
   Attempt OID_WWAN_CONNECT set
   PASS: OID_WWAN_CONNECT succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n30000 ms
   PASS: Indication was received in 0n31 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set connect context WwanActivationCommandDeactivate (null) (null) (null), succeeded
Verify connection id of returned context state is 0xbf
PASS: Connection id of returned context state is 0xbf
Verify activation state of returned context state is WwanActivationStateDeactivated
PASS: Activation state (WwanActivationStateDeactivated) of returned context state is WwanActivationStateDeactivated
```

### <span id="s64"></span><span id="S64"></span>Test Summary: Win8MBN::TestWake::WakeMachineFromConnectedStandbyWithSmsMessage

The test will verify the machine supports InstantGo, put the machine into Connected Standby, and wait for SMS message.

``` syntax
Verify platform supports always on always connected
PASS: Platform supports always on always connected
Attempt to disable interface ({34404430-9CE9-42E2-9086-F8EF87E6E9BD})
PASS: Attempt to disable interface ({34404430-9CE9-42E2-9086-F8EF87E6E9BD}), succeeded
Attempt to set SMS delete (Flag:WwanSmsFlagAll Index:0x0)
   Attempt OID_WWAN_SMS_DELETE set
   PASS: OID_WWAN_SMS_DELETE succeeded, NTSTATUS (NDIS_STATUS_INDICATION_REQUIRED[0x40230001])
   Verify indication is received
   PASS: Indication was received
   Performance Check:Verify indication was received under 0n15000 ms
   PASS: Indication was received in 0n0 ms
   Verify status is WWAN_STATUS_SUCCESS[0x0]
   PASS: Status is WWAN_STATUS_SUCCESS[0x0]
PASS: Attempt to set SMS delete succeeded
Verify unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication is received
PASS: Unsolicited NDIS_STATUS_WWAN_SMS_STATUS indication was received
Performance Check:Verify unsolicited indication was received under 0n300000 ms
PASS: Unsolicited indication was received in 0n0 ms
Verify wait wake event was triggered
PASS: Wait wake event was triggered
Attempt to enable interface ({34404430-9CE9-42E2-9086-F8EF87E6E9BD})
PASS: Attempt to enable interface ({34404430-9CE9-42E2-9086-F8EF87E6E9BD}), succeeded
```

 

 






