---
title: Trusted Execution Environment EFI Protocol
description: Trusted Execution Environment EFI Protocol
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ffb509a2-6d7b-49a2-9e12-e7a06f1bb330
---

# Trusted Execution Environment EFI Protocol


Licensing: Microsoft agrees to grant to you a no charge, royalty-free license to its Necessary Claims on reasonable and non-discriminatory terms solely to make, use, sell, offer for sale, import, or distribute any implementation of this specification. “Necessary Claims” are those claims of Microsoft-owned or Microsoft-controlled patents that are technically necessary to implement the required portions (which also include the required elements of optional portions) of this specification, where the functionality causing the infringement is described in detail and not merely referenced in this Specification.

## <span id="1.0_introduction"></span><span id="1.0_INTRODUCTION"></span>1.0 Introduction


This document specifies an EFI protocol for interacting with a Trusted Execution Environment (TrEE), implementing TPM 2.0 functionality per a subset of a Trusted Computing Group (TCG) Trusted Platform Module 2.0 Library specification. This document also specifies platform firmware measurement requirements. The EFI protocol defined herein leverages to a large degree \[TCG06a\] and \[TCG06b\].

## <span id="2.0_data_structures_and_acronyms"></span><span id="2.0_DATA_STRUCTURES_AND_ACRONYMS"></span>2.0 Data Structures and Acronyms


### <span id="2.1_Data_Structures"></span><span id="2.1_data_structures"></span><span id="2.1_DATA_STRUCTURES"></span>2.1 Data Structures

As in \[TCG06a\], all data values SHALL be represented in Little-Endian format. Strings SHALL be represented as an array of ASCII bytes with the left-most character placed in the lowest memory location.

### <span id="2.2_Acronyms_and_Conventions"></span><span id="2.2_acronyms_and_conventions"></span><span id="2.2_ACRONYMS_AND_CONVENTIONS"></span>2.2 Acronyms and Conventions

(For acronyms not defined herein, see \[TCG06a\])

TrEETrusted Execution Environment

Use of the terms “MUST” and “SHALL” in this document are to be interpreted in accordance with \[RFC2119\].

## <span id="3.0_efi_tree_protocol"></span><span id="3.0_EFI_TREE_PROTOCOL"></span>3.0 EFI TrEE Protocol


This section provides a detailed description of the EFI\_TREE\_PROTOCOL and the EFI\_TREE\_SERVICE\_BINDING\_PROTOCOL. The EFI TrEE Protocol is used to communicate with a TrEE.

### <span id="3.1_TrEE_EFI_Service_Binding_Protocol"></span><span id="3.1_tree_efi_service_binding_protocol"></span><span id="3.1_TREE_EFI_SERVICE_BINDING_PROTOCOL"></span>3.1 TrEE EFI Service Binding Protocol

This section defines the TrEE EFI service binding protocol.

**Summary** - The EFI TrEE Service Binding Protocol is used to locate TrEE devices that are supported by an EFI TrEE Protocol driver and to create and destroy EFI TrEE protocol child driver instances that can use the underlying TrEE device.

**GUID** - `#define EFI_TREE_SERVICE_BINDING_PROTOCOL_GUID \   {0x4cf01d0a, 0xc48c, 0x4271, 0xa2, 0x2a, 0xad, 0x8e, 0x55, 0x97,\    0x81, 0x88}`

**Description**An application (or driver) that requires TrEE services can use one of the protocol handler services, such as BS-&gt;LocateHandleBuffer(), to search for devices that publish an EFI TrEE Service Binding Protocol. Each device with a published the EFI TrEE Service Binding Protocol supports the EFI TrEE Protocol and may be available for use.

After a successful call to the EFI\_TREE\_SERVICE\_BINDING\_PROTOCOL.CreateChild() function, the child EFI TrEE Protocol driver instance is ready for use.

Before an EFI application or driver terminates execution, every successful call to the EFI\_TREE\_SERVICE\_BINDING\_PROTOCOL.CreateChild() function must be matched with a call to the EFI\_TREE\_SERVICE\_BINDING\_PROTOCOL.DestroyChild() function.

### <span id="3.2_TrEE_EFI_Protocol"></span><span id="3.2_tree_efi_protocol"></span><span id="3.2_TREE_EFI_PROTOCOL"></span>3.2 TrEE EFI Protocol

**Summary** - The EFI TrEE protocol is used to communicate with a TrEE – to send commands to a TrEE, use it for trusted execution operations and to provide access to the firmware log of measurements extended in the TrEE. The protocol maintains an Event Log of measurements recorded in the TrEE with a format identical to the TCG 1.2 TCG Event Log (see \[TCG06b\]); referred to as the TrEE Event Log Format TCG 1.2 Event Log in this specification. Implementers may create additional Event Logs with other formats, but this version of the protocol does not define a way to retrieve them.

**GUID** - `#define EFI_TREE_PROTOCOL_GUID \   {0x607f766c, 0x7455, 0x42be, 0x93, 0x0b, 0xe4, 0xd7, 0x6d, 0xb2,\    0x72, 0x0f}`

**Protocol Interface Structure** -

