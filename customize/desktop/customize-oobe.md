---
title: Customize the Out of Box experience (OOBE)
description: Customize the Windows Out of Box experience
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.author: alhopper
ms.date: 09/27/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Customize the Out of Box Experience (OOBE)

When customers turn on their Windows PCs for the first time, they will see the Windows Out of Box Experience (OOBE). OOBE consists of a series of screens that require customers to accept the license agreement, connect to the internet, log in with, or sign up for a Microsoft Account, and share information with the OEM. In Windows 10, this flow is streamlined. The choices you make in your hardware and software engineering determine how much work customers must do to complete the OOBE screens before they can enjoy their PCs running Windows 10.

During OOBE, Cortana voice-over strings will assist users by setting the context of each screen, and requesting their input. While voice assistance is more accessible to the non-sighted, the design is focused at being inclusive to all our customers. Cortana voice is intended to be novel and supplementary to increase user engagement in all places in OOBE. We still expect non-sighted users to enable screen readers to get through OOBE. Some pages in OOBE do not accept voice input, and instead require a keyboard or mouse to complete the action. Cortana voice will clearly communicate input requirements (voice or keyboard/mouse) to the user.

The OOBE flow is also designed to reduce cognitive load significantly by breaking up tasks into discrete chunks. There are several pages in the OOBE flow, and each one requests a specific action or input from the user. This is helpful for our average customer (and even many power users) and has shown to reduce fatigue significantly.

## OOBE flow

The following is a non-exhaustive list of screens the user may see during OOBE, in order:

1. Language selection
1. Cortana welcome
1. Region selection
1. Keyboard selection
1. End User License Agreement (EULA)
1. Connect to a network
1. Sign in to, or create, a Microsoft account
1. Windows Hello setup
1. Privacy settings
1. Save files to OneDrive
1. Set up Office. This screen is only displayed if the user is connected to a network, and has provided their Microsoft account information.
1. OEM Registration pages

> [!NOTE]
> You can hide certain OOBE screens using Unattend. For more information, see [Microsoft-Windows-Shell-Setup OOBE Unattend setting](https://docs.microsoft.com/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-shell-setup-oobe).

## In this section

The following topics describe OOBE customization considerations.

| Topic                                     | Description                                                                        |
|:------------------------------------------|:-----------------------------------------------------------------------------------|
| [OOBE.xml](oobexml.md)                               | Create an OOBE.xml file to organize text and images displayed during OOBE, and to specify settings for customizing the Windows 10 first-run experience. You can use multiple Oobe.xml files for language- and region-specific license terms and settings so that users see appropriate info as soon as they start their PCs. By specifying information in the Oobe.xml file, you help fill in some of the required information so that users are asked to do only the core tasks required to set up their PCs. |
| [Cortana voice support](cortana-voice-support.md)    | This topic describes how Cortana voice walks the user through the OOBE experience, enabling the user to complete parts of OOBE by responding to spoken prompts.                       |
| [OEM HID pairing](oem-hid-pairing.md)                | Add HID pairing support for PCs that ship with an unpaired wireless mouse and/or keyboard. The HID pairing screens are shown to the customer during the first-run experience in OOBE, which is before language selection or any other screen that requires user input.                       |
| [OEM license terms](oem-license.md)                  | You can add your OEM license terms to the License Terms screen in the first-run experience of OOBE. |
| [OEM registration pages](oem-registration-pages.md)  | Add OEM registration screens to gather customer information, and introduce offers, during OOBE.     |

## Related topics

[OOBE Unattend setting](https://docs.microsoft.com/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-shell-setup-oobe)

[Configure Oobe.xml](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-oobexml)