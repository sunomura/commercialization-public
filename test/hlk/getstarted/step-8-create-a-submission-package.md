---
title: Step 8 Create a submission package
description: Step 8 Create a submission package
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c7890995-e415-44c2-9f90-0d45e3b79ba0
---

# Step 8: Create a submission package

>[!NOTE]
>  We highly encourage you to include driver symbols as part of package creation. Including symbols enables Microsoft to triage and root cause issues related to your driver.

 

After the device passes all of the necessary tests, you can create a submission package (.hlkx file) for submission.

Windows HLK Studio supports package creation, so you don't need to use a separate submission tool. It supports adding resource files (drivers, symbols, errata) necessary to complete certification. You can also merge multiple packages (.hlkx files) into one single package.

The following image shows the HLK Studio **Package** tab.

![hlk studio package tab](images/hlk-studio-package-tab.png)

## <span id="To_create_a_submission_package"></span><span id="to_create_a_submission_package"></span><span id="TO_CREATE_A_SUBMISSION_PACKAGE"></span>To create a submission package


1.  Select the **Package** tab.

2.  If you used a special driver for a device (optional), submit it by doing this:

    1.  Click **Add Driver Folder** &gt; **Browse** to select the folder, and then click **OK**.

    2.  In the **Driver Properties** dialog box, select the appropriate **Products** and **Locales**, and then click **OK**.

        >[!IMPORTANT]
        >  The default locale is English only. If you want to add another locale, you must add it now. After the driver package is created, you cannot change the locales.

         

3.  To add symbols (optional), right-click the driver folder, click **Add Symbols** &gt; **Browse** to select the folder, and then click **OK**.

4.  To add a supplemental folder (optional), such as a Readme file, contingency message, errata, or manual filter, click **Add Supplemental Folder** &gt; **Browse** to select the folder, and then click **OK**.

5.  Click **Create Package**.

6.  From the **Signing Options** dialog box, select one of these options:

    >[!IMPORTANT]
    > All submissions must be digitally signed.
    > Starting with Windows 10, you must also include an EV (extended validation) code signing certificate.

    -   **Do not sign** to create an unsigned package, for example, to send to Support for debugging or to later merge with other packages into a single submission package.

    -   **Use the certificate store** to create a digitally signed package—the most common scenario. This option requires an X509 certificate—for example a VeriSign certificate— to be installed on the computer running Windows HLK Studio. From the **Windows Security** dialog box, select the appropriate code signing certificate.

    -   **Use a certificate file** to create a digitally signed package by using a portable security file. This option asks you for an X509 certificate file (.cer file).

For additional information on packages, see the following topics:

-   [HLK Studio - Package Tab](..\user\hlk-studio---package-tab.md)

-   [HLK Signing with an HSM](..\user\hlk-signing-with-an-hsm.md)

### <span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Next steps

Congratulations, you have completed the end to end testing of your device using the Windows HLK. Submit the signed package (.hlkx file) through the Hardware Dashboard on the Windows Dev Center. For more details, see [Dashboard Help](http://go.microsoft.com/fwlink/?LinkId=236060) in the Windows Dev Center.

 

 