``` syntax
typedef struct _EFI_TREE_PROTOCOL {
  EFI_TREE_GET_CAPABILITYGetCapability;
  EFI_TREE_GET_EVENT_LOGGetEventLog;
  EFI_TREE_HASH_LOG_EXTEND_EVENTHashLogExtendEvent;
  EFI_TREE_SUBMIT_COMMANDSubmitCommand;
} EFI_TREE_PROTOCOL;
```

**Parameters**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>GetCapability</p></td>
<td><p>This service provides information about the TrEE and firmware capabilities</p></td>
</tr>
<tr class="even">
<td><p>GetEventLog</p></td>
<td><p>Get a pointer to a firmware event log</p></td>
</tr>
<tr class="odd">
<td><p>HashLogExtendEvent</p></td>
<td><p>This service will cause the EFI TrEE driver to extend an event and (optionally) write the event to the TrEE log.</p></td>
</tr>
<tr class="even">
<td><p>SubmitCommand</p></td>
<td><p>This service submits a command directly to the TrEE.</p></td>
</tr>
</tbody>
</table>

 

**Description** - The EFI\_TREE\_PROTOCOL abstracts TrEE activity. This protocol instance provides a Boot Service and is instantiated as a Boot Service Driver.

Boot Service Drivers are terminated when ExitBootServices ( ) is called and all memory resources consumed by the Boot Services Drivers are released for use in the operating system environment.

This Boot Service must create an EVT\_SIGNAL\_EXIT\_BOOT\_SERVICES event. This event will be notified by the system when ExitBootServices ( ) is invoked.

EVT\_SIGNAL\_EXIT\_BOOT\_SERVICES is a synchronous event used to ensure that certain activities occur following a call to a specific interface function; in this case, that is the cleanup that needs to be done in response to the ExitBootServices ( ) function. ExitBootServices ( ) cannot clean up on behalf of drivers that have been loaded into the system. The drivers have to do that for themselves by creating an event whose type is EVT\_SIGNAL\_EXIT\_BOOT\_SERVICES and whose notification function is a function within the driver itself. Then, when ExitBootServices ( ) has finished its cleanup, it signals the event type EVT\_SIGNAL\_EXIT\_BOOT\_SERVICES.

For implementation details about how a Boot Service instantiated as an EFI Driver creates this required EVT\_SIGNAL\_EXIT\_BOOT\_SERVICES event, see Section 6.1 of \[UEFI12\].

### <span id="3.3_EFI_TREE_PROTOCOL.GetCapability"></span><span id="3.3_efi_tree_protocol.getcapability"></span><span id="3.3_EFI_TREE_PROTOCOL.GETCAPABILITY"></span>3.3 EFI\_TREE\_PROTOCOL.GetCapability

The EFI\_TREE\_PROTOCOL GetCapability function call provides protocol capability information and state information about the TrEE.

**Prototype**

``` syntax
typedef
EFI_STATUS
(EFIAPI *EFI_TREE_GET_CAPABILITY) (
  IN EFI_TREE_PROTOCOL      *This,
  IN OUT TREE_BOOT_SERVICE_CAPABILITY*ProtocolCapability,
);
```

Parameters

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>This</em></p></td>
<td><p>Indicates the calling context.</p></td>
</tr>
<tr class="even">
<td><p>ProtocolCapability</p></td>
<td><p>The caller allocates memory for a TREE_BOOT_SERVICE_CAPABILITY structure and sets the size field to the size of the structure allocated. The callee fills in the fields with the EFI protocol capability information and the current TrEE state information up to the number of fields which fit within the size of the structure passed in.</p></td>
</tr>
</tbody>
</table>

 

**Related Definitions**

``` syntax
typedef struct _TREE_VERSION { 
  UINT8 Major; 
  UINT8 Minor; 
} TREE_VERSION;
typedef UINT64 EFI_PHYSICAL_ADDRESS;
typedef UINT32 TREE_EVENT_LOG_BITMAP;
typedef UINT32 TREE_EVENT_LOG_FORMAT;
#define TREE_EVENT_LOG_FORMAT_TCG_1_2 0x00000001
typedef struct _TREE_BOOT_SERVICE_CAPABILITY { 
  UINT8 Size;
  TREE_VERSION StructureVersion; 
  TREE_VERSION ProtocolVersion;
  UINT32 HashAlgorithmBitmap;
  TREE_EVENT_LOG_BITMAPSupportedEventLogs;
  BOOLEAN TrEEPresentFlag;
  UINT16MaxCommandSize;
  UINT16MaxResponseSize;
  UINT32ManufacturerID;  
} TREE_BOOT_SERVICE_CAPABILITY;

#define TREE_BOOT_HASH_ALG_SHA1       0x00000001
#define TREE_BOOT_HASH_ALG_SHA256     0x00000002
#define TREE_BOOT_HASH_ALG_SHA384     0x00000004
#define TREE_BOOT_HASH_ALG_SHA512     0x00000008
```

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>Size</em></p></td>
<td><p>Allocated size of the structure passed in</p></td>
</tr>
<tr class="even">
<td><p>StructureVersion</p></td>
<td><p>Version of the TREE_BOOT_SERVICE_CAPABILITY structure itself. For this version of the protocol, the <em>Major</em> version shall be set to 1 and the <em>Minor</em> version shall be set to 0.</p></td>
</tr>
<tr class="odd">
<td><p>ProtocolVersion</p></td>
<td><p>Version of the TrEE protocol. For this version of the protocol, the <em>Major</em> version shall be set to 1 and the <em>Minor</em> version shall be set to 0.</p></td>
</tr>
<tr class="even">
<td><p>HashAlgorithmBitMap</p></td>
<td><p>Supported hash algorithms</p></td>
</tr>
<tr class="odd">
<td><p>SupportedEventLogs</p></td>
<td><p>Bitmap of supported event log formats (see above)</p></td>
</tr>
<tr class="even">
<td><p>TrEEPresentFlag</p></td>
<td><p>False = TrEE not present</p></td>
</tr>
<tr class="odd">
<td><p>MaxCommandSize</p></td>
<td><p>Max size (in bytes) of a command that can be sent to the TrEE</p></td>
</tr>
<tr class="even">
<td><p>MaxResponseSize</p></td>
<td><p>Max size (in bytes) of a response that can be provided by the TrEE</p></td>
</tr>
<tr class="odd">
<td><p>ManufacturerID</p></td>
<td><p>4-byte Vendor ID (see [TCG07], “TPM Capabilities Vendor ID” section)</p></td>
</tr>
</tbody>
</table>

 

