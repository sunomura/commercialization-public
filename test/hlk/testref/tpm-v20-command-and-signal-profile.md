---
title: TPM V2.0 Command and Signal Profile
description: TPM V2.0 Command and Signal Profile
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e29d8090-88ab-4124-ba8e-4772f2007790
---

# TPM V2.0 Command and Signal Profile


This document specifies the TPM signaling interface supported by Windows 8 and lists TPM 2.0 commands that:

1.  Are used by Windows 8 and hence required to be implemented for Windows Hardware Certification;

2.  Are not used by Windows 8 but are recommended to implement for other reasons (e.g. TPM management, expected 3rd party app usage and OEM usage.); and

3.  Are not used by Windows 8 but are optional to implement.

No other signaling interface is supported but additional TPM 2.0 commands that are not used by Windows may be implemented in a TPM 2.0 device that is compliant with this specification. Please contact Microsoft for more information about vendor-specific command ranges.

## <span id="Command_and_Signal_Profile"></span><span id="command_and_signal_profile"></span><span id="COMMAND_AND_SIGNAL_PROFILE"></span>Command and Signal Profile


### <span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Requirements

This profile requires that a TPM 2.0 implemented to support Windows 8:

-   Implements the TCG TPM 2.0 Library Specification including critical security patches (for compatibility with later version of the specification, please contact Microsoft. For certifying TPMs in 2015, requirement is to implement v0.99 along with required security patches. For information about the required security patches, please contact Microsoft.)

-   Is always active; i.e. no need for programmatic or user-driven activation.

-   Is provisioned with a primary seed for Endorsement and Storage.

### <span id="Requirements_Matrix"></span><span id="requirements_matrix"></span><span id="REQUIREMENTS_MATRIX"></span>Requirements Matrix

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Signals and Indications</th>
<th>Included</th>
<th>Optional</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>_TPM_Init</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>_TPM_Hash_Start</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>_TPM_Hash_Data</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>_TPM_Hash_End</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Commands</th>
<th>Included</th>
<th>Optional</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Start Up Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_Startup</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>Used by the firmware only</p></td>
</tr>
<tr class="odd">
<td><p>TPM2_Shutdown</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Testing Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_SelfTest</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_IncrementalSelfTest</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_GetTestResult</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Session Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_StartAuthSession</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicyRestart</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Object Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_Create</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_Load</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_LoadExternal</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="odd">
<td><p>TPM2_ReadPublic</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_ActivateCredential</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_MakeCredential</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="even">
<td><p>TPM2_Unseal</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_ObjectChangeAuth</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Duplication Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_Duplicate</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_Rewrap</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_Import</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Asymmetric Primitives</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_RSA_Encrypt</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_RSA_Decrypt</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_ECDH_KeyGen</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_ECDH_ZGen</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_ECC_Parameters</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Symmetric Primitives</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_EncryptDecrypt</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_Hash</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_HMAC</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Random Number Generator</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_GetRandom</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_StirRandom</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Hash/HMAC/Event Sequences</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_HMAC_Start</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_HashSequenceStart</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="even">
<td><p>TPM2_SequenceUpdate</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="odd">
<td><p>TPM2_SequenceComplete</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="even">
<td><p>TPM2_EventSequenceComplete</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="odd">
<td><p><strong>Attestation Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_Certify</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_CertifyCreation</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_Quote</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_GetSessionAuditDigest</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_GetCommandAuditDigest</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_GetTime</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Anonymous Attestation Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_Commit</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Signature Verification Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_VerifySignature</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="even">
<td><p>TPM2_Sign</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Command Audit</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_SetCommandCodeAuditStatus</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Integrity Collection</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PCR_Extend</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PCR_Event</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PCR_Read</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PCR_Allocate</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PCR_SetAuthPolicy</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PCR_SetAuthValue</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PCR_Reset</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Enhanced Authorization Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicySigned</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PolicySecret</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicyTicket</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PolicyOR</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicyPCR</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PolicyLocality</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicyNV</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PolicyCounterTimer</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicyCommandCode</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PolicyPhysicalPresence</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicyCpHash</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PolicyNameHash</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicyDuplicationSelect</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PolicyAuthorize</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicyAuthValue</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_PolicyPassword</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Recommended</p></td>
</tr>
<tr class="even">
<td><p>TPM2_PolicyGetDigest</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Hierarchy Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_CreatePrimary</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_HierarchyControl</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_SetPrimaryPolicy</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_ChangePPS</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_ChangeEPS</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_Clear</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_ClearControl</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_HierarchyChangeAuth</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Dictionary Attack Functions</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_DictionaryAttackLockReset</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_DictionaryAttackParameters</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Miscellaneous Management Functions</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_PP_Commands</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_SetAlgorithmSet</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Field Upgrade</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_FieldUpgradeStart</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>Microsoft strongly recommends some update mechanism is provided</p></td>
</tr>
<tr class="even">
<td><p>TPM2_FieldUpgradeData</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_FirmwareRead</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Context Management</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_ContextSave</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_ContextLoad</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_FlushContext</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_EvictControl</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Clocks and Timers</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_ReadClock</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>Used to read the boot counter</p></td>
</tr>
<tr class="odd">
<td><p>TPM2_ClockSet</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>Likely used by firmware only</p></td>
</tr>
<tr class="even">
<td><p>TPM2_ClockRateAdjust</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Capability Commands</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_GetCapability</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_TestParms</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Non-volatile Storage</strong></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_NV_DefineSpace</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_NV_UndefineSpace</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>Win 8 may use Clear instead</p></td>
</tr>
<tr class="odd">
<td><p>TPM2_NV_UndefineSpaceSpecial</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_NV_ReadPublic</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_NV_Write</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>Likely used by OEM only</p></td>
</tr>
<tr class="even">
<td><p>TPM2_NV_Increment</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_NV_Extend</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_NV_SetBits</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_NV_WriteLock</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_NV_GlobalWriteLock</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_NV_Read</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_NV_ReadLock</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>TPM2_NV_ChangeAuth</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>TPM2_NV_Certify</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

 

 






