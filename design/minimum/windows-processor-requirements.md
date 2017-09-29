---
title: Windows Processor Requirements
description: This specification details the processors that can be used with Customer Systems that include Windows Products (including Custom Images).
ms.author: sapaetsc
ms.date: 06/15/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Windows Processor Requirements

This specification details the processors that can be used with Customer Systems that include Windows Products (including Custom Images). Updates to this specification may be released in the future as requirements change.

For each listed edition, Company must use only the processors listed, as specified in the table below. The requirements below apply whenever the edition below is pre-installed or provided on external media, including as downgrade or down edition software.

For clarity, Company must also meet all processor and other requirements specified in Minimum Hardware Requirements for Windows 10, located at <https://msdn.microsoft.com/library/windows/hardware/dn915086(v=vs.85).aspx> (or updated URL).

If after the inclusion of a processor series in this specification (“Listed Processor”), a processor becomes commercially available that uses the same naming convention or identifier as a Listed Processor but has additional or different features or functionality (“New Processor”), Company must not use New Processor for Customer Systems without Microsoft’s prior written permission. If Company believes a processor has been omitted from this list, please contact Company’s Microsoft OEM or ODM Account Manager.

Some product editions or edition/processor configurations listed below may have no or limited support. Information on support is available at Microsoft Support Policy (<https://support.microsoft.com/en-us/lifecycle>) and Microsoft Lifecycle FAQ (<https://support.microsoft.com/en-us/help/18581>).

## Windows Client Edition Processor table

| Windows Edition                 | Intel Processors                                                                                                                                                                                       | AMD Processors                                                                                         |
|---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Windows 7 and earlier editions  | Up through the following Intel 6th Generation Processors (Intel Core i3/i5/i7-6xxx, Core m3/m5/m7-6xxx, and Xeon E3-xxxx v5) and through series equivalent Intel Atom, Celeron and Pentium Processors | Up through the following AMD 6th Generation Processors (A-Series Ax-8xxx & E-Series Ex-8xxx & FX-870K) |
| Windows 8.1                     | Up through the following Intel 6th Generation Processors (Intel Core i3/i5/i7-6xxx, Core m3/m5/m7-6xxx, and Xeon E3-xxxx v5) and through series equivalent Intel Atom, Celeron and Pentium Processors | Up through the following AMD 6th Generation Processors (A-Series Ax-8xxx & E-Series Ex-8xxx & FX-870K) |
| Windows 10 1507                 | Up through the following Intel 6th Generation Processors (Intel Core i3/i5/i7-6xxx, Core m3/m5/m7-6xxx, and Xeon E3-xxxx v5) and through series equivalent Intel Atom, Celeron and Pentium Processors | Up through the following AMD 6th Generation Processors (A-Series Ax-8xxx & E-Series Ex-8xxx & FX-870K) |
| Windows 10 Enterprise LTSB 2015 | Up through the following Intel 6th Generation Processors (Intel Core i3/i5/i7-6xxx, Core m3/m5/m7-6xxx, and Xeon E3-xxxx v5) and through series equivalent Intel Atom, Celeron and Pentium Processors | Up through the following AMD 6th Generation Processors (A-Series Ax-8xxx & E-Series Ex-8xxx & FX-870K) |
| Windows 10 1511                 | Up through the following Intel 7th Generation Processors (Intel Core i3/i5/i7-7xxx, Core m3-7xxx, and Xeon E3-xxxx v6) and through current Intel Atom, Celeron, and Pentium Processors                | Up through the following AMD 7th Generation Processors (A-Series Ax-9xxx & E-Series Ex-9xxx & FX-9xxx) |
| Windows 10 1607                 | Up through the following Intel 7th Generation Processors (Intel Core i3/i5/i7/i9-7xxx, Core m3-7xxx, and Xeon E3-xxxx v6) and through current Intel Atom, Celeron, and Pentium Processors             | Up through the following AMD 7th Generation Processors (A-Series Ax-9xxx & E-Series Ex-9xxx & FX-9xxx) |
| Windows 10 Enterprise LTSB 2016 | Up through the following Intel 7th Generation Processors (Intel Core i3/i5/i7/i9-7xxx, Core m3-7xxx, and Xeon E3-xxxx v6) and through current Intel Atom, Celeron, and Pentium Processors             | Up through the following AMD 7th Generation Processors (A-Series Ax-9xxx & E-Series Ex-9xxx & FX-9xxx) |
| Windows 10 1703                 | Up through the following Intel 7th Generation Processors (Intel Core i3/i5/i7/i9-7xxx, Core m3-7xxx, and Xeon E3-xxxx v6) and through current Intel Atom, Celeron, and Pentium Processors             | Up through the following AMD 7th Generation Processors (A-Series Ax-9xxx & E-Series Ex-9xxx & FX-9xxx), and AMD Ryzen 3/5/7 1xxx  |

## Windows IoT Core Processor table

| Windows Edition | Intel Processors                                                                 | Qualcomm Processor                                            | Broadcom                                           |
|-----------------|----------------------------------------------------------------------------------|---------------------------------------------------------------|----------------------------------------------------|
| Windows 10 1703 | Up through currently enabled Intel Joule, Atom, Celeron and Pentium Processors\* | Up through currently enabled Qualcomm Snapdragon Processors\* | Up through currently enabled Broadcom Processors\* |

\*Information on which processors are currently enabled is available at <https://developer.microsoft.com/en-us/windows/iot/explore/SoC>

## Windows IoT Enterprise / Embedded Processor table

| Windows Edition                                                                                             | Intel Processors                                                                                                                                                                                       | AMD Processors                                                                                         |
|-------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Windows Embedded Products (e.g., Windows Embedded Standard, Windows CE, POS Ready, 7 FES, 8.1 Industry Pro) | Up through the following Intel 6th Generation Processors (Intel Core i3/i5/i7-6xxxx, Core m3/m5/m7-6xxx, and Xeon E3-xxxx v5) and through series equivalent Intel Atom, Celeron and Pentium Processors | Up through the following AMD 6th Generation Processors (A-Series Ax-8xxx & E-Series Ex-8xxx & FX-870K) |
| Windows 10 Enterprise LTSB 2015                                                                             | Up through the following Intel 6th Generation Processors (Intel Core i3/i5/i7-6xxxx, Core m3/m5/m7-6xxx, and Xeon E3-xxxx v5) and through series equivalent Intel Atom, Celeron and Pentium Processors | Up through the following AMD 6th Generation Processors (A-Series Ax-8xxx & E-Series Ex-8xxx & FX-870K) |
| Windows 10 Enterprise LTSB 2016                                                                             | Up through the following Intel 7th Generation Processors (Intel Core i3/i5/i7/i9-7xxxx, Core m3-7xxx, and Xeon E3-xxxx v6) and through series equivalent Intel Atom, Celeron and Pentium Processors             | Up through the following AMD 7th Generation Processors (A-Series Ax-9xxx & E-Series Ex-9xxx & FX-9xxx) |
| Windows 10 Enterprise CBB 1607                                                                              | Up through the following Intel 7th Generation Processors (Intel Core i3/i5/i7/i9-7xxxx, Core m3-7xxx, and Xeon E3-xxxx v6) and through series equivalent Intel Atom, Celeron and Pentium Processors             | Up through the following AMD 7th Generation Processors (A-Series Ax-9xxx & E-Series Ex-9xxx & FX-9xxx) |

## Windows Server

| Windows Edition                                                                                             | Intel Processors                                                                                                                                                                                       | AMD Processors                                                                                         |
|-------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Windows Server 2012 R2\*                                                                                    | Up through the following Intel 7th Generation Processors (Intel Core i3/i5/i7/i9 -7xxxx; Core m3-7xxx; Xeon E3 v6; Xeon SP 31xx, 41xx, 51xx, 61xx, and 81xx; and Xeon D 15xx), and Atom C33xx           | Up through the following AMD 7th generation processors (AMD A-Series Ax-9xxx & E-Series Ex-9xxx & FX-9xxx), AMD Ryzen Family, and AMD EPYC 7xxxx |
| Windows Server 2016\**                                                                                      | Up through the following Intel 7th Generation Processors (Core i3/i5/i7/i9 -7xxxx; Core m3-7xxx; Xeon E3 v6; Xeon SP 31xx, 41xx, 51xx, 61xx, and 81xx; and Xeon D 15xx), and Atom C33xx                | Up through the following AMD 7th generation processors (AMD A-Series Ax-9xxx & E-Series Ex-9xxx & FX-9xxx), AMD Ryzen Family, and AMD EPYC 7xxxx |

\*Company may submit for certification (in the Windows Hardware Compatibility Program) Customer Systems running Windows Server 2012R2 and the identified processors until December 31, 2017; after such date, no new Customer Systems will be certified running Windows Server 2012R2. 

\** Microsoft continues to evaluate the processor list and potential end dates for certification (in the Windows Hardware Compatibility Program) for Customer Systems running Windows Server 2016, and plans to provide an update to Company by September 15, 2017.