**Description**

The EFI\_TREE\_PROTOCOL Get Capability function call provides EFI protocol version and capability information as well as state information about the TrEE. The caller must set the Size field of the TREE\_BOOT\_SERVICE\_CAPABILITY structure allocated. It is expected future versions of this function call may add additional fields to the structure. The Size value passed in will enable the function to only populate fields the caller allocated memory for. For example:

ProtocolCapability.Size = sizeof(TREE\_BOOT\_SERVICE\_CAPABILITY);

For this version of the specification:

1.  If the This or the ProtocolCapability parameters are NULL, the functional call will return EFI\_INVALID\_PARAMETER.

2.  If the input ProtocolCapability.Size &lt; sizeof(TREE\_BOOT\_SERVICE\_CAPABILITY) the function will set ProtocolCapability.Size equal to sizeof(TREE\_BOOT\_SERVICE\_CAPABILITY) as defined in this specification and will return the error code EFI\_BUFFER\_TOO\_SMALL, the values of the remaining fields will be undefined.

3.  The following return values MUST be set:

    ProtocolCapability.StructureVersion.Major = 1

    ProtocolCapability.StructureVersion.Minor = 0

    ProtocolCapability.ProtocolVersion.Major = 1

    ProtocolCapability.ProtocolVersion.Minor = 0

4.  If the platform does not have a TrEE then the following values MUST be returned:

    ProtocolCapability.SupportedEventLogs = 0

    ProtocolCapability.HashAlgorithmBitmap = 0

    ProtocolCapability.TrEEPresentFlag = FALSE

    ProtocolCapability.MaxCommandSize = 0

    ProtocolCapability.MaxResponseSize = 0

    ProtocolCapability.ManufacturerID = 0

5.  The minimum MaxCommandSize and MaxResponseSize MUST be 0x500 (or greater) for Windows.

**Status Codes Returned**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>EFI_SUCCESS</p></td>
<td><p>Operation completed successfully.</p></td>
</tr>
<tr class="even">
<td><p>EFI_DEVICE_ERROR</p></td>
<td><p>The command was unsuccessful. The <em>ProtocolCapability</em> variable will not be populated.</p></td>
</tr>
<tr class="odd">
<td><p>EFI_INVALID_PARAMETER</p></td>
<td><p>One or more of the parameters are incorrect. The <em>ProtocolCapability</em> variable will not be populated.</p></td>
</tr>
<tr class="even">
<td><p>EFI_BUFFER_TOO_SMALL</p></td>
<td><p>The <em>ProtocolCapability</em> variable is too small to hold the full response. It will be partially populated (required <em>Size</em> field will be set).</p></td>
</tr>
</tbody>
</table>

 

### <span id="3.4_EFI_TREE_PROTOCOL.GetEventLog"></span><span id="3.4_efi_tree_protocol.geteventlog"></span><span id="3.4_EFI_TREE_PROTOCOL.GETEVENTLOG"></span>3.4 EFI\_TREE\_PROTOCOL.GetEventLog

The EFI\_TREE\_PROTOCOL Get Event Log function call allows a caller to retrieve the address of a given event log and its last entry.

**Prototype**

``` syntax
typedef
EFI_STATUS
(EFIAPI *EFI_TREE_GET_EVENT_LOG) (
  IN  EFI_TREE_PROTOCOL      *This,
  IN  TREE_EVENT_LOG_FORMATEventLogFormat,
  OUT EFI_PHYSICAL_ADDRESS*EventLogLocation,
  OUT EFI_PHYSICAL_ADDRESS*EventLogLastEntry,
  OUT BOOLEAN*EventLogTruncated
);
```

