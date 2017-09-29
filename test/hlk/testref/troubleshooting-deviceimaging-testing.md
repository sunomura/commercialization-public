---
title: Troubleshooting Device.Imaging Testing
description: Troubleshooting Device.Imaging Testing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d4903340-2c4e-485c-9dc2-ada99d5e5a0d
---

# Troubleshooting Device.Imaging Testing


To troubleshoot issues that occur with Device.imaging tests, follow these steps:

1.  Review [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

2.  Review one of the following topics, depending on whether you are testing a printer or a scanner

    -   [Printer Testing Prerequisites](printer-testing-prerequisites.md)

    -   [Scanner Testing Prerequisites](scanner-testing-prerequisites.md)

    -   [Web Services on Devices Testing Prerequisites](web-services-on-devices-testing-prerequisites.md)

3.  Review the [Windows HLK release notes](http://go.microsoft.com/fwlink/?LinkID=236110) for current test issues.

4.  For a test failure, look for usable information in the Windows HLK Studio test log. If you find usable information, resolve the issue and rerun the test.

### <span id="Specific_printer_test_information"></span><span id="specific_printer_test_information"></span><span id="SPECIFIC_PRINTER_TEST_INFORMATION"></span>Specific printer test information

When testing your printer over TCP/IP, if the Device.Imaging.Printer.Base feature is not being detected, you may need to go to the **Device Manager** view under **Selection** and manually select all of the devnodes that correspond to the print device.

## <span id="related_topics"></span>Related topics


[Device.Imaging Tests](device-imaging-tests.md)

[Troubleshooting Windows HLK](..\user\troubleshooting-windows-hlk.md)

 

 







