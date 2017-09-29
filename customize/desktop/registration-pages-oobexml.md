---
title: Configure OOBE.xml
description: Configure your OOBE.xml file to support OEM registration pages
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.author: alhopper
ms.date: 09/27/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Configure OOBE.xml

To include your registration pages in OOBE, you must configure the appropriate settings of your OOBE.xml file.

| Element | Setting | Description | Value |
| ------- | ------ | ----------- | ----- |
| <**oem**> |  |  |  |
|  | \<registration> | Optional. Additional details are below. |
| <**registration**> | | | |
| | \<title> | Required if registration element is used. Text to title the Registration page. | String of up to 25 characters. |  
| | \<subtitle> | Required if registration element is used. Text to describe the Registration page. |
| <**customerinfo**> | | | |
| | \<label> | Text to label customerinfo. Rquired for customerinfo to appear. | String of up to 250 characters. We strongly recommend that you use no more than 100 characters because this length of text will fit on one line. |
| | \<defaultvalue> | Value to set customerinfo as selected or not. If this field is checked, information from the four input fields will be provided via asymmetric key encryption. If not checked, no information from the four input fields will be provided. | True or False. True means the check box default condition is selected. False means the check box default condition isn't selected. |
| <**checkbox1**> | | | |
| | \<label> | Text to label checkbox1. Required for checkbox1 to appear. | String of up to 250 characters. We strongly recommend that you use no more than 100 characters because this length of text will fit on one line. |
| | \<defaultvalue> | Value to set checkbox1 as selected or not selected. | True or False. True means the check box default condition is selected. False means the check box default condition isn't selected. |
| \<**checkbox2**> | | | |
| | \<label> | Text to label checkbox2. Required for checkbox2 to appear. | String of up to 250 characters. We strongly recommend that you use no more than 100 characters because this length of text will fit on one line. |
| | \<defaultvalue> | Value to set checkbox3 as selected or not selected. | True or False. True means the check box default condition is selected. False means the check box default condition isn't selected. |
| <**checkbox3**> | | | |
| | \<label> | Text to label checkbox3. Required for checkbox3 to appear. | String of up to 250 characters. We strongly recommend that you use no more than 100 characters because this length of text will fit on one line. |
| | \<defaultvalue> | Value to set checkbox3 as selected or not selected. | True or False. True means the check box default condition is selected. False means the check box default condition isn't selected. |
| <**link1**> | | | |
| | \<label> | Label for the link to the HTML file. Required for link1 to appear. | String of up to 100 characters.|
| | \<link> | File must be named linkfile1.html. OOBE searches for these files under the oobe\info folder. OOBE searches for files under the appropriate locale and language specific subfolders of oobe\info. | linkfile1.html |
| <**link2**> | | | |
| | \<label> | Label for the link to the HTML file. Required for link2 to appear. | String of up to 100 characters.|
| | \<link> | File must be named linkfile2.html. OOBE searches for these files under the oobe\info folder. OOBE searches for files under the appropriate locale and language specific subfolders of oobe\info. | linkfile2.html |
| <**link3**> | | | |
| | \<label> | Label for the link to the HTML file. Required for link3 to appear. | String of up to 100 characters.|
| | \<link> | File must be named linkfile3.html. OOBE searches for these files under the oobe\info folder. OOBE searches for files under the appropriate locale and language specific subfolders of oobe\info. | linkfile3.html |
| <**hideSkip**> | | Optional. Controls whether or not the Skip button is displayed to the user.  Default is False, resulting in the skip button being visible. | True or False. True means the skip button is not visible to the user. False means the skip button is displayed as an option to the user. |

At least one element (for example, `customerinfo`) is required in order for the registration screens to display during OOBE.

> [!Tip]
> For more information on these settings, and the others you can configure, please see [Oobe.xml Settings](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/oobexml-settings).

## XML example

```xml
<oobe>
    <oem>
      <registration>
        <title>Register your PC</title>
        <subtitle>This page will help Fabrikam know about you.</subtitle>
        <customerinfo>
          <label>Let Fabriakm contact you</label>
          <defaultvalue>true</defaultvalue>
        </customerinfo>
        <checkbox1>
          <label>Use Contoso Antimalware to help protect your PC</label>
          <defaultvalue>true</defaultvalue>
        </checkbox1>
        <checkbox2>
          <label>Let Fabrikam send you offers</label>
        </checkbox2>
        <checkbox3>
          <label>Let Fabrikam send you offers</label>
        </checkbox3>
        <link1>
          <label>Learn more about Contoso Antimalware</label>
        </link1>
        <link2>
          <label>Learn more about Fabrikam offers</label>
        </link2>
        <link3>
          <label>Fabrikam privacy statement</label>
        </link3>
        <hideSkip>true</hideSkip>
      </registration>
    </oem>
</oobe>
```