**Parameters**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>EventLogFormat</em></p></td>
<td><p>The type of the event log for which the information is requested.</p></td>
</tr>
<tr class="even">
<td><p><em>EventLogLocation</em></p></td>
<td><p>A pointer to the memory address of the event log.</p></td>
</tr>
<tr class="odd">
<td><p><em>EventLogLastEntry</em></p></td>
<td><p>If the Event Log contains more than one entry, this is a pointer to the address of the start of the last entry in the event log in memory. For information about what values are returned in this parameter in the special cases of an empty Event Log or an Event Log with only one entry, see the Description section below.</p></td>
</tr>
<tr class="even">
<td><p><em>EventLogTruncated</em></p></td>
<td><p>If the Event Log is missing at least one entry because an event would have exceeded the area allocated for events, this value is set to TRUE. Otherwise, the value will be FALSE and the Event Log will be complete.</p></td>
</tr>
</tbody>
</table>

 

**Description**

The firmware manages an Event Log of the measurements recorded in the TrEE during the boot process. During the boot process, before UEFI platform initialization, an entry is made in the Event Log for each measurement extended in the TrEE. In the UEFI environment, each time a call is made to HashLogExtendEvent to extend a measurement in the TrEE, an event is generally recorded in the Event Log containing the extended measurement. If the area allocated by firmware for the Event Log was too small to hold all events added, the function call indicates the Event Log was truncated and has missing entries. This version of the specification only requires an Event Log of SHA1 measurements to be maintained. Future versions of this specification may maintain additional Event Logs supporting different hash algorithms.

The Event Log area returned by this function is released when ExitBootServices ( ) is called. Callers of this method MUST not access the area after ExitBootServices ( ) has been called.For this version of the specification:

1.  If EventLogFormat does not equal TREE\_EVENT\_LOG\_FORMAT\_TCG\_1\_2, the function call MUST return EFI\_INVALID\_PARAMETER.

2.  If no TrEE is present the function MUST set the following values and return EFI\_SUCCESS:

    1.  EventLogLocation = NULL

    2.  EventLogLastEntry = NULL

    3.  EventLogTruncated = FALSE

3.  The EventLogLocation value MUST be set to the start of the specified event log format in memory

4.  If the specified event log:

    1.  does not contain any events then EventLogLastEntry MUST be set to 0

    2.  contains exactly one entry then EventLogLastEntry MUST be set to the same value as EventLogLocation

    3.  contains more than one event then EventLogLastEntry MUST be set to the start address of the last event of the specified Event Log

5.  If a prior call to EFI\_TREE\_PROTOCOL.HashLogExtendEvent returned EFI\_VOLUME\_FULL then EventLogTruncated MUST be set to TRUE, otherwise it MUST be set to FALSE.

**Status Codes Returned**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>EFI_SUCCESS</p></td>
<td><p>Operation completed successfully.</p></td>
</tr>
<tr class="even">
<td><p>EFI_INVALID_PARAMETER</p></td>
<td><p>One or more of the parameters are incorrect (e.g. asking for an event log whose format is not supported).</p></td>
</tr>
</tbody>
</table>

 

### <span id="3.5_EFI_TREE_PROTOCOL.HashLogExtendEvent"></span><span id="3.5_efi_tree_protocol.hashlogextendevent"></span><span id="3.5_EFI_TREE_PROTOCOL.HASHLOGEXTENDEVENT"></span>3.5 EFI\_TREE\_PROTOCOL.HashLogExtendEvent

The EFI\_TREE\_PROTOCOL HashLogExtendEvent function call provides callers with an opportunity to extend and optionally log events without requiring knowledge of actual TPM commands.The extend operation will occur even if this function cannot create an event log entry (e.g. due to the event log being full).

**Prototype**

``` syntax
typedef
EFI_STATUS
(EFIAPI * EFI_TREE_HASH_LOG_EXTEND_EVENT) (
  IN EFI_TREE_PROTOCOL*This,
  IN UINT64Flags,
  IN EFI_PHYSICAL_ADDRESSDataToHash,
  IN UINT64DataToHashLen,
  IN TrEE_EVENT*Event,
);
```

**Parameters**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>This</em></p></td>
<td><p>Indicates the calling context.</p></td>
</tr>
<tr class="even">
<td><p><em>Flags</em></p></td>
<td><p>Bitmap providing additional information (see below).</p></td>
</tr>
<tr class="odd">
<td><p><em>DataToHash</em></p></td>
<td><p>Physical address of the start of the data buffer to be</p></td>
</tr>
<tr class="even">
<td><p>hashed.</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><em>DataToHashLen</em></p></td>
<td><p>The length in bytes of the buffer referenced by <em>DataToHash</em>.</p></td>
</tr>
<tr class="even">
<td><p><em>Event</em></p></td>
<td><p>Pointer to data buffer containing information about the event.</p></td>
</tr>
</tbody>
</table>

 

Related Definitions

