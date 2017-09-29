---
title: Global Navigation Satellite System (GNSS) Test Guidance
description: Global Navigation Satellite System (GNSS) Test Guidance
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 43fd72a4-e081-442f-8820-d06e82908604
---

# Global Navigation Satellite System (GNSS) Test Guidance


This article provides global positioning system (GPS) implementation guidelines to ensure a high-quality, competitive GPS experience in computers that run Windows 8 and Windows 8.1. The guidelines in this article apply to original equipment manufacturers (OEMs), independent hardware vendors (IHVs), and other Microsoft partners (such as software vendors). This article focuses on testing the integration of global navigation satellite system (GNSS) devices into a Windows 8 system.

Testing of areas other than GPS is out of the scope of this document. Fully exercising the operating system components or the GNSS device is out of the scope of this document. It is assumed that the IHVs and OEMs thoroughly test their GNSS device both independently and integrated into the system. Interoperability testing is limited to the components that interact with the location platform and devices. This testing should include successful completion of the [Windows Hardware Lab Kit (Windows HLK)](http://go.microsoft.com/fwlink/?LinkID=8705) tests, this test plan, pre-operator trial tests, and internal tests that are developed specifically for the GNSS driver and GNSS receiver.

>[!NOTE]
>  
In this article, the term GPS is used interchangeably with GNSS. Unless it is otherwise stated, GPS refers to satellite positioning as a location provider solution, instead of as the GPS satellite system that is deployed by the United States government.

 

Clear sky conditions are defined as GPS/GNSS satellites that receive signals without obstruction from above or from the surrounding environment down to an elevation mask of 5 degrees above the horizon. All signal levels must be consistent with unobstructed signal levels at the ground and not lower than -131 dBm.

This information applies to the following operating systems:

-   Windows 8

-   Windows 8.1

**In this article:**

-   [Requirements from Partners](#partreqs)

-   [Reporting and results communication](#reporting)

-   [Test equipment](#equip)

-   [Functionality tests](#functtests)

-   [Assisted GPS tests](#agps)

-   [Power consumption tests](#powercon)

-   [Power management tests](#powerman)

-   [Antenna performance tests](#antperf)

-   [Interoperability tests](#interop)

-   [Drive tests](#drivetests)

-   [Simulator tests](#simtests)

-   [GPS acceptance test matrix](#matrix)

## <span id="partreqs"></span><span id="PARTREQS"></span>Requirements from Partners


To receive certification, Microsoft partners must meet the following requirements:

-   To enable Assisted GPS (A-GPS) testing and the ability to cold-start a device, GNSS Drivers must support the SENSOR\_PROPERTY\_CLEAR\_ASSISTANCE\_DATA property. To enable turning on and turning off National Marine Electronics Association (NMEA) sentences in data reports, the GNSS Driver must support SENSOR\_PROPERTY\_TURN\_ON\_OFF\_NMEA. By default, NMEA lines are not included in data reports. This requirement is explicitly described here:

    //{e1e962f4-6e65-45f7-9c36-d487b7b1bd34}DEFINE\_GUID(SENSOR\_PROPERTY\_TEST\_GUID, 0XE1E962F4, 0X6E65, 0X45F7, 0X9C, 0X36, 0XD4, 0X87, 0XB7, 0XB1, 0XBD, 0X34);DEFINE\_PROPERTYKEY(SENSOR\_PROPERTY\_CLEAR\_ASSISTANCE\_DATA, 0XE1E962F4, 0X6E65, 0X45F7, 0X9C, 0X36, 0XD4, 0X87, 0XB7, 0XB1, 0XBD, 0X34, 2); //\[VT\_UI4\]

    DEFINE\_PROPERTYKEY(SENSOR\_PROPERTY\_TURN\_ON\_OFF\_NMEA, 0XE1E962F4, 0X6E65, 0X45F7, 0X9C, 0X36, 0XD4, 0X87, 0XB7, 0XB1, 0XBD, 0X34, 3); //\[VT\_UI4\]

    \#define GNSS\_CLEAR\_ALL\_ASSISTANCE\_DATA 0x00000001

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tbody>
    <tr class="odd">
    <td><p><strong>SENSOR_PROPERTY_ CLEAR_ASSISTANCE_DATA (PID = 2)</strong></p></td>
    <td><p><strong>VT_UI4</strong>. Write. Clear the assistance data. Setting a value of GNSS_CLEAR_ALL_ASSISTANCE_DATA signals the driver to clear all assistance data, including time, almanac, ephemeris and last position.Windows HLK tests can set this value to clear the assistance data before a cold start test, before A-GPS tests, or independently before running simulator tests where time and location is simulated. If A-GPS capabilities (for example, SUPL, LTO) are supported, the driver can try to utilize the capabilities after this operation by using the network connection. However, the device should be in a state where no assistance data is saved in the device or on the system. Any assistance data elements are downloaded again.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>SENSOR_PROPERTY_TURN_ON_OFF_NMEA (PID = 3)</strong></p></td>
    <td><p><strong>VT_UI4</strong>. Read/Write. If set to TRUE, NMEA sentence is included in data reports. If set to False, NMEA sentence is not included in data reports. Windows HLK tests can use this property to instruct the device to start or stop including NMEA data in data reports.</p></td>
    </tr>
    </tbody>
    </table>

     

-   In addition to required Windows Hardware Lab Kit (Windows HLK) tests, optional Windows HLK [Device.Input Tests](device-input-tests.md) must run and pass for non-ARM System on Chip (SoC) systems. (These tests are already mandatory for ARM systems).

-   OEMs and IHVs must run and document the tests that are specified in the [GPS acceptance test matrix](#matrix) before they can submit a system, device, or driver to Microsoft.

-   IHVs should review failures as reported at http://sysdev.microsoft.com that are caused by their GPS drivers, and fix all high-impact failures.

-   Antenna requirements from OEMs must include the items that are listed in [Antenna performance tests](#antperf).

-   The SENSOR\_DATA\_TYPE\_NMEA\_SENTENCE property must be supported on systems to verify dynamic navigation accuracy and antenna quality.

-   No dependency on third-party services or Win32 applications can accompany the GPS solution. Third-party Win32 applications are subject to signing requirements on SoC systems and are therefore not allowed.

-   USB connected GPS devices must support selective suspend.

-   GPS on mobile broadband modules must update by using [Unified Extensible Firmware Interface](http://www.uefi.org/specifications) (UEFI), and a standalone GPS must update by using a driver.

-   When GPS and mobile broadband exist on the same physical chip, the GPS device should be exposed as part of a USB composite device and it should have its own USB interface.

## <span id="reporting"></span><span id="REPORTING"></span>Reporting and results communication


Microsoft will communicate all issues to partners using bugs. The bugs will contain Windows HLK logs, traces, driver logs, crash dumps, and any relevant performance results and baseline performance comparison data.

## <span id="equip"></span><span id="EQUIP"></span>Test equipment


The following test equipment is used to perform the tests that are described in this article:

-   [Spirent GSS6700 GNSS Simulator](http://www.spirent.com/Products/GSS6700.aspx)

-   Faraday cage

-   RF shielding box

-   Mobile Broadband SIM

-   Reference Devices: Garmin Montana; Windows Tablets that have GPs devices that are certified by using Microsoft Signature.

-   External antennas

## <span id="functtests"></span><span id="FUNCTTESTS"></span>Functionality tests


Windows HLK tests that apply to GNSS devices are the first set of tests to verify the basic functionality of GPS devices. Windows HLK contains tests for GPS Sensors, Radio Manager, Device Fundamentals, System Fundamentals Power Management, and USB Hardware Certification tests (for USB connected devices) that apply to GNSS devices.

### <span id="Sensor_category__type__properties_and_data_fields"></span><span id="sensor_category__type__properties_and_data_fields"></span><span id="SENSOR_CATEGORY__TYPE__PROPERTIES_AND_DATA_FIELDS"></span>Sensor category, type, properties and data fields

**Description**: The device should report correct sensor category and type, support mandatory properties and data fields, and report accurate data. In addition to the mandatory sensor properties that are verified in the Windows HLK, managed program systems must support the SENSOR\_DATA\_TYPE\_NMEA\_SENTENCE property.

**Run Steps**: Query sensor category, type, properties, and data fields the Device Under Test (DUT) reports. Confirm the accuracy of the reported data. You can use the Sensor Diagnostics Tool (SDT) in the [Windows Driver Kit (WDK)](http://go.microsoft.com/fwlink/?LinkID=256421) to test these items.

**Expected Result**: Mandatory fields must be supported and report accurate data.

### <span id="State_transitions"></span><span id="state_transitions"></span><span id="STATE_TRANSITIONS"></span>State transitions

**Description**: The device should report changes in sensor state, as documented in [Writing a location sensor driver](http://go.microsoft.com/fwlink/?LinkID=299233).

-   Data reports must be reported only after a device reaches SENSOR\_STATE\_READY or SENSOR\_STATE\_INITIALIZING.

-   A device should not report data if it does not have latitude and longitude information.

-   A GPS sensor must start in the SENSOR\_STATE\_INITIALIZING state before it obtains a location fix.

-   A GPS sensor should continue to acquire a location fix and must stay in the SENSOR\_STATE\_INITIALIZING state until the request is cancelled by the operating system.

-   A GPS sensor must go into the SENSOR\_STATE\_INITIALIZING state when it loses the signal and no longer has data. It should go back to into the SENSOR\_STATE\_READY state when it reacquires a location fix.

**Run Steps**: You must monitor state transitions and data events while you disable and re-enable the device. Move into an area that has no GPS signal (for example, a Faraday cage), wait for at least one minute, and return the device to an area that has coverage.

**Expected Result**: The device should report sensor state transitions (for example, from SENSOR\_STATE\_INITIALIZING to SENSOR\_STATE\_READY), and data reports should be reported only after reaching these states. Data is only reported if latitude and longitude information is available. The device should start in the SENSOR\_STATE\_INITIALIZING state and should not move into the SENSOR\_STATE\_READY state until after it gets a location fix and has a valid error radius. When the device is moved out of a GPS signal coverage area, the device should go into the SENSOR\_STATE\_INITIALIZING state, and it should revert to SENSOR\_STATE\_READY when it is returned to a coverage area.

### <span id="Latitude_and_longitude_accuracy"></span><span id="latitude_and_longitude_accuracy"></span><span id="LATITUDE_AND_LONGITUDE_ACCURACY"></span>Latitude and longitude accuracy

**Description**: The device should provide accurate latitude and longitude values in the specified error radius.

**Run Steps**: During static testing and in-vehicle testing, device data is compared to latitude and longitude data that reference GPS, survey markers, and a simulator report.

**Expected Result**: The difference between the latitude and longitude values that the device reports and the reference GPS reports must be inside the error radius.

### <span id="Speed_data"></span><span id="speed_data"></span><span id="SPEED_DATA"></span>Speed data

**Description**: The device should report speed data in knots when the device is moving.

**Run Steps**: Monitor the speed data that the device reports during simulated in-vehicle or drive tests.

**Expected Result**: The device should report speed data that is accurate within ±15% of the speed data that a reference GPS or simulator reports.

### <span id="Heading_data"></span><span id="heading_data"></span><span id="HEADING_DATA"></span>Heading data

**Description**: The device should report headings in degrees that are relative to true north when the device is moving.

**Run Steps**: Monitor the heading data that is reported by the device during simulated in-vehicle tests, manual walking tests, and drive tests.

**Expected Result**: The device should report heading data, which should be within ±15% of the heading data that a reference GPS or simulator reports.

### <span id="Other_sensor_properties"></span><span id="other_sensor_properties"></span><span id="OTHER_SENSOR_PROPERTIES"></span>Other sensor properties

**Description**: If other sensor properties are supported by the device, the properties should report valid data and accurate values.

**Run Steps**: Monitor properties that the device supports and verify that they provide valid data within acceptable accuracy ranges.

**Expected Result**: If a device supports a particular sensor property, the device should report accurate values within ±20% of the values that a reference GPS or simulator reports.

## <span id="agps"></span><span id="AGPS"></span>Assisted GPS tests


Within a few seconds of initial power-up, a GPS device should use A-GPS to return an approximated location. When the GPS uses A-GPS, the sensor should provide location data, which can be from several hundred meters to six figure numbers. When the GPS radio can obtain multiple satellite locks, the error radius should decrease to a value of 3 to 30 meters.

### <span id="A-GPS"></span><span id="a-gps"></span>A-GPS

**Description**: A-GPS should help to obtain a faster Time to First Fix (TTFF) that has higher accuracy.

**Run Steps**: Cold-start the GPS device. Monitor latitude, longitude and error radius data fields by using the SDT.

You should run the tests under the following conditions:

-   Clear-sky conditions (simulated or actual)

-   Subscribed for data events

-   Report interval of one second

-   Wi-Fi or cellular baseband is present and enabled

**Expected Result**: The device should return a position from A-GPS as soon as possible, and should report an associated error radius. The higher error radius (for example, 300 meters if Wi-Fi is available) should decrease to 3 to 30 meters as the device acquires multiple satellite locks. GPS should report a position within 15 seconds that is based on assistance data.

### <span id="Position_injection"></span><span id="position_injection"></span><span id="POSITION_INJECTION"></span>Position injection

A GPS driver can use data from its triangulation sensors to speed up TTFF by using the Sensor API ([ISensorManager](http://go.microsoft.com/fwlink/?LinkID=288833)). If a driver is used, the following tests apply:

-   **Connection time**

    **Description**: A GPS driver should close the connection to other sensors immediately after it gets a position. It should timeout after 15 seconds and it should close the connection to the Sensor API if it does not get a position.

    **Run Steps**: Monitor the traces from the Sensor API for the active client counts for all sensors in the system. Cold-start the GPS device and monitor the changes on the active client counts for other sensors in the system.

    **Expected Result**: If active client counts for other sensors are incremented, they should return to their previously recorded values after 15 seconds.

-   **Connection type**

    **Description**: GPS drivers should not instantiate [ILocation](http://go.microsoft.com/fwlink/?LinkID=288834) to get data from other location sensors. They can use the Sensor API to open a connection for instance triangulation sensors (SENSOR\_TYPE\_LOCATION\_TRIANGULATION). A GPS driver should not get data from location sensors of the same type. For example, a GPS sensor should not use data from other sensors with type **GPS** to get a faster location fix.

    **Run Steps**: Discover the sensor type that the device is reporting; for example, SENSOR\_TYPE\_LOCATION\_GPS. Disable all sensors except for sensors of the same type as the device. Monitor the traces from the Sensor API for the active client counts for enabled sensors in the system. Cold-start the GPS device. Monitor the changes on the active client counts for sensors in the system.

    **Expected Result**: The device should not increment active client counts for sensors of the same type.

## <span id="Robustness"></span><span id="robustness"></span><span id="ROBUSTNESS"></span>Robustness


*Driver Verifier*, *WDF Verifier*, and *Application Verifier* are enabled for the location platform and the GPS device stack to test the reliability of GPS support in the system.

Driver Verifier is part of the Windows operating system. It can be started from a command prompt that has administrative privileges by using the following settings:

**Verifier /standard /driver wudfpf.sys Wdf01000.sys Wdfldr.sys wudfrd.sys** &lt;*any kernel mode driver* &gt;, &lt;*dependent kernel mode drivers* &gt;

Where &lt;*any kernel mode driver*&gt; is the driver to be verified, and &lt;*dependent kernel mode drivers*&gt; are the kernel mode drivers on which the GPS driver depends; for example, **wmbclass.sys**.

For more information about Driver Verifier, see [About Driver Verifier](http://go.microsoft.com/fwlink/?LinkID=288849).

WDF Verifier is enabled by default for all WDF drivers. The **WdfVerifier.exe** tool in the WDK can be used to control the verbosity of logging, debugger settings, and more. For more information about WDF Verifier, see [WDF Verifier Control Application](http://go.microsoft.com/fwlink/?LinkID=288836).

[Application Verifier](httrp://go.microsoft.com/fwlink/?LinkID=254761) (**appverif.exe**) is available in Windows HLK and the Windows 8.1 SDK. A minimum of basic settings is required.

### <span id="Driver_Verifier__WDF_Verifier_and_Application_Verifier"></span><span id="driver_verifier__wdf_verifier_and_application_verifier"></span><span id="DRIVER_VERIFIER__WDF_VERIFIER_AND_APPLICATION_VERIFIER"></span>Driver Verifier, WDF Verifier and Application Verifier

**Description**: Enable Application Verifier and Driver Verifier at the beginning of testing.

**Run Steps**: Enable Driver Verifier on all kernel mode drivers in the driver package (if any) and enable any kernel mode drivers on which the GPS driver depends. Enable Application Verifier for **%windir%\\system32\\WUDFHost.exe** and other user-mode binaries on which the GPS driver depends (for example, **wwanapi.dll**).

**Expected Result**: No verifier failures.

### <span id="Telemetry_data"></span><span id="telemetry_data"></span><span id="TELEMETRY_DATA"></span>Telemetry data

**Description**: Monitor telemetry data from site http://sysdev.microsoft.com for the GPS driver.

**Run Steps**: Monitor telemetry data from http://sysdev.microsoft.com for the GPS driver. Identify, investigate, and fix the driver failures.

**Expected Result**: The device must report all telemetry failures; you should triage, investigate, and fix the primary problems.

### <span id="GPS_stress_tests"></span><span id="gps_stress_tests"></span><span id="GPS_STRESS_TESTS"></span>GPS stress tests

A combination of the following operations is simultaneously performed on the GPS device during simulator testing, walk testing, and drive testing:

-   Enable Driver Verifier

-   Enable Application Verifier

-   Repeated Windows HLK test runs (GPS Sensor, Radio Manager, System Power Management)

-   Radio management operations

-   Connected Standby

-   GPS device disable/re-enable

-   Windows Location Provider disable/re-enable

-   Mobile Broadband device disable/re-enable

-   Wi-Fi device disable/re-enable

-   Turn off Mobile Broadband radio

-   Turn off Wi-Fi Radio

-   Large download over Mobile Broadband connection

-   Large download over Wi-Fi connection

-   Bluetooth activity

Perform a basic verification test before the stress testing. It is expected that the same verification test passes both before and after the stress tests, and that no failures are observed.

## <span id="Performance"></span><span id="performance"></span><span id="PERFORMANCE"></span>Performance


GPS device performance is tested for cold-start TTFF, hot-start TTFF, acquisition sensitivity, tracking sensitivity, re-acquisition time, static navigation accuracy, and dynamic navigation accuracy.

A GNNS simulator that has an OTA connection can be used for performance testing.

### <span id="Cold-start_TTFF"></span><span id="cold-start_ttff"></span><span id="COLD-START_TTFF"></span>Cold-start TTFF

**Description**: Cold-start TTFF should be achieved in less than 45 seconds for 90% of the time. Cold-start is described as the following condition:

-   Time is unknown

-   Current ephemeris is unknown

-   Position is unknown

**Run Steps**: You can use the SDT to clear the GPS assistance data before you start the cold-start test. Ensure that the cold-start conditions described above are met. Monitor the TTFF under clear sky conditions (actual or simulated).

**Expected Result**: The device should use the GNSS device to get a location fix within 45 seconds for 90% of the time.

### <span id="Acquisition_sensitivity"></span><span id="acquisition_sensitivity"></span><span id="ACQUISITION_SENSITIVITY"></span>Acquisition sensitivity

**Description**: The device should obtain a location fix at -150 dBm or lower power levels.

**Run Steps**: Under simulated lab conditions, by using a direct radio frequency (RF) connection when antenna connector is accessible, expose device to low power levels up to -150 dBm.

**Expected Result**: The device should acquire a fix at -150 dBm.

### <span id="Tracking_sensitivity"></span><span id="tracking_sensitivity"></span><span id="TRACKING_SENSITIVITY"></span>Tracking sensitivity

**Description**: The device should maintain a location fix at -155 dBm or lower power levels.

**Run Steps**: Under simulated lab conditions, by using a direct RF connection when an antenna connector is accessible, reduce the power level to -155 dBm after the device obtains a location fix.

**Expected Result**: The device should maintain a location fix -155 dBm.

### <span id="Reacquisition_time"></span><span id="reacquisition_time"></span><span id="REACQUISITION_TIME"></span>Reacquisition time

**Description**: The device should be able to reacquire a location fix in 2 seconds. Clear sky conditions are assumed when a signal is available.

**Run Steps**: Under simulated lab conditions, after the device obtains a location fix, reduce the power level enough to force the device to lose the fix. Then increase power levels and monitor the reacquisition time. Alternatively, you can drive through a tunnel during drive testing.

**Expected Result**: The device should reacquire a location fix in 2 seconds.

### <span id="Static_navigation_accuracy"></span><span id="static_navigation_accuracy"></span><span id="STATIC_NAVIGATION_ACCURACY"></span>Static navigation accuracy

**Description**: The device should report accurate latitude, longitude, and altitude (if supported).

**Run Steps**: Compare the accuracy of longitude, latitude and altitude (if available), to the location from a trusted data source. Trusted data sources can be survey markers, GNSS simulators, or a Microsoft Signature-certified Windows tablet that has GPS.

**Expected Result**: The DUT should report horizontal accuracy of 15 meters and vertical accuracy of 30 meters for 95% of the time.

### <span id="Dynamic_navigation_accuracy"></span><span id="dynamic_navigation_accuracy"></span><span id="DYNAMIC_NAVIGATION_ACCURACY"></span>Dynamic navigation accuracy

**Description**: When the DUT is mobile, the DUT should accurately report latitude, longitude and altitude if supported.

**Run Steps**: During simulated or actual device/walk testing, compare the accuracy of longitude, latitude and altitude (if available), to the location from trusted data source. Trusted data sources can be survey markers, GNSS simulators, or a Microsoft Signature-certified Windows tablet that has GPS.

**Expected Result**: Device should report horizontal accuracy of 15 meters and vertical accuracy of 100 meters.

## <span id="powercon"></span><span id="POWERCON"></span>Power consumption tests


The following diagram illustrates how a driver can use WDF idle detection **StopIdle/ResumeIdle** methods to move between D-States.  The test cases in this section confirm that the driver is going to the correct state at the appropriate time.

&lt;*Art placeholder for Fig1\_ Fig1\_stopidle\_resumeidle*&gt;

Figure 1. StopIdle/ResumeIdle

### <span id="USB_selective_suspend"></span><span id="usb_selective_suspend"></span><span id="USB_SELECTIVE_SUSPEND"></span>USB selective suspend

This test applies to USB connected devices only. A GPS device for which no clients subscribe for a report interval of 8 seconds or less should participate on selective suspend when all devices on the bus are ready to go into a Suspend state.

Device Manager and [Event Tracing for Windows (ETW)](http://go.microsoft.com/fwlink/?LinkID=256040) events are used to monitor the USB bus state transitions.

### <span id="Average_sleep_power_consumption"></span><span id="average_sleep_power_consumption"></span><span id="AVERAGE_SLEEP_POWER_CONSUMPTION"></span>Average sleep power consumption

GPS device should have a sleep average power consumption of less than 1mW, including any bus connection interfaces. If this is not the case, the device must support removing power completely from the GPS device when in D3 (D3-Cold).

### <span id="D3-Cold"></span><span id="d3-cold"></span><span id="D3-COLD"></span>D3-Cold

Devices that support D3cold should not degrade the TTFF performance for more than 6 seconds. For example, if a device can get a location fix in 2 seconds under hot-start conditions, it should be able to get a fix in 8 seconds or less when it resumes from D3cold. If device cannot meet this requirement, the driver should limit D3cold state transitions to when GPS Radio is disabled.

For more information about D3cold, see [Supporting D3cold in a Driver](http://go.microsoft.com/fwlink/?LinkID=288844).

## <span id="powerman"></span><span id="POWERMAN"></span>Power management tests


### <span id="Connected_Standby"></span><span id="connected_standby"></span><span id="CONNECTED_STANDBY"></span>Connected Standby

Connected Standby testing includes Windows HLK PowerState tests and Device Fundamentals tests with IO cover test scenarios.

**Resume in no coverage area**

**Description**: Put the system into the Connected Standby state when there are active clients. Resume in a no-coverage area. The device should try to acquire a location fix and enter the SENSOR\_STATE\_INITIALIZING state.

**Run Steps**: When active clients are connected, put the device into Connected Standby. Wake from Connected Standby in an area that does not have a GPS signal.

**Expected Result**: The device should acquire a location fix and go into the SENSOR\_STATE\_INITIALIZING state.

## <span id="antperf"></span><span id="ANTPERF"></span>Antenna performance tests


### <span id="Performance_tests_that_use_an_OTA_connection"></span><span id="performance_tests_that_use_an_ota_connection"></span><span id="PERFORMANCE_TESTS_THAT_USE_AN_OTA_CONNECTION"></span>Performance tests that use an OTA connection

It is common to performance-test GNSS receivers in a lab environment over a cabled RF connection, thereby bypassing the GPS antenna and its associated circuitry. Device performance and issues in GPS antenna and its circuitry can cause poor user experience in location-based service applications. To discover these issues, you should test managed system devices for GPS performance by using an OTA test methodology.

Antenna testing includes the following requirements for certification:

-   Systems that have GPS support must pass testing according to the [Cellular Telecommunications & Internet Association (CTIA)](http://ctia.org) Test Plan for Mobile Station Over-the-Air Performance, Method of Measurement for Radiated Radio Frequency (RF) Power and Receiver Performance v3.0+ for A-GPS. For more information about CTIA tests, see [CTIA Certification Tests](http://ctia.org/business_resources/certification/index.cfm/AID/11259). In addition, Total Isotropic Sensitivity (TIS), Upper Hemisphere Isotropic Sensitivity (UHIS) and Partial Isotropic GPS Sensitivity (PIGS), must be measured; OEMs must post measurement results to Microsoft for review. These requirements apply to systems that have Mobile Broadband support.

-   The system must have TIS and UHIS free space of -140 dBm or better for GPS. For systems that have Mobile Broadband support, the measurements must follow the test methodology and test parameters that are defined in the Antenna Performance for execution guidelines for Wi-Fi-only systems section of the CTIA 3.x test plan.

-   The average gain of the GPS antenna must be better than -6dBi.

-   Performance must not drop below the minimal acceptable standard when the device is held in a common handheld position. The device must maintain over-the-air (OTA) acquisition sensitivity at -140 dBm and OTA tracking sensitivity of -145 dBm when the system is held in common positions.

-   The device must maintain OTA acquisition sensitivity at -140 dBm and OTA tracking sensitivity of -145 dBm when the keyboard or docking station is closed.

-   You must perform antenna and radiated sensitivity testing when the GPS antenna is in the expected positions in the device.

-   The intended GPS production antenna must be in its intended location for Engineering Verification (EV) systems. The antenna location must be finalized for Design Verification (DV) systems.

-   OEMs should run antenna performance and radiated sensitivity tests and understand the failures on EV units. The tests must pass prior to DV units.

**RF Sensitivity Testing for Wi-Fi-only systems**

A GPS IHV can provide NMEA logging and plotting tools and documentation.

Compare Signal-to-Noise Ratio (SNR) on the test device and on a reference device that has good GPS RF sensitivity at the same location under the same conditions. Enable IHV NMEA logs and take the devices for walk/drive testing for 15+ minutes under a clear sky. Analyze the logs by using the NMEA Plotting tool that the IHV provides. Compare average signal strength of the devices.

>[!NOTE]
>  
If you do not have the NMEA Plotting tool from an IHV, you can use Microsoft<sup>®</sup> Bing

 

### <span id="Human_interference_tests"></span><span id="human_interference_tests"></span><span id="HUMAN_INTERFERENCE_TESTS"></span>Human interference tests

Antenna positioning should take human interference into account. When the system is held in common states, GPS should not lose a location fix, should not increase the error radius more than 30%, and should maintain OTA acquisition sensitivity at -140 dBm and OTA tracking sensitivity of -145 dBm.

Commonly used states for slates:

-   Hands on the sides, landscape orientation

-   Hand on bottom, landscape orientation

-   Hands on the sides, portrait orientation (start on left)

-   Hands on the bottom, portrait orientation (start on left)

-   Hands on the sides, portrait orientation (start on right)

-   Hands on the bottom, portrait orientation (start on right)

**Human interference impact on acquisition and tracking sensitivity**

**Description**: The device acquisition and tracking sensitivity should not cause performance to drop below the minimal acceptable standard when the device is held at specified handgrips.

**Run Steps**: Hold the device in common handheld positions. Check acquisition sensitivity and tracking sensitivity.

**Expected Result**: Tracking and acquisition sensitivity should not be impacted when the device is held in certain positions. The device should maintain OTA acquisition sensitivity at -140 dBm and OTA tracking sensitivity of -145 dBm.

## <span id="interop"></span><span id="INTEROP"></span>Interoperability tests


### <span id="Mobile_Broadband__Wi-Fi__and_GPS_interoperability"></span><span id="mobile_broadband__wi-fi__and_gps_interoperability"></span><span id="MOBILE_BROADBAND__WI-FI__AND_GPS_INTEROPERABILITY"></span>Mobile Broadband, Wi-Fi, and GPS interoperability

**Description**: Disabling mobile broadband or Wi-Fi device should not prevent GPS from functioning. Turning MB or Wi-Fi radio off should not prevent GPS from getting a location fix.

**Run Steps**:

-   Disable Mobile Broadband and confirm that GPS can still get a location fix. Re-enable Mobile Broadband.

    >[!NOTE]
    >  
    GPS devices that use device services is an exception; these devices should first go into SENSOR\_STATE\_INITIALIZING state and, after 30 seconds, should go into the SENSOR\_STATE\_NOT\_AVAILABLE state when Mobile Broadband is disabled

     

-   Disable Wi-Fi and confirm that GPS can still get a location fix.

-   Turn off Mobile Broadband Radio and confirm that GPS can still get a location fix.

-   Turn off Wi-Fi Radio and confirm that GPS can still get a location fix.

-   Remove the Mobile Broadband SIM and confirm that GPS can get a location fix.

**Expected Result**: For Mobile Broadband or Wi-Fi devices, radio and SIM state should not prevent GPS from functioning.

### <span id="Mobile_Broadband__Wi-Fi__Bluetooth__Near_Field_Communication__NFC___and_camera_interference"></span><span id="mobile_broadband__wi-fi__bluetooth__near_field_communication__nfc___and_camera_interference"></span><span id="MOBILE_BROADBAND__WI-FI__BLUETOOTH__NEAR_FIELD_COMMUNICATION__NFC___AND_CAMERA_INTERFERENCE"></span>Mobile Broadband, Wi-Fi, Bluetooth, Near Field Communication (NFC), and camera interference

Radios and other devices such as system cameras can interfere with the GPS. GPS devices commonly share the same module with Mobile Broadband, Wi-Fi and Bluetooth. GPS functionality should not be impacted by these devices.

**Description**: Simultaneous usage of Mobile Broadband, Wi-Fi, Bluetooth, and camera should not degrade the performance and functionality of the GPS device, or vice versa.

Execution Steps: Run basic functionality tests with Mobile Broadband, Wi-Fi, Bluetooth, and camera on and actively in use.

-   Perform a large download over a Mobile Broadband connection while using GPS. Monitor sensor state, error radius and signal strength and the event logs from SDT.

-   Perform a large download over a Wi-Fi connection while using GPS. Monitor sensor state, error radius and signal strength and the event logs from SDT.

-   Perform a Bluetooth file transfer while using GPS. Monitor sensor state, error radius and signal strength and the event logs from SDT.

-   Perform a Wi-Fi scan while using GPS. Monitor sensor state, error radius and signal strength and the event logs from SDT.

-   Perform a Mobile Broadband scan while using GPS. Monitor sensor state, error radius and signal strength and the event logs from SDT.

-   Perform a Bluetooth scan while using GPS. Monitor sensor state, error radius and signal strength and the event logs from SDT.

-   Record video while using GPS. Monitor sensor state, error radius and signal strength and the event logs from SDT.

-   Watch a movie over the Internet while using GPS. Monitor sensor state, error radius and signal strength and the event logs from SDT.

-   Perform an NFC data transfer (for example, transfer photos) for 5 minutes. Monitor sensor state, error radius and signal strength and the event logs from SDT.

**Expected Result**: GPS should function normally during the time that these devices are being used. Usage of these devices should not impact sensor state, error radius and signal strength negatively.

## <span id="drivetests"></span><span id="DRIVETESTS"></span>Drive tests


Manual drive testing occurs when the system is taken on a drive by using a predefined route that includes tunnels and areas with different multipath impact. During the drive, the system GPS data is captured by a test application and is compared to a reference GPS. At no time should the location that the system reports be +/- the error radius outside the location reported by the reference GPS. The average error radius should be &lt;= 30 meters.

Drive testing exercises real life conditions such as dynamic navigation accuracy, reacquisition after going through a tunnel, impact of multi-path signals, and atmospheric conditions.

The following functionality tests are run during drive testing:

-   State transitions are monitored and compared to reference GPS.

-   Latitude, longitude and altitude (if available) are monitored and compared to reference GPS. A visual map representation is used for easy comparison.

-   Speed and heading data are monitored and compared to reference GPS.

-   Acquisition time and reacquisition time after driving through tunnels are measured and compared to reference GPS.

-   Tracking sensitivity is monitored in multipath impact areas. Data report frequency and any interruptions on the data reports are monitored.

-   Dynamic navigation accuracy is monitored and compared to reference GPS by using visual map representations.

-   Device Plug and Play (PnP) and radio manager state transitions are performed during dynamic navigation.

-   Report intervals are monitored and compared to reference GPS.

## <span id="simtests"></span><span id="SIMTESTS"></span>Simulator tests


A GNSS simulator (Spirent GSS6700) is used to achieve controlled lab conditions. It replays same test scenarios for repetition, simulates satellite states, various locations, and time such as south of equator and 2 years later, simulates in vehicle navigation, atmospheric conditions, multi-path signals, and error conditions. The standard Spirent GSS6700 simulator test scenarios are run.

An OTA RF connection tests the system together with original antenna and shielding. Direct connection can also be used when an antenna connector is accessible for receiver testing. Simulator testing focuses on common simulator scenarios, including GNSS receiver performance characteristics and the following scenarios:

-   Cold-start TTFF

-   Hot-start TTFF

-   Acquisition sensitivity

-   Re-acquisition sensitivity

-   Tracking sensitivity

-   Static position accuracy

-   Dynamic position accuracy

-   Multipath

-   GPS and Globalnaya navigatsionnaya sputnikovaya sistema (GLONASS)

## <span id="matrix"></span><span id="MATRIX"></span>GPS acceptance test matrix


-   OS build tests run on:

-   Windows HLK version:

-   Platform firmware version:

-   Platform tests run on:

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Test level</th>
<th>Test description</th>
<th>Verification results</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>Driver must be signed with the IHV certificate</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>Driver must be installed by using device manager/ Deployment Image Servicing and Management (DISM)</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Robustness.Driver Verifier, WDF Verifier and Application Verifier</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>Location Sensor WHLK tests: Device.Input.Sensor.*System tests for Location Sensors: System.Client.Sensor.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>Radio Management WHLK tests: System.Client.RadioManagement.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>In addition to required WHLK tests, Optional WHLK tests under Location Sensor WHLK tests: Device.Input.Sensor.* and System.Client.Sensor.* must run and pass for non-ARM SoC systems</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>Device Fundamentals WHLK tests: Device.DevFund.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>USB WHLK tests (USB connected devices only): Device.Connectivity.UsbDevices.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Functionality.Sensor category, type, properties and data fields</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Functionality.State Transitions</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Functionality.Accuracy of Latitude and Longitude</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Functionality.Speed Data</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Functionality.Heading Data</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Assisted GPS.A-GPS</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Assisted GPS.Position Injection. Connection Type</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Antenna Performance.OTA Connection. The device should get a location fix in clear sky outdoors as is without using external antennas or other modifications.</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Interoperability.* (GPS can get a location fix when Mobile Broadband, Bluetooth, Wi-Fi, or camera is in active use)</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Functionality.Other Sensor Properties</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Assisted GPS.Position Injection. Connection Time</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Basic (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Antenna Performance.HumanInterference Tests. Device should get a location fix in clear sky outdoors as is without any external antennas or other modifications, while it is held in common handheld positions.</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Stress (Level 2)</p></td>
<td><p>GPS.Test Descriptions.Robustness.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Performance (Level 2)</p></td>
<td><p>GPS.Test Descriptions.Performance.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Power (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Power Consumption.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Power (Level 1)</p></td>
<td><p>GPS.Test Descriptions.Power Management.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Antenna Performance (Level 1 for OEM)</p></td>
<td><p>GPS.Test Descriptions.Antenna Performance.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Drive Tests (Level 3)</p></td>
<td><p>GPS.Test Descriptions.Drive Tests.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Simulator Tests (Level 4)</p></td>
<td><p>GPS.Test Descriptions.Simulator Tests.*</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <span id="related_topics"></span>Related topics


[Windows Sensor and Location Platform](http://go.microsoft.com/fwlink/?LinkID=288838)

[Location driver guidelines for power and performance](http://go.microsoft.com/fwlink/?LinkID=288847)

[Writing a location sensor driver](http://go.microsoft.com/fwlink/?LinkID=28884)

[Filtering data](http://go.microsoft.com/fwlink/?LinkID=288848)

[Sensor Device Testing Prerequisites](sensor-device-testing-prerequisites.md)

 

 







