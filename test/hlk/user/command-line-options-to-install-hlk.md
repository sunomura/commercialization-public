---
title: Command-line options to install HLK
description: Command-line options to install HLK
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 356d44dc-226c-482b-bf47-2fa6ab6a4d94
---

# Command-line options to install HLK


## <span id="Installation_and_Uninstallation_Examples"></span><span id="installation_and_uninstallation_examples"></span><span id="INSTALLATION_AND_UNINSTALLATION_EXAMPLES"></span>Installation and Uninstallation Examples


To install the Windows HLK Controller, Studio, Client and/or Manager (Unattended):

-   To install the Windows HLK Controller, use the following command from the root of the Windows HLK installation media:

    -   HLKSetup.exe /q

    >[!NOTE]
    >  By installing one or all of the kits, you automatically install all prerequisites (Windows HLK Controller, .NET 4.5, SQL), so there is no need to individually install other Windows HLK features.

 

To install/uninstall Windows HLK Controller and HLK Studio (Unattended)

-   To uninstall the Windows HLK Controller and HLK Studio, use the following command from the root of the Windows HLK installation media:

    -   HLKSetup.exe /uninstall /q

-   To install the Windows HLK Client:

    -   \\\\HLKController\\HLKInstall\\Client\\setup.cmd /qn ICFAGREE=Yes

-   To install the Windows HLK Studio:

    -   \\\\HLKController\\HLKInstall\\Studio\\setup.exe /qn

-   To uninstall the Windows HLK Client:

    -   \\\\HLKController\\HLKInstall\\Client\\setup.cmd /qn /uninstall

-   To uninstall the Windows HLK Studio:

    -   \\\\HLKController\\HLKInstall\\Studio\\setup.exe /qn /uninstall

    >[!NOTE]
    >  Replace “HLKController” with the name of the computer on which you installed the Controller.

 

 

 