``` syntax
#pragma pack(1)
typedef struct _TrEE_EVENT {
  UINT32Size;            
  TrEE_EVENT_HEADERHeader;
  UINT8Event[ANYSIZE_ARRAY];
} TrEE_EVENT;
typedef struct _TrEE_EVENT_HEADER {
  UINT32HeaderSize;
  UINT16HeaderVersion;
  TrEE_PCRINDEXPCRIndex;
  TrEE_EVENTTYPEEventType;
} TrEE_EVENT_HEADER;
#pragma pack()
typedef UINT32 TrEE_PCRINDEX;
typedef UINT32 TrEE_EVENTTYPE;
```

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>Size</em></p></td>
<td><p>Total size of the event including the Size component, the header and the <em>Event</em> data.</p></td>
</tr>
<tr class="even">
<td><p><em>HeaderSize</em></p></td>
<td><p>Size of the event header itself (sizeof(TrEE_EVENT_HEADER)).</p></td>
</tr>
<tr class="odd">
<td><p><em>HeaderVersion</em></p></td>
<td><p>Header version. For this version of this specification, the value shall be 1.</p></td>
</tr>
<tr class="even">
<td><p><em>PCRIndex</em></p></td>
<td><p>Index of the PCR that shall be extended (0 – 23).</p></td>
</tr>
<tr class="odd">
<td><p><em>EventType</em></p></td>
<td><p>Type of the event that shall be extended (and optionally logged).</p></td>
</tr>
</tbody>
</table>

 

**Flag Values**

The Flags variable is a bitmap providing additional data as follows:

``` syntax
#define TREE_EXTEND_ONLY 0x0000000000000001
```

This bit is shall be set when an event shall be extended but not logged.

``` syntax
#define PE_COFF_IMAGE 0x0000000000000010
```

This bit shall be set when the intent is to measure a PE/COFF image.

**Description**

The EFI\_TREE\_PROTOCOL Hash Log Extend Event function call calculates the measurement of a data buffer (possibly containing a PE/COFF binary image) and causes the TrEE driver to extend the measurement. In addition, the service optionally creates an event log entry and appends it to the Event Log for each event log format supported by the service. The service allows a caller to make use of the TrEE without knowing anything about specific TrEE commands.

The use of this function to measure PE/COFF images must be done before relocations have been applied to the image. Note: Use caution using this method to measure PE/COFF images. Generally implementations that load PE/COFF images strip important data during the load process from the image and may change the image section alignment in memory. The net result is calculating the hash of an in-memory image does not match the actual measurement for the image as properly calculated when it is loaded from storage media.

Upon invocation, the function shall perform the following actions:

1.  If any of the parameters This, DataToHash, or Event are NULL, the function MUST return EFI\_INVALID\_PARAMETER.

2.  If the Event.Size is less than Event.Header.HeaderSize + sizeof(UINT32), the function MUST return EFI\_INVALID\_PARAMETER.

3.  If the Event.Header.PCRIndex is not 0 through 23, inclusive, the function MUST return EFI\_INVALID\_PARAMETER.

4.  If the Flags bitmap has the PE\_COFF\_IMAGE bit SET but the PE/COFF image is corrupt or not understood the function MUST return EFI\_UNSUPPORTED.

5.  The function allows any value for the Event.Header.EventType parameter.

6.  The function MUST calculate the digest (measurement) of the data starting at DataToHash with a length of DataToHashLen. When the PE\_COFF\_IMAGE bit is set, the function MUST calculate the measurement of the PE/COFF image in accordance with “Measuring a PE/COFF image” in Appendix A below.

7.  The function MUST successfully send the TPM2\_PCR\_Extend command to the TrEE to extend the PCR indicated by Event.Header.PCRIndex with the measurement digest. If the command cannot be sent successfully, the function must return EFI\_DEVICE\_ERROR. If the firmware supports more algorithms than SHA1 it may calculate digests using other algorithms and extend them too.

8.  If a previous call to this function returned EFI\_VOLUME\_FULL and the TREE\_EXTEND\_ONLY bit is set in the Flags parameter, the function MUST return EFI\_VOLUME\_FULL. (No attempt is made to add the event log entry to the event log(s).)

9.  The function MUST build a TCG Event Log entry as follows: (Note: The TCG\_PCR\_EVENT structure is defined in \[TCG06b\] and shall be considered byte-aligned.)

    1.  TCG\_PCR\_EVENT.PCRIndex = Event.Header.PCRIndex

    2.  TCG\_PCR\_EVENT.EventType = Event.Header.EventType

    3.  TCG\_PCR\_EVENT.Digest = &lt;the SHA1 measurement digest calculated above&gt;

    4.  TCG\_PCR\_EVENT.EventSize = Event.Size – sizeof(UINT32) - Event.Header.HeaderSize

    5.  TCG\_PCR\_EVENT.Event = Event.Event (Note: this is a memory copy of EventSize bytes)

10. The function MAY build similar event log entries for other supported Event Log formats.

11. If the TCG\_PCR\_EVENT Event Log entry created above does not fit in the area allocated for the TrEE Event Log Format TCG 1.2 Event Log, the function MUST return EFI\_VOLUME\_FULL.

12. If the firmware supports additional Event Log formats and any of the events created for those event logs would exceed the area allocated for the Event Log, the function MUST return EFI\_VOLUME\_FULL.

13. The function MUST append the events created to their corresponding event logs and the service MUST update its internal pointer to the start of the last event for each Event Log.

