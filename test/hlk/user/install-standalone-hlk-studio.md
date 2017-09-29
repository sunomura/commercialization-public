---
title: Install standalone HLK Studio
description: Install standalone HLK Studio
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: da9dd0fd-cffc-4276-9398-e60505c5236b
---

# Install standalone HLK Studio


You can install a standalone Windows HLK Studio if you want to view .hlkx certification packages (including logs/results), either in-progress or finished, without installing the Windows HLK Controller. Installation only takes a few seconds, and enables you to complete the following scenarios:

-   View log files from the package.

-   View test results in the package.

-   Regenerate the package.

-   Merge with another package.

-   Add additional drivers to the package.

-   Add a DUA driver update to the package.

## <span id="To_install_standalone_Windows_HLK_Studio"></span><span id="to_install_standalone_windows_hlk_studio"></span><span id="TO_INSTALL_STANDALONE_WINDOWS_HLK_STUDIO"></span>To install standalone Windows HLK Studio


1.  [Download the Windows HLK](https://go.microsoft.com/fwlink/p/?LinkId=733613) to a location accessible to your test server.

2.  From HLKSetup.exe, select the **Studio Only** option.

3.  After installation, open HLK Studio.

4.  HLK Studio opens automatically on the **Connect** tab, which you can interact with just as you would with the full Windows HLK.

## <span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Limitations


Installing a standalone HLK Studio also installs HLK Manager to your system. However, you won’t be able to access or use any of the features of HLK Manager.

Also, you should avoid installing a standalone HLK Studio on the same machine where a remote Studio (Studio installed from a Controller) has been installed. There are known limitations to this scenario, which may leave your system in an inoperable state.

 

 






