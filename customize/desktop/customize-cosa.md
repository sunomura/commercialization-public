---
title: Customize the Country and Operator Settings Asset
description: Customize the COSA database of mobile operator profiles
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.author: alhopper
ms.date: 09/20/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Customize the Country and Operator Settings Asset


In Windows 10, version 1703, we added the Country and Operator Settings Asset (COSA) database of mobile operator profiles. It is included in Windows 10 as a provisioning package. When a SIM is inserted in a COSA-enabled Windows-based device, the provisioning framework attempts to establish a cellular connection by searching for the matching profile and APN in COSA.  

> [!Note]  
> This feature is only supported in Windows 10, version 1703 for desktop editions (Home, Pro, Enterprise, and Education)

COSA can be extended with OEM-generated provisioning packages during desktop imaging. This enables OEMs to introduce new COSA profiles to the database, as well as replace or extend existing COSA profiles. For example, you can add a profile for a mobile virtual network operator (MVNO) not currently in COSA, or a new partner for Data Marketplace, by creating an answer file that contains the settings. You can also change or remove an existing profile using the `Replace` operator in the existing answer file.

> [!Important]
> When using `Replace` to change or remove a profile, there are certain settings, listed below, which should not be modified or removed by OEMs. These settings are either system specific, or contractual settings between Microsoft and Mobile Operators (MOs), and their values should be preserved.
> 
> * Support DataMarketplace
> * DataMarketplace Roaming UI Enabled
> * Account Experience URL
> * Branding Name
> * Branding Icon Name
> * Use Branding Name on Roaming

> [!Important]  
> Microsoft is collecting the following telemetry data related to the COSA:
> - AfterMarketProfile – Published when an OEM package adds a new profile. Data includes the profile ID (typically a GUID) as well as the targeting info for the profile (such as MCC, MNC, SPN, and so on).
> - ProfileReplaced – Published when the OEM package replaces a COSA profile. Data is the profile ID.
> - ProfileSuppressedByAfterMarketProfile – Published when an OEM package contains a profile that matches when a COSA profile also matches. The telemetry data contains the Profile ID.