**Status Codes Returned.**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p>
<p>EFI_SUCCESS</p></td>
<td><p>Operation completed successfully.</p></td>
</tr>
<tr class="even">
<td><p>EFI_DEVICE_ERROR</p></td>
<td><p>The command was unsuccessful.</p></td>
</tr>
<tr class="odd">
<td><p>EFI_VOLUME_FULL</p></td>
<td><p>The extend operation occurred, but the event could not be written to one or more event logs.</p></td>
</tr>
<tr class="even">
<td><p>EFI_INVALID_PARAMETER</p></td>
<td><p>One or more of the parameters are incorrect.</p></td>
</tr>
<tr class="odd">
<td><p>EFI_UNSUPPORTED</p></td>
<td><p>The PE/COFF image type is not supported.</p></td>
</tr>
</tbody>
</table>

 

### <span id="3.6_EFI_TREE_PROTOCOL.SubmitCommand"></span><span id="3.6_efi_tree_protocol.submitcommand"></span><span id="3.6_EFI_TREE_PROTOCOL.SUBMITCOMMAND"></span>3.6 EFI\_TREE\_PROTOCOL.SubmitCommand

This service enables the sending of commands to the TrEE.

**Prototype**

``` syntax
typedef
EFI_STATUS
(EFIAPI *EFI_TREE_SUBMIT_COMMAND) (
  IN EFI_TREE_PROTOCOL*This,
  IN UINT32InputParameterBlockSize,
  IN UINT8*InputParameterBlock,
  IN UINT32OutputParameterBlockSize,
  IN UINT8*OutputParameterBlock 
);
```

**Parameters**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p>
<p><em>This</em></p></td>
<td><p>Indicates the calling context.</p></td>
</tr>
<tr class="even">
<td><p><em>InputParameterBlockSize</em></p></td>
<td><p>Size of the TrEE input parameter block.</p></td>
</tr>
<tr class="odd">
<td><p><em>InputParameterBlock</em></p></td>
<td><p>Pointer to the TrEE input parameter block.</p></td>
</tr>
<tr class="even">
<td><p><em>OutputParameterBlockSize</em></p></td>
<td><p>Size of the TrEE output parameter block.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutputParameterBlock</em></p></td>
<td><p>Pointer to the TrEE output parameter block.</p></td>
</tr>
</tbody>
</table>

 

**Description**

The EFI\_TREE\_PROTOCOL Submit Command function call provides a pass-through capability from the caller to the system’s TrEE.

The caller is responsible for building the command byte-stream to be sent to the TrEE and is also responsible for interpreting the resulting byte-stream returned by the TrEE. The TrEE in and out operands for each TrEE command are defined elsewhere.

Note that the returned status codes reflect the outcome of the function invocation and not the success (or failure) of the underlying TrEE command.

The TPM 2.0 MUST not return TPM2\_RC\_RETRY prior to the completion of the call to ExitBootServices(). (The reason for this requirement is the return code would block the boot process until the TPM command could be compeleted.)

The TPM 2.0 MUST have access to its persistent storage prior to the call to ExitBootServices completing. If TPM 2.0 implementation MAY not have access to persistent storage after the call to ExitBootServices, please contact Microsoft for additional requirements.

**Status Codes Returned**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>EFI_SUCCESS</p></td>
<td><p>The command byte stream was successfully sent to the device and a response was successfully received.</p></td>
</tr>
<tr class="even">
<td><p>EFI_DEVICE_ERROR</p></td>
<td><p>The command was not successfully sent to the device or a response was not successfully received from the device.</p></td>
</tr>
<tr class="odd">
<td><p>EFI_INVALID_PARAMETER</p></td>
<td><p>One or more of the parameters are incorrect.</p></td>
</tr>
<tr class="even">
<td><p>EFI_BUFFER_TOO_SMALL</p></td>
<td><p>The output parameter block is too small.</p></td>
</tr>
</tbody>
</table>

 

## <span id="References"></span><span id="references"></span><span id="REFERENCES"></span>References


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[MSFT08]</p></td>
<td><p>Microsoft Corporation, “Windows Authenticode Portable Executable Signature Format,” Version 1.0, March 21, 2008.</p></td>
</tr>
<tr class="even">
<td><p>[RFC2119]</p></td>
<td><p>Bradner, S., “Keywords for Use in RFCs to Indicate Requirement Levels,” IETF RFC 2119, March 1997.</p></td>
</tr>
<tr class="odd">
<td><p>[TCG06a]</p></td>
<td><p>Trusted Computing Group, “TCG EFI Protocol,” Version 1.20 Revision 1.00, June 9, 2006.</p></td>
</tr>
<tr class="even">
<td><p>[TCG06b]</p></td>
<td><p>Trusted Computing Group, “TCG EFI Platform Specification,” Version 1.20 Revision 1.0, June 7, 2006.</p></td>
</tr>
<tr class="odd">
<td><p>[TCG07]</p></td>
<td><p>Trusted Computing Group, “TCG Vendor ID Registry,” Version 1.0, Revision 0.1, August 31, 2007.</p></td>
</tr>
<tr class="even">
<td><p>[UEFI12]</p></td>
<td><p>UEFI, “Unified Extensible Firmware Interface Specification,” Version 2.3.1 Errata C,</p></td>
</tr>
<tr class="odd">
<td><p>June 2012.</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <span id="Appendix_A__Static_Root_of_Trust_Measurements"></span><span id="appendix_a__static_root_of_trust_measurements"></span><span id="APPENDIX_A__STATIC_ROOT_OF_TRUST_MEASUREMENTS"></span>Appendix A: Static Root of Trust Measurements

