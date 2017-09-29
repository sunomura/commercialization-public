---
title: Troubleshooting Device.Input Testing
description: Troubleshooting Device.Input Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: af8b3b3b-3263-4739-9e38-2d53232b6259
---

# Troubleshooting Device.Input Testing


To troubleshoot issues that occur with Device.input tests, follow these steps:

1.  Review [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

2.  Review one of the following topics, depending on the type of input device that you are testing:

    -   [Fingerprint Reader Testing Prerequisites](fingerprint-reader-testing-prerequisites.md)

    -   [Game Controller Testing Prerequisites](game-controller-testing-prerequisites.md)

    -   [Keyboard Testing Prerequisites](keyboard-testing-prerequisites.md)

    -   [Mouse or other Pointing Device Testing Prerequisites](mouse-or-other-pointing-device-testing-prerequisites.md)

    -   [Sensor Device Testing Prerequisites](sensor-device-testing-prerequisites.md)

    -   [Smart Card Reader Testing Prerequisites](smart-card-reader-testing-prerequisites.md)

3.  Review the [Windows HLK release notes](http://go.microsoft.com/fwlink/?LinkID=236110) for current test issues.

4.  For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

### <span id="Specific_information_about_keyboard_tests"></span><span id="specific_information_about_keyboard_tests"></span><span id="SPECIFIC_INFORMATION_ABOUT_KEYBOARD_TESTS"></span>Specific information about keyboard tests

The Device.Input test category does not include specific keyboard tests. However, there are tests in the Device.Fundamentals category that apply to keyboards. For more information, see [Device.DevFund Tests](device-devfund-tests.md).

### <span id="Specific_information_about_mouse_or_other_pointing_device_tests"></span><span id="specific_information_about_mouse_or_other_pointing_device_tests"></span><span id="SPECIFIC_INFORMATION_ABOUT_MOUSE_OR_OTHER_POINTING_DEVICE_TESTS"></span>Specific information about mouse or other pointing device tests

The Device.Input test category does not include specific mouse tests. However, the Device.Fundamentals category includes tests that apply to mice.

### <span id="Specific_information_about_sensor_device_tests"></span><span id="specific_information_about_sensor_device_tests"></span><span id="SPECIFIC_INFORMATION_ABOUT_SENSOR_DEVICE_TESTS"></span>Specific information about sensor device tests

Currently, known sensor test issues are grouped into the following categories:

-   Test initialization failures

-   Operating system issues

-   Permissions issues

**Test initialization failures**

When the sensor tests start on a test computer, they perform several tests to verify that the environment can be used for testing. If you receive errors that have a TUID of A012D6BB-36BB-4088-AF3F-1BE3C5607928, verify the following:

-   The test computer must be running Windows 8 or Windows 7.

-   The test computer must currently have your test sensor device installed and the device must be operational.

-   The test sensor device must appear as a sensor device in the **Location and Other Sensors** Control Panel.

**Operating system issues**

The sensor tests are only valid on Windows 8 and Windows 7. The tests are not supported on any other version of Windows.

**Permissions issues**

The user who is logged into the client computer must have permissions to access the sensor device for some of the sensor logo tests. To check permissions, follow these steps:

1.  Open the **Location and Other Sensors** Control Panel.

2.  Grant all users access to the sensor device that is being tested. To do this, follow these steps:

    1.  In the **Location and Other Sensors** Control Panel, select the check box next to the sensor device that is being tested.

    2.  Click **Apply**.

>[!NOTE]
>  
You must have administrator permissions on the test system to change the permissions for the sensor test device.

 

## <span id="related_topics"></span>Related topics


[Device.Input Tests](device-input-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