We recommend MOs and organizations submit any profile changes made to extend COSA to Microsoft. To learn more, see [COSA/APN database submission](https://docs.microsoft.com/en-us/windows-hardware/drivers/mobilebroadband/apn-database-submission).

## To add a new profile

You can add a new profile that is not yet included in the COSA database using the following steps.

1. Create an answer file or edit an existing answer file that contains the new profile settings. Here is an example:

  ```
    <?xml version="1.0" encoding="UTF-8"?>
  <WindowsCustomizations>
    <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
      <ID>{7240F79C-7567-4BA3-95C0-ABD31D02A385}</ID>
      <Name>COSAPC.Extension</Name>
      <Version>5.0</Version>
      <OwnerType>OEM</OwnerType>
    </PackageConfig>
    <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
      <Customizations>
        <Targets>
          <Target Id="12345678-abcd-1111-aaaa-1ead5bca0320">
            <TargetState>
              <Condition Name="Mcc" Value="901" />
              <Condition Name="Mnc" Value="37" />
              <Condition Name="ICCID" Value="range:8988247000100000000,8988247000199999997" />
              <Condition Name="uiname" Value="Fabrikam (OEM)" />
              <Condition Name="uiorder" Value="0" />
            </TargetState>
          </Target>
          <Target Id="87654321-abcd-1111-aaaa-1ead5bca0320">
            <TargetState>
              <Condition Name="Mcc" Value="001" />
              <Condition Name="Mnc" Value="01" />
              <Condition Name="uiname" Value="Contoso (OEM)" />
              <Condition Name="uiorder" Value="0" />
            </TargetState>
          </Target>
        </Targets>
        <Profile Name="Fabrikam (OEM)">
          <TargetRefs>
            <TargetRef Id="87654321-abcd-1111-aaaa-1ead5bca0320" />
          </TargetRefs>
          <Settings>
            <Connections>
              <Cellular>
                <Connection ConnectionName="Fabrikam (OEM)_i0$(__MVID)@WAP">
                  <PurposeGroups>{3e5545d2-1137-4dc8-a198-33f1c657515f}</PurposeGroups>
                  <AlwaysOn>1</AlwaysOn>
                  <FriendlyName>DataMarketplace</FriendlyName>
                  <AccessPointName>apn</AccessPointName>
                  <IPType>IPv4v6</IPType>
                  <AlwaysOn>1</AlwaysOn>
                  <Roaming>5</Roaming>
                </Connection>
              </Cellular>
            </Connections>
            <DataMarketplace>
              <PerSimSettings>
                <SettingsForSim SimIccid="$(__ICCID)">
                  <SupportDataMarketplace>1</SupportDataMarketplace>
                  <DataMarketplaceRoamingUIEnabled>0</DataMarketplaceRoamingUIEnabled>
                </SettingsForSim>
              </PerSimSettings>
            </DataMarketplace>
          </Settings>
        </Profile>
        <Profile Name="Contoso (OEM)">
          <TargetRefs>
            <TargetRef Id="12345678-abcd-1111-aaaa-1ead5bca0320" />
          </TargetRefs>
          <Settings>
            <Connections>
              <Cellular>
                <Connection ConnectionName="Contoso (OEM)_i0$(__MVID)@WAP">
                  <PurposeGroups>{3e5545d2-1137-4dc8-a198-33f1c657515f}</PurposeGroups>
                  <AlwaysOn>1</AlwaysOn>
                  <FriendlyName>DataMarketplace</FriendlyName>
                  <AccessPointName>apn</AccessPointName>
                  <IPType>IPv4v6</IPType>
                  <AlwaysOn>1</AlwaysOn>
                  <Roaming>5</Roaming>
                </Connection>
              </Cellular>
            </Connections>
            <DataMarketplace>
              <PerSimSettings>
                <SettingsForSim SimIccid="$(__ICCID)">
                  <SupportDataMarketplace>1</SupportDataMarketplace>
                  <DataMarketplaceRoamingUIEnabled>0</DataMarketplaceRoamingUIEnabled>
                </SettingsForSim>
              </PerSimSettings>
            </DataMarketplace>
          </Settings>
        </Profile>
      </Customizations>
    </Settings>
  </WindowsCustomizations>
  ```

2. Create a provisioning package that includes the answer file. For more information, see [To build a provisioning package](https://docs.microsoft.com/en-us/windows/configuration/provisioning-packages/provisioning-command-line#to_build_a_provisioning_package).

3. Place your provisioning packages (PPKG) in the following location: %WINDIR%\Provisioning\COSA\OEM.

4. Perform necessary tests for validation.  

For a full list of COSA settings, please see [Planning your COSA/APN database submission](https://docs.microsoft.com/en-us/windows-hardware/drivers/mobilebroadband/planning-your-apn-database-submission#complete-the-apncosa-update-spreadsheet).

## To change an existing profile 

Use the `Replace` operator to make changes to an existing profile. 

1. Navigate to the provisioning package (PPKG) where the COSA database is stored. It should be in the following location: %WINDIR%\Provisioning\COSA\Microsoft.

2. Unzip the package and open the answer file. You can use a third-party tool, such as 7-Zip File Manager ([www.7-Zip.org](http://www.7-zip.org/)), to inspect and unzip the package.

3. Edit the answer file to use the `Replace` operator, and only make changes to settings that require modification. Leave all other settings as they are.

  ```
  <Replace Name="MobileCarrier1 (Replaced)">
          <TargetRefs>
            <TargetRef Id="aaaaaaaa-d95d-4833-8f13-605691a20fb3" />
          </TargetRefs>
         <Settings>
            <Connections>
              <Cellular>
                <Connection ConnectionName="MobileCarrier1 (Replaced)_i0$(__MVID)@WAP">
                  <PurposeGroups>{3e5545d2-1137-4dc8-a198-33f1c657515f}</PurposeGroups>
                  <AlwaysOn>1</AlwaysOn>
                  <FriendlyName>Broadband</FriendlyName>
                 <AccessPointName>broadband</AccessPointName>
                  <IPType>IPv4v6</IPType>
                </Connection>
                <Connection ConnectionName="MobileCarrier1 (Replaced)_i1$(__MVID)@WAP">
                  <PurposeGroups>{3e5545d2-1137-4dc8-a198-33f1c657515f}</PurposeGroups>
                  <AlwaysOn>1</AlwaysOn>
                  <FriendlyName>Newphone</FriendlyName>
                  <AccessPointName>newgenphone</AccessPointName>
                  <IPType>IPv4v6</IPType>
                </Connection>
                <Connection ConnectionName="MobileCarrier1 (Replaced)_i2$(__MVID)@WAP">
                  <PurposeGroups>{95522B2B-A6D1-4E40-960B-05E6D3F962AB}</PurposeGroups>
                  <AlwaysOn>0</AlwaysOn>
                  <FriendlyName>Purchasing</FriendlyName>
                  <AccessPointName>Some_name_here</AccessPointName>
                  <IPType>IPv4v6</IPType>
                </Connection>
             </Cellular>
            </Connections>
            <Cellular>
              <PerSimSettings>
               <SettingsForSim SimIccid="$(__ICCID)">
                 <AccountExperienceURL>https://some_URL_here</AccountExperience>
                 <AppID>
                  AppID_here
                 </AppID>
                </SettingsForSim>
              </PerSimSettings>
            </Cellular>
         </Settings>
        </Replace>
   ```

   > [!Note]  
   > The TargetRef ID used by the Replace operator should be the profile GUID used by COSA.

4. Create a provisioning package that includes the modified answer file. For more information, see [To build a provisioning package](https://docs.microsoft.com/en-us/windows/configuration/provisioning-packages/provisioning-command-line#to_build_a_provisioning_package).

5. Place your provisioning packages (PPKG) in the following location: %WINDIR%\Provisioning\COSA\OEM.

6. Perform necessary tests for validation.  


## To remove an existing profile  

Use the `Replace` operator to remove an existing profile. The settings included in a `Replace` element are applied instead of the original COSA settings. If no settings are specified, the operation becomes a Removal.

1. Navigate to the provisioning package (PPKG) where the COSA database is stored. It should be in the following location: %WINDIR%\Provisioning\COSA\Microsoft.

2. Unzip the package and open the answer file. You can use a third-party tool, such as 7-Zip File Manager ([www.7-Zip.org](http://www.7-zip.org/)), to inspect and unzip the package.

3. Edit the answer file to use the `Replace`operator. Delete any settings you wish to remove from the COSA database. Here is an example:  

  ```
        <Replace Name="MobileCarrier2 (Removed)">
          <TargetRefs>
            <TargetRef Id="bbbbbbbb-aafd-46f3-88b1-014d2bdf879f" />
          </TargetRefs>
        </Replace>
  ```

4. Create a provisioning package that includes the answer file. For more information, see [To build a provisioning package](https://docs.microsoft.com/en-us/windows/configuration/provisioning-packages/provisioning-command-line#to_build_a_provisioning_package).

5. Place your provisioning packages (PPKG) in the following location: %WINDIR%\Provisioning\COSA\OEM.

6. Perform necessary tests for validation.  