>[!IMPORTANT]
>  
Appendix A implementation of PCR\[7\] measurements is mandatory for InstantGo systems.

 

At a high level, firmware is responsible for measuring the following components during boot:

-   Platform firmware that contains or measures the UEFI Boot Services and UEFI Runtime Services

-   Security relevant variables associated with platform firmware

-   UEFI drivers or boot applications loaded separately

-   Variables associated with separately loaded UEFI Drivers or UEFI Boot applications

The above measurements are defined by the TCG EFI Platform specification \[TCG06b\] Sections 5.1 – 5.5 and are not referred to further herein. Measurements into PCR\[1\] and PCR\[3\] are optional depending on platform configuration.

For Windows, PCR\[7\] is used to reflect the UEFI 2.3.1 Secure Boot policy. This policy relies on the firmware authenticating all boot components launched prior to the UEFI environment and the UEFI platform initialization code (or earlier firmware code) invariantly recording the Secure Boot policy information into PCR\[7\].

Platform firmware adhering to the policy must therefore measure the following values into PCR\[7\]:

1.  The contents of the PK variable

2.  The contents of the KEK variable

3.  The contents of the EFI\_IMAGE\_SECURITY\_DATABASE variable

4.  The contents of the EFI\_IMAGE\_SECURITY\_DATABASE1 variable

5.  Entries in the EFI\_IMAGE\_SECURITY\_DATABASE that are used to validate EFI Drivers or EFI Boot Applications in the boot path

6.  The contents of the SecureBoot variable

Because of the above, UEFI variables PK, KEK, EFI\_IMAGE\_SECURITY\_DATABASE, EFI\_IMAGE\_SECURITY\_DATABASE1 and SecureBoot SHALL NOT be measured into PCR\[3\].

In addition, if the platform provides a firmware debugger which may be launched prior to the UEFI environment, it MUST record this fact in PCR\[7\]. Likewise, if the platform provides a debugger for the UEFI environment, launch of the debugger MUST be recorded in PCR\[7\].

**Implementation Note**

The UEFI LoadImage function MUST record measurements in PCR\[2\] or PCR\[4\] per events described in \[TCG06b\] and also PCR\[7\] per events described in the section “Measuring UEFI Configuration into PCR\[7\]” below. To determine whether an image measurement applies to PCR\[2\] or PCR\[4\], LoadImage MUST examine the Subsystem field in the PE/COFF image. The values IMAGE\_SUBSYSTEM\_EFI\_BOOT\_SERVICE\_DRIVER, IMAGE\_SUBSYSTEM\_EFI\_RUNTIME\_DRIVER and IMAGE\_SUBSYSTEM\_EFI\_ROM correspond to PCR\[2\]. The value IMAGE\_SUBSYSTEM\_EFI\_APPLICATION corresponds to PCR\[4\]. If the loaded image is some other type, it MUST be recorded in PCR\[4\]. Images that LoadImage fails to load due to (a) signature verification failure or (b) because the image does not comply with currently enforced UEFI 2.3.1 Secure Boot policy do not need to be measured in a PCR.

****Related Definitions

``` syntax
#define EV_EFI_VARIABLE_DRIVER_CONFIG \
                                  0x80000001 /* Defined in [TCG06b] */
#define EV_EFI_ACTION             0x80000007 /* Defined in [TCG06b] */
#define EV_EFI_VARIABLE_AUTHORITY 0x800000E0

This specification requires a modified TCG structure definition for EFI_VARIABLE_DATA.  The revised structure is:
typedef struct {
  EFI_GUIDVariableName;
  UINT64        UnicodeNameLength;    // The TCG Defintion used UINTN
  UINT64        VariableDataLength;   // The TCG Defintion used UINTN
  CHAR16       UnicodeName[1];
  INT8         VariableData[1];   
} EFI_VARIABLE_DATA;
```

**Measuring a PE/COFF Image**

When measuring a PE/COFF image, the EventType shall be as defined in \[TCG06b\] (for example, when measuring an EFI Boot Application, the EventType shall be EV\_EFI\_BOOT\_SERVICES\_APPLICATION) and the Event value shall be the value of the EFI\_IMAGE\_LOAD\_EVENT structure defined in \[TCG06b\].

The HashLogExtendEvent service MUST hash the PE/COFF image in accordance with the procedure specified in “Calculating the PE Image Hash” section of \[MSFT08\].

**Measuring UEFI Configuration into PCR\[7\]**

