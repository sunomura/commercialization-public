---
title: How to run HLK Motion Sensor Tests
description: How to run HLK Motion Sensor Tests
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 55de9db6-c5a9-4ee2-9a1c-3bad34d23ffd
---

# How to run HLK Motion Sensor Tests


## <span id="Introduction"></span><span id="introduction"></span><span id="INTRODUCTION"></span>Introduction


This document is a guide or a supplement to the existing HLK 2.0 documentation and tools for sensors OEMs, ODMs and IHVs. It provides some tips and tricks that a partner can leverage to run the tests. Partners are free to use other implementations to test their device-- this is just a singular reference. Items identified in this document are optional (you can run the tests without these pieces of hardware). They have simply been used to help demonstrate the orientations for the purposes of this document.

This document assumes that the HLK 2.0 or greater is being used to test a tablet form factor system (requiring motion and light sensors). Other form factors (e.g. laptops) are beyond the scope of this document. Although the tests do validate other form factor systems, the details below are primarily designed to optimize testing on tablet form factor systems.

This document describes the following tests:

-   [Verify Sensor Orientation – 3D Accelerometer](#accel)

-   [Gyroscope Sensor Test](#gyro)

-   [Verify Sensor Orientation – 3D Compass](#compass)

-   [Verify Sensor Orientation – Inclinometer](#inclin)

-   [Verify Advanced Orientation Sensors](#advor)

The motion sensor tests are required for the following:

-   Sensor device certification

-   System certification

The motivation to have **identical** tests in both of these areas is to ensure that IHVs provide passing hardware, firmware, and drivers to PC manufacturers and that PC manufacturers integrate the parts correctly onto their systems to provide accurate and reliable sensor readings.

### <span id="Test_Purpose"></span><span id="test_purpose"></span><span id="TEST_PURPOSE"></span>Test Purpose

The primary purpose of the motion sensor tests is to assist hardware partners in validating that their sensors are correctly orientated in the system and that they meet the WHLK required accuracy requirements. These tests are not designed to provide full test coverage or to take advantage of specialized equipment that can more accurately determine the inaccuracies of individual sensors. It is recommended that PC manufacturers to test their systems with additional applications and quality assurance tests after passing WHLK (e.g. test with production-quality Windows 8 apps).

### <span id="Recommended_Testing_Sequence"></span><span id="recommended_testing_sequence"></span><span id="RECOMMENDED_TESTING_SEQUENCE"></span>Recommended Testing Sequence

Microsoft recommends that you run the tests in the order that is listed in the following table. By testing the accelerometer and gyroscope first, you can ensure that these basic sensors are working correctly. The next set of tests validates the data from Compass, Inclinometer, and Orientation sensors that are derived by combining data of multiple sensors. It is also recommended not to attempt to execute subsequent tests until all previous tests are passing.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Sensor</th>
<th>Test Name</th>
<th>Dependencies</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Accelerometer</p></td>
<td><p>Verify Sensor Orientation – 3D Accelerometer</p></td>
<td><p>n/a</p></td>
</tr>
<tr class="even">
<td><p>Gyroscope</p></td>
<td><p>Gyroscope Sensor Test</p>
<p></p></td>
<td><p>n/a</p></td>
</tr>
<tr class="odd">
<td><p>Compass</p></td>
<td><p>Verify Sensor Orientation – 3D Compass</p></td>
<td><p>Accelerometer, Gyro, Compass</p></td>
</tr>
<tr class="even">
<td><p>Inclinometer</p></td>
<td><p>Verify Sensor Orientation – Inclinometer</p></td>
<td><p>Accelerometer, Gyro, Compass</p></td>
</tr>
<tr class="odd">
<td><p>Fusion/Orientation Sensors (Rotation Matrix / Quaternion)</p></td>
<td><p>Verify Advanced Orientation Sensors</p></td>
<td><p>Accelerometer, Gyro, Compass</p></td>
</tr>
</tbody>
</table>

 

### <span id="equip"></span><span id="EQUIP"></span>Suggested Test Equipment

For the purposes of this document, the following hardware items were utilized to help run the WHLK tests. While these devices are not required for WHLK, they may assist the validation engineer get through the tests more easily if used.

![suggested test equipment](images/fig1-suggested-test-equipment.jpg)

**Figure 1 Suggested Test Equipment**

-   Bluetooth keyboard

-   Bluetooth mouse

-   Compass / GPS

-   Clamp and tape to hold system

-   Revolving turn-table (for example, a Lazy Susan)

-   Sensor Diagnostic Tool

These additional devices help test a tablet form factor system (where accelerometer, gyro, compass, inclinometer and orientation sensors are required). For other configurations, these tools may not apply. The remainder of this document will only focus on tablet and not other form factors.

The sensor diagnostic tool (sensordiagnostictool.exe available in the WDK) is useful for debugging test failures. This tool will show the data being returned in real-time from the various motion sensors which can be compared to the expected results.

## <span id="accel"></span><span id="ACCEL"></span>Verify Sensor Orientation – 3D Accelerometer


Test Scope: This test verifies the accelerometer is correctly orientated in the system. The tests have an error tolerance of +/- 0.1 G.

Prerequisites before running this test:

1.  Manually verify that screen autorotation works as expected.

2.  Use SDT and validate that the sensors do not show new data events when sitting stationary.

Once these simple prerequisites pass, proceed to run the WHLK test. Should you run into errors with the tests, ensure that the device is in the correct orientation as per this document. PC manufacturers with questions should first contact their sensor manufacturer (IHV) to identify how they passed the WHLK tests before contacting Microsoft for assistance with WHLK tests.

### <span id="Accelerometer_Test_1"></span><span id="accelerometer_test_1"></span><span id="ACCELEROMETER_TEST_1"></span>Accelerometer Test 1

Hold the device perpendicular to a flat and level surface with the Windows button on the bottom.

Expected values:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_X_G</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_Y_G</p></td>
<td><p>-1</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_Z_G</p></td>
<td><p>0</p></td>
</tr>
</tbody>
</table>

 

![accelerometer test 1](images/fig2-accelerometer-test-1.jpg)

**Figure 2 Accelerometer Test 1**

### <span id="Accelerometer_Test_2"></span><span id="accelerometer_test_2"></span><span id="ACCELEROMETER_TEST_2"></span>Accelerometer Test 2

Rotate device 90 degrees clockwise, keeping the device perpendicular to the flat and level surface. The Windows button should be on the left.

Expected values:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_X_G</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_Y_G</p></td>
<td><p>0</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_Z_G</p></td>
<td><p>0</p></td>
</tr>
</tbody>
</table>

 

![accelerometer test 2](images/fig3-accelerometer-test-2.jpg)

**Figure 3 Accelerometer Test 2**

### <span id="Accelerometer_Test_3"></span><span id="accelerometer_test_3"></span><span id="ACCELEROMETER_TEST_3"></span>Accelerometer Test 3

Now lay the device flat, with the windows button away from you.

Expected values:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_X_G</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_Y_G</p></td>
<td><p>0</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_Z_G</p></td>
<td><p>-1</p></td>
</tr>
</tbody>
</table>

 

![accelerometer test 3](images/fig4-accelerometer-test-3.jpg)

**Figure 4 Accelerometer Test 3**

### <span id="Accelerometer_Test_4"></span><span id="accelerometer_test_4"></span><span id="ACCELEROMETER_TEST_4"></span>Accelerometer Test 4

Now flip the device over, so the screen is face down.

Expected values:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_X_G</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_Y_G</p></td>
<td><p>0</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ACCELERATION_Z_G</p></td>
<td><p>1</p></td>
</tr>
</tbody>
</table>

 

![accelerometer test 4](images/fig5-accelerometer-test-4.jpg)

**Figure 5 Accelerometer Test 4**

## <span id="gyro"></span><span id="GYRO"></span>Gyroscope Sensor Test


Test Scope:

Gyroscopes generally emit noise on the magnitude of +/- 2 degrees per second. Prior to running the Gyroscope verification tests, testers should use the sensor diagnostic tool to validate the gyroscope sensor is not generating values greater than 2 degrees per second when the system is stationary.

Prerequisites before running this test:

1.  Accelerometer tests pass.

2.  Use SDT, and validate that the sensors do not return data when sitting stationary on a flat surface.

If the gyroscope sensor is generating excessive noise, testers should work with the sensor manufacturer to understand and fix the source of the noise.

Gyro tests expect to receive an angular velocity of greater than 40 degrees per second on the axis being rotated and less than 15 degrees per second on the stationary axes. To achieve passing results, testers will likely find that the system can be rotated on a turntable to keep the other two axes stationary. Note the system should also be centered on the turntable to prevent movement on other axes from detecting rotation.

### <span id="Gyro_Test_1"></span><span id="gyro_test_1"></span><span id="GYRO_TEST_1"></span>Gyro Test 1

Lay the device flat with the screen up. Rotate the device clockwise.

Expected values during rotation:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_X_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Y_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Z_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; -40</p></td>
</tr>
</tbody>
</table>

 

![gyro test 1](images/fig6-gyro-test-1.jpg)

**Figure 6 Gyro Test 1**

### <span id="Gyro_Test_2"></span><span id="gyro_test_2"></span><span id="GYRO_TEST_2"></span>Gyro Test 2

Lay the device flat with the screen up. Rotate the device counterclockwise.

Expected Values during rotation:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_X_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Y_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Z_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&gt; 40</p></td>
</tr>
</tbody>
</table>

 

![gyro test 2](images/fig7-gyro-test-2.jpg)

**Figure 7 Gyro Test 2**

### <span id="Gyro_Test_3"></span><span id="gyro_test_3"></span><span id="GYRO_TEST_3"></span>Gyro Test 3

Hold the device vertical with the windows button on the bottom. Looking down on the device, rotate the device clockwise along the axis between the top of the screen and the windows button.

Expected values during rotation:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_X_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Y_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; -40</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Z_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
</tbody>
</table>

 

![gyro test 3](images/fig8-gyro-test-3.jpg)

**Figure 8 Gyro Test 3**

### <span id="Gyro_Test_4"></span><span id="gyro_test_4"></span><span id="GYRO_TEST_4"></span>Gyro Test 4

Hold the device vertical with the windows button on the bottom. Looking down on the device, rotate the device counterclockwise along the axis between the top of the screen and the windows button.

Expected values during rotation:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_X_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Y_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&gt; 40</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Z_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
</tbody>
</table>

 

![gyro test 4](images/fig9-gyro-test-4.jpg)

**Figure 9 Gyro Test 4**

### <span id="Gyro_Test_5"></span><span id="gyro_test_5"></span><span id="GYRO_TEST_5"></span>Gyro Test 5

Hold the device vertical with the windows button on the left. Looking down on the device, rotate the device clockwise keeping the device vertical and in the portrait orientation.

Expected values during rotation:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_X_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&gt; 40</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Y_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Z_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
</tbody>
</table>

 

![gyro test 5](images/fig10-gyro-test-5.jpg)

**Figure 10 Gyro Test 5**

### <span id="Gyro_Test_6"></span><span id="gyro_test_6"></span><span id="GYRO_TEST_6"></span>Gyro Test 6

Hold the device vertical with the windows button on the left. Looking down on the device, rotate the device counterclockwise keeping the device vertical and in the portrait orientation.

Expected values during rotation:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_X_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt;-40</p></td>
</tr>
<tr class="even">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Y_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
<tr class="odd">
<td><p>SENSOR_DATA_TYPE_ANGULAR_ACCELERATION_Z_DEGREES_PER_SECOND_SQUARED</p></td>
<td><p>&lt; 15</p></td>
</tr>
</tbody>
</table>

 

![gyro test 6](images/fig11-gyro-test-6.jpg)

**Figure 11 Gyro Test 6**

## <span id="compass"></span><span id="COMPASS"></span>Verify Sensor Orientation – 3D Compass


Most compass implementations use data from both the 3D magnetometer and the gyro to calculate the current direction the user is facing relative to the magnetic north pole. Some implementations also use data from the accelerometer. Therefore, if the gyroscope or accelerometer sensor is not functioning properly, testers should expect to see the compass return incorrect headings.

Since the earth’s magnetic force is relatively weak, the magnetometer sensors will often be subject to interference from other components inside the system. If the magnetometers are not adequately isolated from sources of electromagnetic interference such as antennas, power lines, or other components that are composed of materials such as iron that interfere with magnetic reception, testers will find that the compass will return incorrect headings. Please refer to the [Integrating Motion and Orientation Sensors whitepaper](http://go.microsoft.com/fwlink/?LinkId=262274) for guidance on correct magnetometer placement and best practices.

The user is strongly encouraged to stand holding the system at various angles and rotate themselves so they end up facing different directions. Regardless of the angle the system is being held, or landscape / portrait orientation, the compass should always return the heading that is relative to the direction that the user is facing. Note that sensor diagnostic tool can be used to display the heading value from the compass sensor. If testers find out that the compass is returning incorrect or inconsistent results, please work with the magnetometer sensor vendor to determine if the error is a result of interference or potentially an incorrect sensor fusion algorithm.

The compass tests in the WHLK validate that the compass returns expected values when the system is held at different directions and orientations. The compass tests allow for an error tolerance of +/- 10 degrees. Testers should use a reference compass to determine the direction of magnetic north prior to starting the compass test.

### <span id="Compass_Test_1"></span><span id="compass_test_1"></span><span id="COMPASS_TEST_1"></span>Compass Test 1

Lay the device on a flat surface with the Windows button pointing due south.

The compass should return a heading near 0 degrees.

>[!NOTE]
>  
Ignore the logging exception text. This will not cause a failure to be logged.

 

![compass test 1](images/fig12-compass-test-1.jpg)

**Figure 12 Compass Test 1**

### <span id="Compass_Test_2"></span><span id="compass_test_2"></span><span id="COMPASS_TEST_2"></span>Compass Test 2

Now hold the device vertical with the Windows button on the bottom, with the screen towards you. Aim the Windows button due north.

The compass should return a heading near 0 degrees

![compass test 2](images/fig13-compass-test-2.jpg)

**Figure 13 Compass Test 2**

### <span id="Compass_Test_3"></span><span id="compass_test_3"></span><span id="COMPASS_TEST_3"></span>Compass Test 3

Now lay the device flat, screen down with the windows button pointing due south.

The compass should return a heading near 0 degrees.

![compass test 3](images/fig14-compass-test-3.jpg)

**Figure 14 Compass Test 3**

### <span id="Compass_Test_4"></span><span id="compass_test_4"></span><span id="COMPASS_TEST_4"></span>Compass Test 4

Now rotate the screen 90 degrees clockwise so the Windows button is pointing due West.

The compass should return a heading near 90 degrees.

![compass test 4](images/fig15-compass-test-4.jpg)

**Figure 15 Compass Test 4**

### <span id="Compass_Test_5"></span><span id="compass_test_5"></span><span id="COMPASS_TEST_5"></span>Compass Test 5

Rotate the screen another 90 degrees clockwise so the Windows button is pointing due North.

The compass should return a heading near 180 degrees.

![compass test 5](images/fig16-compass-test-5.jpg)

**Figure 16 Compass Test 5**

### <span id="Compass_Test_6"></span><span id="compass_test_6"></span><span id="COMPASS_TEST_6"></span>Compass Test 6

Rotate the screen another 90 degrees clockwise so the Windows button is pointing due East.

The compass should return a value near 270 degrees.

![compass test 6](images/fig17-compass-test-6.jpg)

**Figure 17 Compass Test 6**

## <span id="inclin"></span><span id="INCLIN"></span>Verify Sensor Orientation – Inclinometer


Based on the guidance in the [Integrating Motion and Orientation Sensors whitepaper](http://go.microsoft.com/fwlink/?LinkId=262274), the inclinometer implementation could use data from the accelerometer, gyroscope and compass to determine the Euler angle values.

The tests will allow for angle errors of +/- 10 degrees.

>[!IMPORTANT]
>  
Please refer to the Validation of Euler Angles section of the Integrating Motion and Orientation Sensors whitepaper for the expected angles for each of the inclinometer tests.

 

### <span id="Inclinometer_Test_1"></span><span id="inclinometer_test_1"></span><span id="INCLINOMETER_TEST_1"></span>Inclinometer Test 1

Place the device on a flat and level surface with the windows button pointing due SOUTH.

![inclinometer test 1](images/fig18-inclinometer-test-1.jpg)

**Figure 18 Inclinometer Test 1**

### <span id="Inclinometer_Test_2"></span><span id="inclinometer_test_2"></span><span id="INCLINOMETER_TEST_2"></span>Inclinometer Test 2

Place the device on a flat and level surface with the windows button pointing due EAST.

![inclinometer test 2](images/fig19-inclinometer-test-2.jpg)

**Figure 19 Inclinometer Test 2**

### <span id="Inclinometer_Test_3"></span><span id="inclinometer_test_3"></span><span id="INCLINOMETER_TEST_3"></span>Inclinometer Test 3

Place the device on a flat and level surface with the windows button pointing due NORTH.

![inclinometer test 3](images/fig20-inclinometer-test-3.jpg)

**Figure 20 Inclinometer Test 3**

### <span id="Inclinometer_Test_4"></span><span id="inclinometer_test_4"></span><span id="INCLINOMETER_TEST_4"></span>Inclinometer Test 4

Place the device on a flat and level surface with the windows button pointing due WEST.

![inclinometer test 4](images/fig21-inclinometer-test-4.jpg)

**Figure 21 Inclinometer Test 4**

### <span id="Inclinometer_Test_5"></span><span id="inclinometer_test_5"></span><span id="INCLINOMETER_TEST_5"></span>Inclinometer Test 5

Place the device on a flat and level surface face up with the windows button pointing due SOUTH.

![inclinometer test 5](images/fig22-inclinometer-test-5.jpg)

**Figure 22 Inclinometer Test 5**

### <span id="Inclinometer_Test_6"></span><span id="inclinometer_test_6"></span><span id="INCLINOMETER_TEST_6"></span>Inclinometer Test 6

Hold the device vertically against a flat and level surface so the windows button is on the bottom, the +Y axis points straight up and the screen is facing due SOUTH.

![inclinometer test 6](images/fig23-inclinometer-test-6.jpg)

**Figure 23 Inclinometer Test 6**

### <span id="Inclinometer_Test_7"></span><span id="inclinometer_test_7"></span><span id="INCLINOMETER_TEST_7"></span>Inclinometer Test 7

Place the device on a flat and level surface face down so the windows button is pointing due NORTH.

![inclinometer test 7](images/fig24-inclinometer-test-7.jpg)

**Figure 24 Inclinometer Test 7**

### <span id="Inclinometer_Test_8"></span><span id="inclinometer_test_8"></span><span id="INCLINOMETER_TEST_8"></span>Inclinometer Test 8

Hold the device vertically against a flat and level surface so the windows button is on the top, the +Y axis points straight down and the screen is facing due NORTH.

![inclinometer test 8](images/fig25-inclinometer-test-8.jpg)

**Figure 25 Inclinometer Test 8**

### <span id="Inclinometer_Test_9"></span><span id="inclinometer_test_9"></span><span id="INCLINOMETER_TEST_9"></span>Inclinometer Test 9

Place the device on a flat and level surface face up with the windows button pointing due SOUTH.

![inclinometer test 9](images/fig26-inclinometer-test-9.jpg)

**Figure 26 Inclinometer Test 9**

### <span id="Inclinometer_Test_10"></span><span id="inclinometer_test_10"></span><span id="INCLINOMETER_TEST_10"></span>Inclinometer Test 10

Hold the device vertically against a flat and level surface on its right side so the screen is pointing due EAST.

![inclinometer test 10](images/fig27-inclinometer-test-10.jpg)

**Figure 27 Inclinometer Test 10**

### <span id="Inclinometer_Test_11"></span><span id="inclinometer_test_11"></span><span id="INCLINOMETER_TEST_11"></span>Inclinometer Test 11

Place the device on a flat and level surface face down with the windows button pointing due SOUTH.

![inclinometer test 11](images/fig28-inclinometer-test-11.jpg)

**Figure 28 Inclinometer Test 11**

### <span id="Inclinometer_Test_12"></span><span id="inclinometer_test_12"></span><span id="INCLINOMETER_TEST_12"></span>Inclinometer Test 12

Hold the device vertically against a flat and level surface on its left side so the screen is pointing due WEST.

![inclinometer test 12](images/fig29-inclinometer-test-12.jpg)

**Figure 29 Inclinometer Test 12**

## <span id="advor"></span><span id="ADVOR"></span>Verify Advanced Orientation Sensors


Most rotation matrix and quaternion implementations will use data derived from both the accelerometer and compass to determine rotation matrix and quaternion values. Testers are recommended to first validate accelerometer and compass values before attempting to run the advanced orientation tests.

The tests use dot products to compute the delta between the expected vector and the vector retrieved from the advanced orientation sensors. The tests allow for a delta of up to 15 degrees. If testers find that the sensor is returning different values than what the test expects then the orientation fusion algorithm should be reviewed to see that it produces consistent results with the values given in the [Integrating Motion and Orientation Sensors whitepaper](http://go.microsoft.com/fwlink/?LinkId=262274).

>[!IMPORTANT]
>  
Please refer to the Validation of Euler Angles section of the Integrating Motion and Orientation Sensors whitepaper for the expected quaternion and rotation matrix values.

 

### <span id="Advanced_Orientation_Sensor_Test_1"></span><span id="advanced_orientation_sensor_test_1"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_1"></span>Advanced Orientation Sensor Test 1

Place device on a flat level surface, screen up with the windows button pointing due SOUTH.

![advanced orientation sensor test 1](images/fig30-adv-orientation-sensor-test-1.jpg)

**Figure 30 Advanced Orientation Sensor Test 1**

### <span id="Advanced_Orientation_Sensor_Test_2"></span><span id="advanced_orientation_sensor_test_2"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_2"></span>Advanced Orientation Sensor Test 2

Place device on a flat level surface, screen up with the windows button pointing due EAST.

![advanced orientation sensor test 2](images/fig31-adv-orientation-sensor-test-2.jpg)

**Figure 31 Advanced Orientation Sensor Test 2**

### <span id="Advanced_Orientation_Sensor_Test_3"></span><span id="advanced_orientation_sensor_test_3"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_3"></span>Advanced Orientation Sensor Test 3

Place device on a flat level surface, screen up with the windows button pointing due NORTH.

![advanced orientation sensor test 3](images/fig32-adv-orientation-sensor-test-3.jpg)

**Figure 32 Advanced Orientation Sensor Test 3**

### <span id="Advanced_Orientation_Sensor_Test_4"></span><span id="advanced_orientation_sensor_test_4"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_4"></span>Advanced Orientation Sensor Test 4

Place device on a flat level surface, screen up with the windows button pointing due WEST.

![advanced orientation sensor test 4](images/fig33-adv-orientation-sensor-test-4.jpg)

**Figure 33 Advanced Orientation Sensor Test 4**

### <span id="Advanced_Orientation_Sensor_Test_5"></span><span id="advanced_orientation_sensor_test_5"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_5"></span>Advanced Orientation Sensor Test 5

Place device on a flat level surface, screen up with the windows button pointing due SOUTH.

![advanced orientation sensor test 5](images/fig34-adv-orientation-sensor-test-5.jpg)

**Figure 34 Advanced Orientation Sensor Test 5**

### <span id="Advanced_Orientation_Sensor_Test_6"></span><span id="advanced_orientation_sensor_test_6"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_6"></span>Advanced Orientation Sensor Test 6

Hold the device vertically with the windows button on the bottom and the windows button pointing due SOUTH.

![advanced orientation sensor test 6](images/fig35-adv-orientation-sensor-test-6.jpg)

**Figure 35 Advanced Orientation Sensor Test 6**

### <span id="Advanced_Orientation_Sensor_Test_7"></span><span id="advanced_orientation_sensor_test_7"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_7"></span>Advanced Orientation Sensor Test 7

Place the device on a flat level surface with screen down and the windows button pointing due NORTH.

![advanced orientation sensor test 7](images/fig36-adv-orientation-sensor-test-7.jpg)

**Figure 36 Advanced Orientation Sensor Test 7**

### <span id="Advanced_Orientation_Sensor_Test_8"></span><span id="advanced_orientation_sensor_test_8"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_8"></span>Advanced Orientation Sensor Test 8

Place the device on a flat level surface with screen down and the windows button pointing due NORTH.

![advanced orientation sensor test 8](images/fig37-adv-orientation-sensor-test-8.jpg)

**Figure 37 Advanced Orientation Sensor Test 8**

### <span id="Advanced_Orientation_Sensor_Test_9"></span><span id="advanced_orientation_sensor_test_9"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_9"></span>Advanced Orientation Sensor Test 9

Place device on a flat level surface, screen up with the windows button pointing due SOUTH.

![advanced orientation sensor test 9](images/fig38-adv-orientation-sensor-test-9.jpg)

**Figure 38 Advanced Orientation Sensor Test 9**

### <span id="Advanced_Orientation_Sensor_Test_10"></span><span id="advanced_orientation_sensor_test_10"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_10"></span>Advanced Orientation Sensor Test 10

Hold the device vertically with the windows button on the side, left side on top, and the windows button pointing due EAST.

![advanced orientation sensor test 10](images/fig39-adv-orientation-sensor-test-10.jpg)

**Figure 39 Advanced Orientation Sensor Test 10**

### <span id="Advanced_Orientation_Sensor_Test_11"></span><span id="advanced_orientation_sensor_test_11"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_11"></span>Advanced Orientation Sensor Test 11

Place the device on a flat level surface with screen down and the windows button pointing due SOUTH.

![advanced orientation sensor test 11](images/fig40-adv-orientation-sensor-test-11.jpg)

**Figure 40 Advanced Orientation Sensor Test 11**

### <span id="Advanced_Orientation_Sensor_Test_12"></span><span id="advanced_orientation_sensor_test_12"></span><span id="ADVANCED_ORIENTATION_SENSOR_TEST_12"></span>Advanced Orientation Sensor Test 12

Hold the device vertically with the windows button on the side, left side on bottom, and the windows button pointing due WEST.

![advanced orientation sensor test 12](images/fig41-adv-orientation-sensor-test-12.jpg)

**Figure 41 Advanced Orientation Sensor Test 12**

 

 






