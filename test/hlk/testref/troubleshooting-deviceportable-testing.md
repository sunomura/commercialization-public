---
title: Troubleshooting Device.Portable Testing
description: Troubleshooting Device.Portable Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 05f3b097-bc9a-499e-a5a2-31e12c88c8ae
---

# Troubleshooting Device.Portable Testing


To troubleshoot issues that occur with Device.Portable tests, follow these steps:

1.  Review the following Windows Hardware Lab Kit (Windows HLK) topics:

    -   [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md)

    -   [Device.Portable Testing Prerequisites](deviceportable-testing-prerequisites.md)

2.  Make sure that the device appears in **Device Manager** under **Portable Devices**.

3.  Some tests require that you log on to the computer as an Administrator. An Administrator account is needed if a test uses a test driver and then needs to revert to the original driver.

4.  Verify that you have installed the latest Windows HLK filters and kit updates. For more information, see [Windows Hardware Lab Kit Filters](..\user\windows-hardware-lab-kit-filters.md).

5.  For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

6.  If you cannot obtain a successful test result, contact [Windows HLK Support](..\user\windows-hlk-support.md).

## <span id="related_topics"></span>Related topics


[Device.Portable Tests](device-portable-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