For all EFI variable value events, the EventType shall be EV\_EFI\_VARIABLE\_DRIVER\_CONFIG defined above and the Event value shall be the value of the EFI\_VARIABLE\_DATA structure defined above in this specification (this structure shall be considered byte-aligned). The measurement digest shall be the SHA-1 hash of the event data which is the EFI\_VARIABLE\_DATA structure. (Note: This is a different digest than the one specified by \[TCG06b\].) The EFI\_VARIABLE\_DATA.UnicodeNameLength value is the number of CHAR16 characters (not the number of bytes). The EFI\_VARIABLE\_DATA.UnicodeName contents MUST NOT include a null terminator. If reading the EFI variable returns EFI\_NOT\_FOUND, the EFI\_VARIABLE\_DATA.VariableDataLength field MUST be set to zero and EFI\_VARIABLE\_DATA.VariableData field will have a size of zero.

1.  If the platform provides a firmware debugger mode which may be used prior to the UEFI environment or if the platform provides a debugger for the UEFI environment, then the platform SHALL extend an EV\_EFI\_ACTION event as specified in \[TCG06b\] into PCR\[7\] before allowing use of the debugger. The event string shall be “UEFI Debug Mode”. Further, the platform MUST create a TCG Event Log entry as follows:

    1.  TCG\_PCR\_EVENT.PCRIndex = 7

    2.  TCG\_PCR\_EVENT.EventType = EV\_EFI\_ACTION

    3.  TCG\_PCR\_EVENT.Digest = &lt;the SHA-1 digest of the string value “UEFI Debug Mode” without the terminating NULL character&gt;

    4.  TCG\_PCR\_EVENT.EventSize = strlen(“UEFI Debug Mode”)

    5.  TCG\_PCR\_EVENT.Event = “UEFI Debug Mode”

    The platform MAY build similar event log entries for other supported Event Log formats.

2.  Before executing any code not cryptographically authenticated as being provided by the Platform Manufacturer, the Platform Manufacturer firmware MUST measure the following values in the order listed using the EV\_EFI\_VARIABLE\_DRIVER\_CONFIG event type to PCR\[7\]:

    1.  SecureBoot variable value

    2.  The PK variable value

    3.  The KEK variable value

    4.  The EFI\_IMAGE\_SECURITY\_DATABASE\_GUID/EFI\_IMAGE\_SECURITY\_DATABASE variable value

    5.  The EFI\_IMAGE\_SECURITY\_DATABASE\_GUID/EFI\_IMAGE\_SECURITY\_DATABASE1 variable value

3.  If the platform supports changing any of the following UEFI policy variables after they are initially measured in PCR\[7\] and before **ExitBootServices ( )** has completed without unconditionally restarting the platform, it MUST measure the variable again immediately upon change. Additionally the normal update process for setting any of the UEFI variables below MUST occur before the initial measurement in PCR\[7\] or after the call to **ExitBootServices()** has completed.

    1.  SecureBoot variable value

    2.  The PK variable value

    3.  The KEK variable value

    4.  The EFI\_IMAGE\_SECURITY\_DATABASE\_GUID/EFI\_IMAGE\_SECURITY\_DATABASE variable value

    5.  The EFI\_IMAGE\_SECURITY\_DATABASE\_GUID/EFI\_IMAGE\_SECURITY\_DATABASE1 variable value

4.  The system SHALL measure the EV\_SEPARATOR event in PCR\[7\]. (This occurs at the same time the separator is measured to PCR\[0\] through PCR\[7\].)

5.  Before launching an EFI Driver or an EFI Boot Application (and regardless of whether the launch is due to the EFI Boot Manager picking an image from the DriverOrder or BootOrder UEFI variables or an already launched image calling the UEFI LoadImage() function), the UEFI firmware SHALL measure the entry in the EFI\_IMAGE\_SECURITY\_DATABASE\_GUID/EFI\_IMAGE\_SECURITY\_DATABASE variable that was used to validate the EFI image into PCR\[7\]. The measurement SHALL occur in conjunction with image load. For this event, the EventType shall be EV\_EFI\_VARIABLE\_AUTHORITY and the Event value shall be the value of the EFI\_VARIABLE\_DATA structure (the structure is defined above in this specification with a different definition than the TCG specification). The EFI\_VARIABLE\_DATA.VariableData value shall be the EFI\_SIGNATURE\_DATA value from the EFI\_SIGNATURE\_LIST that contained the authority that was used to validate the image and the EFI\_VARIABLE\_DATA.VariableName shall be set to EFI\_IMAGE\_SECURITY\_DATABASE\_GUID. The EFI\_VARIABLE\_DATA.UnicodeName shall be set to the value of EFI\_IMAGE\_SECURITY\_DATABASE. The value shall not include the terminating NULL character.

6.  Before launching any additional EFI Drivers or EFI Boot Applications, the UEFI firmware SHALL check if the entry in the EFI\_IMAGE\_SECURITY\_DATABASE\_GUID/EFI\_IMAGE\_SECURITY\_DATABASE variable which validates the EFI image has previously been measured with the EV\_EFI\_VARIABLE\_AUTHORITY event type in PCR\[7\]. If it has not been, it MUST be measured as described in the previous step. If it has been measured previously, it MUST NOT be measured again.

>[!NOTE]
>  
A measurement example for PCR\[7\] measurements is available upon request from Microsoft.

 

 

 






