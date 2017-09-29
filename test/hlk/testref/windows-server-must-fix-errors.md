---
title: Windows Server Must-Fix Code Analysis and Static Driver Verifier Errors affecting Network and Storage Adapter Vendors
description: Windows Server Must-Fix Code Analysis and Static Driver Verifier Errors affecting Network and Storage Adapter Vendors
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 24D3A2CA-97A4-4051-8CBC-479861039789
---

# <span id="p_hlk_test.windows_server_must-fix_errors"></span>Windows Server Must-Fix Code Analysis and Static Driver Verifier Errors affecting Network and Storage Adapter Vendors


## <span id="Overview"></span><span id="overview"></span><span id="OVERVIEW"></span>Overview


If your company manufactures a Network or Storage adapter that is to be Certified for Windows Server 2016, there are Code Analysis (CA) and Static Driver Verifier (SDV) driver source code errors which are considered Must-Fix in order for the driver to be successfully certified for Windows Server 2016.

The SDV user interface highlights these errors specifically for NDIS and Network related interface calls that are incorrect and considered Must-Fix in order to get a driver Certified for Windows Server 2016. The Storage interface calls are planned to be called out as well, but that functionality is not complete at this time.

The CA user interface does not currently highlight the errors it detects in Network and Storage driver sources that are incorrect and considered Must-Fix in order to get a driver Certified for Windows Server 2016. That work is planned for future versions of the CA tool.

## <span id="Criteria_for_Rules_Selection_as_Must-Fix"></span><span id="criteria_for_rules_selection_as_must-fix"></span><span id="CRITERIA_FOR_RULES_SELECTION_AS_MUST-FIX"></span>Criteria for Rules Selection as Must-Fix


The criteria for the SDV and CA Rules which have been selected for Network and Storage adapter drivers as being Must-Fix in order to get a driver Certified for Windows Server 2016 are as follows:

-   Accuracy - the Rule finds code errors with a low false failure rate
-   Impact - the code error can cause data corruption, hangs or crashes
-   Data Driven – the code error caused a problem in a driver that crashed and was analyzed as part of Microsoft’s Online Crash Analysis tool, OCA.
-   Experience - the code error is one included in the internal bar used by Microsoft, with high impact and security issues always being fixed
-   Minimal Annotation - there is low dependency on annotations of the driver’s sources in order for the CA and SDV tools to function. Note however that some annotations are required.

>[!NOTE]
>  
There are a few CA Rules below for which there are no links in MSDN, which are called out below. The functionality for checking these in Visual Studio Express 2013 does not exist, so other versions of Visual Studio must be used. However, the errors are generally self-explanatory.

For all other Rules, the link can be found by searching on MSDN.

For convenience, there is a short snippet of text from the links, but the links themselves usually contain more text and code examples of both correct and incorrect usage to illustrate the needed change(s).

 

## <span id="CA_Rules"></span><span id="ca_rules"></span><span id="CA_RULES"></span>CA Rules


<span id="C6001_USING_UNINITIALIZED_MEMORY_"></span><span id="c6001_using_uninitialized_memory_"></span>C6001:USING UNINITIALIZED MEMORY   
This warning is reported when an uninitialized local variable is used before it is assigned a value. This could lead to unpredictable results.

<span id="C6011_DEREFERENCING_A_NULL_POINTER_"></span><span id="c6011_dereferencing_a_null_pointer_"></span>C6011:DEREFERENCING A NULL POINTER   
This warning indicates that a null pointer is being dereferenced. If the pointer value is invalid, the result is undefined.

<span id="C6014_LEAKING_MEMORY_"></span><span id="c6014_leaking_memory_"></span>C6014:LEAKING MEMORY   
This warning indicates that the specified pointer points to allocated memory or some other allocated resource that has not been freed.

<span id="C6063_MISSING_STRING_ARGUMENT_TO_FORMAT_FUNCTION_"></span><span id="c6063_missing_string_argument_to_format_function_"></span>C6063:MISSING\_STRING\_ARGUMENT\_TO\_FORMAT\_FUNCTION   
This defect can cause crashes and buffer overflows (if the called function is of the sprintf family), as well as potentially incorrect output.

<span id="C6214_CAST_HRESULT_TO_BOOL_"></span><span id="c6214_cast_hresult_to_bool_"></span>C6214:CAST\_HRESULT\_TO\_BOOL   
Any comparison that uses the Boolean variable to test for HRESULT success or failure could lead to incorrect results.

<span id="C6215_CAST_BOOL_TO_HRESULT_"></span><span id="c6215_cast_bool_to_hresult_"></span>C6215:CAST\_BOOL\_TO\_HRESULT   
Casting a Boolean type to an HRESULT and then using it in a test expression will yield an incorrect result.

<span id="C6216_COMPILER_INSERTED_CAST_BOOL_TO_HRESULT_"></span><span id="c6216_compiler_inserted_cast_bool_to_hresult_"></span>C6216:COMPILER\_INSERTED\_CAST\_BOOL\_TO\_HRESULT   
The typical failure value for functions that return a Boolean false is a success status when it is tested as an HRESULT. This is likely to lead to incorrect results.

<span id="C6230_USING_HRESULT_IN_BOOLEAN_CONTEXT_"></span><span id="c6230_using_hresult_in_boolean_context_"></span>C6230:USING\_HRESULT\_IN\_BOOLEAN\_CONTEXT   
This warning indicates that a bare HRESULT is being used in a context, such as if statement, where a Boolean result is expected. This is likely to yield incorrect results.

<span id="C6248_CREATINGNULLDACL_"></span><span id="c6248_creatingnulldacl_"></span>C6248:CREATINGNULLDACL   
This warning identifies a call that sets a SECURITY\_DESCRIPTOR's DACL field to null, which grants full access to any user who requests it; normal security checking is not performed with respect to the object. Objects that have null DACLs can have their security descriptors altered by malicious users so that no one has access to the object.

<span id="C6259_DEADCODEINBITORLIMITEDSWITCH_"></span><span id="c6259_deadcodeinbitorlimitedswitch_"></span>C6259:DEADCODEINBITORLIMITEDSWITCH   
This warning indicates unreachable code caused by the result of a bitwise-AND (&) comparison in a switch expression

<span id="C6260_USEOFBYTEAREA_"></span><span id="c6260_useofbytearea_"></span>C6260:USEOFBYTEAREA   
This warning indicates that the results of two sizeof operations have been multiplied together.

<span id="C6268_MISPARENTHESIZED_CASTS_"></span><span id="c6268_misparenthesized_casts_"></span>C6268:MISPARENTHESIZED\_CASTS   
This warning indicates that a complex cast expression might involve a precedence problem when performing pointer arithmetic. In some cases, this defect causes incorrect behavior or a program crash.

<span id="C6276_CHAR_TO_WCHAR_CAST_"></span><span id="c6276_char_to_wchar_cast_"></span>C6276:CHAR\_TO\_WCHAR\_CAST   
This warning indicates a potentially incorrect cast from an ANSI string (char\_t\*) to a UNICODE string (wchar\_t \*). Using such strings with the wcs\* library of functions could cause buffer overruns and access violations.

<span id="C6277_CREATEPROCESS_ESCAPE_"></span><span id="c6277_createprocess_escape_"></span>C6277:CREATEPROCESS\_ESCAPE   
This warning indicates that the application name parameter is null and there might be spaces in the executable path name. A malicious user might insert a rogue executable with the same name earlier in the path.

<span id="C6281_BITWISERELATIONPRECEDENCEERROR_"></span><span id="c6281_bitwiserelationprecedenceerror_"></span>C6281:BITWISERELATIONPRECEDENCEERROR   
This warning indicates a possible error in the operator precedence. This might produce incorrect results.

<span id="C6282_ASSIGNMENTREPLACESTEST_"></span><span id="c6282_assignmentreplacestest_"></span>C6282:ASSIGNMENTREPLACESTEST   
This warning indicates that an assignment of a constant to a variable was detected in a test context.

<span id="C6284_OBJECT_AS_STRING_ARGUMENT_TO_FORMAT_FUNCTION_"></span><span id="c6284_object_as_string_argument_to_format_function_"></span>C6284:OBJECT\_AS\_STRING\_ARGUMENT\_TO\_FORMAT\_FUNCTION   
This warning indicates that the format string specifies a string, for example, a %s specification for printf or scanf, but a C++ object has been passed instead.

<span id="C6287_REDUNDANTTEST_"></span><span id="c6287_redundanttest_"></span>C6287:REDUNDANTTEST   
This warning indicates that a redundant element was detected in an expression.

<span id="C6288_MUTUALINCLUSIONOVERANDISFALSE_"></span><span id="c6288_mutualinclusionoverandisfalse_"></span>C6288:MUTUALINCLUSIONOVERANDISFALSE   
This warning indicates that in a test expression, a variable is being tested against two different constants and the result depends on both conditions being true.

<span id="C6289_MUTUALEXCLUSIONOVERORISTRUE_"></span><span id="c6289_mutualexclusionoveroristrue_"></span>C6289:MUTUALEXCLUSIONOVERORISTRUE   
This warning indicates that in a test expression a variable is being tested against two different constants and the result depends on either condition being true. This always evaluates to true.

<span id="C6290_LOGICALNOTBITWISEAND_"></span><span id="c6290_logicalnotbitwiseand_"></span>C6290:LOGICALNOTBITWISEAND   
This warning indicates possible confusion in the use of an operator or an operator precedence.

<span id="C6291_LOGICALNOTBITWISEOR_"></span><span id="c6291_logicalnotbitwiseor_"></span>C6291:LOGICALNOTBITWISEOR   
The ! operator yields a Boolean result, and the | (bitwise-or) operator takes two arithmetic arguments. It is difficult to judge the severity of this problem without examining the code

<span id="C6293_LOOP_INDEX_GOES_NEGATIVE_"></span><span id="c6293_loop_index_goes_negative_"></span>C6293:LOOP\_INDEX\_GOES\_NEGATIVE   
This warning indicates that a for-loop might not function as intended.

<span id="C6295_INFINITE_LOOP_"></span><span id="c6295_infinite_loop_"></span>C6295:INFINITE\_LOOP   
No link in MSDN

<span id="C6296_LOOP_ONLY_EXECUTED_ONCE_"></span><span id="c6296_loop_only_executed_once_"></span>C6296:LOOP\_ONLY\_EXECUTED\_ONCE   
This warning indicates that a for-loop might not function as intended

<span id="C6299_BITFIELD_TO_BOOL_COMPARISON_"></span><span id="c6299_bitfield_to_bool_comparison_"></span>C6299:BITFIELD\_TO\_BOOL\_COMPARISON   
This warning indicates an incorrect assumption that Booleans and bit fields are equivalent. The comparison can yield unexpected results.

<span id="C6305_SIZEOF_COUNTOF_MISMATCH_"></span><span id="c6305_sizeof_countof_mismatch_"></span>C6305:SIZEOF\_COUNTOF\_MISMATCH   
This will cause unexpected scaling in pointer arithmetic.

<span id="C6306_INCORRECT_VARARG_FUNCTIONCALL_"></span><span id="c6306_incorrect_vararg_functioncall_"></span>C6306:INCORRECT\_VARARG\_FUNCTIONCALL   
This warning indicates an incorrect function call.

<span id="C6308_REALLOCLEAK_"></span><span id="c6308_reallocleak_"></span>C6308:REALLOCLEAK   
This warning indicates a memory leak that is the result of the incorrect use of a reallocation function.

<span id="C6312_EXCEPTIONCONTINUEEXECUTION_"></span><span id="c6312_exceptioncontinueexecution_"></span>C6312:EXCEPTIONCONTINUEEXECUTION   
This warning indicates the use of the constant EXCEPTION\_CONTINUE\_EXECUTION. This can cause an infinite loop.

<span id="C6318_EXCEPTIONCONTINUESEARCH_"></span><span id="c6318_exceptioncontinuesearch_"></span>C6318:EXCEPTIONCONTINUESEARCH   
This warning indicates that if an exception occurs in the protected block of this structured exception handler, the exception will not be handled because the constant EXCECPTION\_CONTINUE\_SEARCH is used in the exception filter expression. This code is equivalent to the protected block without the exception handler block because the handler block is not executed.

<span id="C6328_FORMAT_SIZE_MISMATCH_"></span><span id="c6328_format_size_mismatch_"></span>C6328:FORMAT\_SIZE\_MISMATCH   
For C runtime character-based routines in the family name isxxx(), passing an argument of type char can have unpredictable results.

<span id="C6384_DIVIDING_SIZEOF_POINTER_"></span><span id="c6384_dividing_sizeof_pointer_"></span>C6384:DIVIDING\_SIZEOF\_POINTER   
This warning indicates that a size calculation might be incorrect.

<span id="C26110_FAILING_TO_HOLD_LOCK_BEFORE_CALLING_FUNCTION_"></span><span id="c26110_failing_to_hold_lock_before_calling_function_"></span>C26110:FAILING TO HOLD LOCK BEFORE CALLING FUNCTION   
No link in MSDN

<span id="C28126_OBJ_REFERENCE_MODE__"></span><span id="c28126_obj_reference_mode__"></span>C28126:OBJ\_REFERENCE\_MODE   
Driver is passing UserMode or KernelMode for the AccessMode parameter, instead of using Irp-&gt;RequestorMode.

<span id="C28128_FUNCTION_ASSIGNMENT_"></span><span id="c28128_function_assignment_"></span>C28128:FUNCTION\_ASSIGNMENT   
The driver directly accessed a structure member that should be accessed only by using specialized functions.

<span id="C28134_POOL_TAG_"></span><span id="c28134_pool_tag_"></span>C28134:POOL\_TAG   
No link in MSDN

<span id="C28135_KE_WAIT_LOCAL_"></span><span id="c28135_ke_wait_local_"></span>C28135:KE\_WAIT\_LOCAL   
If the first argument to KeWaitForSingleObject is a local variable, the Mode parameter must be KernelMode

<span id="C28145_MODIFYING_MDL_"></span><span id="c28145_modifying_mdl_"></span>C28145:MODIFYING\_MDL   
The opaque MDL structure should not be modified by a driver

<span id="C28157_IRQL_NOT_USED_"></span><span id="c28157_irql_not_used_"></span>C28157:IRQL\_NOT\_USED   
There is at least one path in which the driver is executing at a different IRQL when the function completes.

<span id="C28158_IRQL_NOT_SET"></span><span id="c28158_irql_not_set"></span>C28158:IRQL\_NOT\_SET  
There is at least one path in which the IRQL value is not saved in that variable.

<span id="C28163_MUST_NOT_TRY_"></span><span id="c28163_must_not_try_"></span>C28163:MUST\_NOT\_TRY   
This warning is reported when a function is of a type that should never be enclosed in a try/except block is found in a try/except block.

<span id="C28164_PVOID_"></span><span id="c28164_pvoid_"></span>C28164:PVOID   
This warning is reported when a pointer to a pointer is used in a call to a function that is expecting a pointer to an object.

<span id="C28170_NO_PAGED_CODE_"></span><span id="c28170_no_paged_code_"></span>C28170:NO\_PAGED\_CODE   
The function has been declared to be in a paged segment, but neither PAGED\_CODE nor PAGED\_CODE\_LOCKED was found

<span id="C28171_MULTIPLE_PAGED_CODE_"></span><span id="c28171_multiple_paged_code_"></span>C28171:MULTIPLE\_PAGED\_CODE   
The function has more than one instance of PAGED\_CODE or PAGED\_CODE\_LOCKED

<span id="C28719_BANNED_API_USAGE_"></span><span id="c28719_banned_api_usage_"></span>C28719:BANNED\_API\_USAGE   
This warning indicates that a function is being used that has been banned, and has a more robust and secure replacement.

<span id="C28726_BANNED_API_USAGEL2_"></span><span id="c28726_banned_api_usagel2_"></span>C28726:BANNED\_API\_USAGEL2   
This warning indicates that a function is being used that has been banned, and has a more robust and secure replacement.

<span id="C28735_BANNED_CRIMSON_API_USAGE_"></span><span id="c28735_banned_crimson_api_usage_"></span>C28735:BANNED\_CRIMSON\_API\_USAGE   
This warning indicates that a function is being used that has been banned, and has a more robust and secure replacement. ETW is the replacement

<span id="C28736_BANNED_API_ARGUMENT_USAGE_"></span><span id="c28736_banned_api_argument_usage_"></span>C28736:BANNED\_API\_ARGUMENT\_USAGE   
This warning indicates that a function is being used that has been banned, and has a more robust and secure replacement. ETW is the replacement

<span id="C28750_BANNED_API_USAGE_LSTRLEN_"></span><span id="c28750_banned_api_usage_lstrlen_"></span>C28750:BANNED\_API\_USAGE\_LSTRLEN   
This warning indicates that a function is being used that has been banned, and has better replacements.

<span id="C28751_BANNED_API_USAGE_EXALLOCATEPOOL_"></span><span id="c28751_banned_api_usage_exallocatepool_"></span>C28751:BANNED\_API\_USAGE\_EXALLOCATEPOOL   
Banned usage of ExAllocatePool and its variants. This warning indicates that a function is being used that has been banned, and has a more robust and secure replacement.

## <span id="Rules_needed_for_SDV_to_work_as_well_as_possible"></span><span id="rules_needed_for_sdv_to_work_as_well_as_possible"></span><span id="RULES_NEEDED_FOR_SDV_TO_WORK_AS_WELL_AS_POSSIBLE"></span>Rules needed for SDV to work as well as possible


The below CA outputs are not errors per se, but rather indicate where some annotation is required in order for Static Driver Verifier to work as well as possible.

<span id="C28168_"></span><span id="c28168_"></span>C28168:  
This warning supports Static Driver Verifier by checking that each function assigned into the dispatch table is annotated with one or more \_Dispatch\_type\_ annotations

<span id="C28169_"></span><span id="c28169_"></span>C28169:  
This warning supports Static Driver Verifier by checking that each function assigned into the dispatch table is annotated with one or more \_Dispatch\_type\_ annotations

<span id="C28101_"></span><span id="c28101_"></span>C28101:  
The Drivers module has inferred that the current function is a &lt;function-type&gt; function

<span id="C28022_"></span><span id="c28022_"></span>C28022:  
The function class(es) on this function do not match the function class(es) on the typedef used to define it.

<span id="C28023_"></span><span id="c28023_"></span>C28023:  
The function being assigned or passed should have a \_Function\_class\_ annotation for at least one of the class(es)

<span id="C28024_"></span><span id="c28024_"></span>C28024:  
The function pointer being assigned to is annotated with the function class, which is not contained in the function class(es) list.

<span id="C28155_"></span><span id="c28155_"></span>C28155:  
Driver routine was not declared with the correct Role type

<span id="C28208_"></span><span id="c28208_"></span>C28208:  
Function signature doesn’t match with the function declarations

## <span id="SDV_Rules"></span><span id="sdv_rules"></span><span id="SDV_RULES"></span>SDV Rules


### <span id="Network"></span><span id="network"></span><span id="NETWORK"></span>Network

<span id="DoubleComplete_"></span><span id="doublecomplete_"></span><span id="DOUBLECOMPLETE_"></span>DoubleComplete   
The DoubleComplete rule specifies that NDIS drivers must not complete an object identifier (OID) request multiple times.

<span id="DoubleCompleteWorkItem_"></span><span id="doublecompleteworkitem_"></span><span id="DOUBLECOMPLETEWORKITEM_"></span>DoubleCompleteWorkItem   
The DoubleCompleteWorkItem rule specifies that NDIS drivers must not complete an OID request multiple times when the completion is deferred in a work item.

<span id="Init_DeRegisterInterrupt"></span><span id="init_deregisterinterrupt"></span><span id="INIT_DEREGISTERINTERRUPT"></span>Init\_DeRegisterInterrupt  
The Init\_DeRegisterInterrupt rule specifies that if NdisMRegisterInterruptEx is called at least once during MPInitilize, NdisMDeregisterInterruptEx should be called at least once in MPHaltEx.

<span id="Init_NdisAllocateIoWorkItem"></span><span id="init_ndisallocateioworkitem"></span><span id="INIT_NDISALLOCATEIOWORKITEM"></span>Init\_NdisAllocateIoWorkItem  
The Init\_NdisAllocateIoWorkItem rule specifies that if NdisAllocateIoWorkItem is called at least once during MiniportInitializeEx, the NdisFreeIoWorkItem function should;

-   be called at least once in MPHaltEx, if MiniportInitializeEx succeeds
-   be called in MiniportInitializeEx, if MiniportInitializeEx fails

<span id="Init_RegisterInterrupt_"></span><span id="init_registerinterrupt_"></span><span id="INIT_REGISTERINTERRUPT_"></span>Init\_RegisterInterrupt   
The Init\_RegisterInterrupt rule specifies that the registration of interrupts, which usually happens during initialization, must be undone if something goes wrong in the initialization process or during the halting of the miniport driver. If NdisMRegisterInterruptEx is called at least one time during MiniportInitializeEx, the NdisMDeregisterInterruptEx function must be called at least one time in MiniportHaltEx.

<span id="Init_RegisterSG_"></span><span id="init_registersg_"></span><span id="INIT_REGISTERSG_"></span>Init\_RegisterSG   
The Init\_RegisterSG rule specifies that the registration of the scatter-gather list (SG), which usually happens during initialization, must be undone if something goes wrong in the initialization process or during the halting of the miniport driver. If NdisMRegisterScatterGatherDma is called at least one time during MiniportInitializeEx, the NdisMDeregisterScatterGatherDma function should be called at least one time in MiniportHaltEx.

<span id="Irql_CallManager_Function_"></span><span id="irql_callmanager_function_"></span><span id="IRQL_CALLMANAGER_FUNCTION_"></span>Irql\_CallManager\_Function   
The Irql\_CallManager\_Function rule specifies that the NDIS functions for the NDIS CallManager must be called at correct IRQL levels. This rule examines the following NDIS functions;

-   NdisCmActivateVc
-   NdisCmAddPartyComplete
-   NdisCmCloseAddressFamilyComplete
-   NdisCmCloseCallComplete
-   NdisCmDeactivateVc
-   NdisCmDeregisterSapComplete
-   NdisCmDispatchCallConnected
-   NdisCmDispatchIncomingCall
-   NdisCmDispatchIncomingCallQoSChange
-   NdisCmDispatchIncomingCloseCall
-   NdisCmDispatchIncomingDropParty
-   NdisCmDropPartyComplete
-   NdisCmMakeCallComplete
-   NdisCmModifyCallQoSComplete
-   NdisCmNotifyCloseAddressFamily
-   NdisCmOpenAddressFamilyComplete
-   NdisCmRegisterAddressFamilyEx
-   NdisCmRegisterSapComplete

<span id="Irql_Connection_Function_"></span><span id="irql_connection_function_"></span><span id="IRQL_CONNECTION_FUNCTION_"></span>Irql\_Connection\_Function   
The Irql\_Connection\_Function rule specifies that the NDIS connection functions for protocol drivers must be called at correct IRQL levels. This rule verifies the following NDIS functions;

-   NdisCoAssignInstanceName
-   NdisCoCreateVc
-   NdisCoDeleteVc
-   NdisCoGetTapiCallId
-   NdisCoOidRequest
-   NdisCoOidRequestComplete
-   NdisCoSendNetBufferLists

<span id="Irql_Filter_Driver_Function_"></span><span id="irql_filter_driver_function_"></span><span id="IRQL_FILTER_DRIVER_FUNCTION_"></span>Irql\_Filter\_Driver\_Function   
The Irql\_Filter\_Driver\_Function rule specifies that the NDIS functions for filter drivers must be called at correct IRQL levels. The NDIS functions for filter drivers include the following;

-   NdisFRegisterFilterDriver
-   NdisFDeregisterFilterDriver
-   NdisFSetAttributes
-   NdisFRestartFilter
-   NdisFRestartComplete
-   NdisFPauseComplete
-   NdisFSendNetBufferLists
-   NdisFReturnNetBufferLists
-   NdisFSendNetBufferListsComplete
-   NdisFCancelSendNetBufferLists
-   NdisFIndicateReceiveNetBufferLists
-   NdisFNetPnPEvent
-   NdisFDevicePnPEventNotify
-   NdisEnumerateFilterModules

<span id="Irql_Gather_DMA_Function_"></span><span id="irql_gather_dma_function_"></span><span id="IRQL_GATHER_DMA_FUNCTION_"></span>Irql\_Gather\_DMA\_Function   
The Irql\_Gather\_DMA\_Function rule specifies that the NDIS scatter/gather DMA functions must be called at correct IRQL levels. This rule verifies the following NDIS functions;

-   NdisMAllocateNetBufferSGList
-   NdisMAllocateSharedMemoryAsyncEx
-   NdisMDeregisterScatterGatherDma
-   NdisMFreeNetBufferSGList
-   NdisMRegisterScatterGatherDma

<span id="Irql_IM_Function_"></span><span id="irql_im_function_"></span><span id="IRQL_IM_FUNCTION_"></span>Irql\_IM\_Function   
The Irql\_IM\_Function rule specifies that the NDIS functions for Intermediate (IM) drivers must be called at correct IRQL levels. This rule verifies the following NDIS functions;

-   NdisIMAssociateMiniport
-   NdisIMCancelInitializeDeviceInstance
-   NdisIMDeInitializeDeviceInstance
-   NdisIMGetBindingContext
-   NdisIMInitializeDeviceInstanceEx

<span id="Irql_Interfaces_Function_"></span><span id="irql_interfaces_function_"></span><span id="IRQL_INTERFACES_FUNCTION_"></span>Irql\_Interfaces\_Function   
The Irql\_Interfaces\_Function rule specifies that the NDIS network interface functions must be called at correct IRQL levels. This rule verifies the following NDIS network interface functions; NdisIfAddIfStackEntry,

-   NdisIfAllocateNetLuidIndex
-   NdisIfDeleteIfStackEntry
-   NdisIfDeregisterInterface
-   NdisIfDeregisterProvider
-   NdisIfFreeNetLuidIndex
-   NdisIfGetInterfaceIndexFromNetLuid
-   NdisIfGetNetLuidFromInterfaceIndex
-   NdisIfQueryBindingIfIndex
-   NdisIfRegisterInterface
-   NdisIfRegisterProvider

<span id="Irql_Interrupt_Function_"></span><span id="irql_interrupt_function_"></span><span id="IRQL_INTERRUPT_FUNCTION_"></span>Irql\_Interrupt\_Function   
The Irql\_Interrupt\_Function rule specifies that the NDIS functions for interrupts must be called at correct IRQL levels. This rule verifies the following NDIS functions;

-   NdisMDeregisterInterruptEx
-   NdisMRegisterInterruptEx

<span id="Irql_IrqlSetting_Function_"></span><span id="irql_irqlsetting_function_"></span><span id="IRQL_IRQLSETTING_FUNCTION_"></span>Irql\_IrqlSetting\_Function   
The Irql\_IrqlSetting\_Function rule specifies that the NDIS interrupt macros must be called at correct IRQL levels. This rule verifies the following NDIS macros;

-   NDIS\_LOWER\_IRQL
-   NDIS\_RAISE\_IRQL\_TO\_DISPATCH"

<span id="Irql_MCM_Function_"></span><span id="irql_mcm_function_"></span><span id="IRQL_MCM_FUNCTION_"></span>Irql\_MCM\_Function   
The Irql\_MCM\_Function rule specifies that the NDIS MCM functions for drivers must be called at correct IRQL levels.

<span id="Irql_MCO_Function_"></span><span id="irql_mco_function_"></span><span id="IRQL_MCO_FUNCTION_"></span>Irql\_MCO\_Function   
The Irql\_MCO\_Function rule specifies that the NDIS MCO DDIs for miniport drivers must be called at correct IRQL levels.

<span id="Irql_Miniport_Driver_Function_"></span><span id="irql_miniport_driver_function_"></span><span id="IRQL_MINIPORT_DRIVER_FUNCTION_"></span>Irql\_Miniport\_Driver\_Function   
The Irql\_Miniport\_Driver\_Function rule specifies that the NDIS functions for miniport drivers must be called at correct IRQL levels. This rule verifies functions for NDIS miniport driver logging, NDIS ports, and NDIS DMA interface;

-   NdisMCreateLog
-   NdisMDeregisterDmaChannel
-   NdisMDeregisterIoPortRange
-   NdisMDeregisterMiniportDriver
-   NdisMFlushLog
-   NdisMFreePort
-   NdisMFreeSharedMemory
-   NdisMGetDeviceProperty
-   NdisMGetDmaAlignment
-   NdisMMapIoSpace
-   NdisMPauseComplete
-   NdisMQueryAdapterInstanceName
-   NdisMReadDmaCounter
-   NdisMRegisterDmaChannel
-   NdisMRegisterIoPortRange
-   NdisMRegisterMiniportDriver
-   NdisMRemoveMiniport
-   NdisMResetComplete
-   NdisMRestartComplete
-   NdisMSetMiniportAttributes
-   NdisMSetupDmaTransfer
-   NdisMSleep
-   NdisMUnmapIoSpace
-   NdisMUpdateSharedMemory
-   NdisMWriteLogData

<span id="Irql_Miscellaneous_Function_"></span><span id="irql_miscellaneous_function_"></span><span id="IRQL_MISCELLANEOUS_FUNCTION_"></span>Irql\_Miscellaneous\_Function   
The Irql\_Miscellaneous\_Function rule specifies that the NDIS functions must be called at correct IRQL levels. This rule verifies the following functions;

-   KeGetCurrentProcessorNumber
-   NdisAllocateFromNPagedLookasideList
-   NdisAllocateGenericObject
-   NdisAllocateIoWorkItem
-   NdisAllocateMemoryWithTagPriority
-   NdisAnsiStringToUnicodeString
-   NdisCloseConfiguration
-   NdisCloseFile
-   NdisDeleteNPagedLookasideList
-   NdisDeregisterDeviceEx
-   NdisEqualMemory
-   NdisEqualUnicodeString
-   NdisFreeGenericObject
-   NdisFreeIoWorkItem
-   NdisFreeMemory
-   NdisFreeSpinLock
-   NdisFreeString
-   NdisFreeToNPagedLookasideList
-   NdisGeneratePartialCancelId
-   NdisGetCurrentProcessorCounts
-   NdisGetDriverHandle
-   NdisGetRoutineAddress
-   NdisGetSharedDataAlignment
-   NdisGetVersion
-   NdisInitAnsiString
-   NdisInitializeListHead
-   NdisInitializeNPagedLookasideList
-   NdisInitializeSListHead
-   NdisInitializeString
-   NdisInitUnicodeString
-   NdisMapFile
-   NdisOpenConfigurationEx
-   NdisOpenConfigurationKeyByIndex
-   NdisOpenConfigurationKeyByName
-   NdisOpenFile
-   NdisQueryAdapterInstanceName
-   NdisQueryDepthSList
-   NdisQueueIoWorkItem
-   NdisReadConfiguration
-   NdisReadNetworkAddress
-   NdisReEnumerateProtocolBindings
-   NdisSetOptionalHandlers
-   NdisSystemProcessorCount
-   NdisUnicodeStringToAnsiString
-   NdisUnmapFile
-   NdisUpcaseUnicodeString
-   NdisWaitEvent
-   NdisWriteConfiguration
-   NdisWriteErrorLogEntry
-   NdisWriteEventLogEntry

<span id="Irql_NetBuffer_Function_"></span><span id="irql_netbuffer_function_"></span><span id="IRQL_NETBUFFER_FUNCTION_"></span>Irql\_NetBuffer\_Function   
The Irql\_NetBuffer\_Function rule specifies that the NET\_BUFFER-related functions must be called at correct IRQL levels. This rule verifies the following NDIS functions;

-   NdisAdvanceNetBufferDataStart
-   NdisAdvanceNetBufferListDataStart
-   NdisAllocateCloneNetBufferList
-   NdisAllocateFragmentNetBufferList
-   NdisAllocateMdl
-   NdisAllocateNetBuffer
-   NdisAllocateNetBufferAndNetBufferList
-   NdisAllocateNetBufferList
-   NdisAllocateNetBufferListContext
-   NdisAllocateNetBufferListPool
-   NdisAllocateNetBufferMdlAndData
-   NdisAllocateNetBufferPool
-   NdisAllocateReassembledNetBufferList
-   NdisCopyFromNetBufferToNetBuffer
-   NdisCopyReceiveNetBufferListInfo
-   NdisCopySendNetBufferListInfo
-   NdisFreeCloneNetBufferList
-   NdisFreeFragmentNetBufferList
-   NdisFreeMdl
-   NdisFreeNetBuffer
-   NdisFreeNetBufferList
-   NdisFreeNetBufferListContext
-   NdisFreeNetBufferListPool
-   NdisFreeNetBufferPool
-   NdisFreeReassembledNetBufferList
-   NdisGetDataBuffer
-   NdisGetMdlPhysicalArraySize
-   NdisGetPoolFromNetBuffer
-   NdisGetPoolFromNetBufferList
-   NdisQueryMdl
-   NdisQueryMdlOffset
-   NdisQueryNetBufferPhysicalCount
-   NdisRetreatNetBufferDataStart
-   NdisRetreatNetBufferListDataStart

<span id="Irql_OID_Function"></span><span id="irql_oid_function"></span><span id="IRQL_OID_FUNCTION"></span>Irql\_OID\_Function  
The Irql\_OID\_Function rule specifies that the NDIS OID request DDIs must be called at correct IRQL levels.

<span id="Irql_Protocol_Driver_Function_"></span><span id="irql_protocol_driver_function_"></span><span id="IRQL_PROTOCOL_DRIVER_FUNCTION_"></span>Irql\_Protocol\_Driver\_Function   
The Irql\_Protocol\_Driver\_Function rule specifies that the NDIS functions for CoNDIS clients must be called at correct IRQL levels. This rule verifies the following NDIS functions;

-   NdisClAddParty
-   NdisClCloseAddressFamily
-   NdisClCloseCall
-   NdisClDeregisterSap
-   NdisClDropParty
-   NdisClGetProtocolVcContextFromTapiCallId
-   NdisClIncomingCallComplete
-   NdisClMakeCall
-   NdisClModifyCallQoS
-   NdisClNotifyCloseAddressFamilyComplete
-   NdisClOpenAddressFamilyEx
-   NdisCloseAdapterEx
-   NdisClRegisterSap
-   NdisCompleteBindAdapterEx
-   NdisCompleteNetPnPEvent
-   NdisCompleteUnbindAdapterEx
-   NdisDeregisterProtocolDriver
-   NdisMNetPnPEvent
-   NdisOpenAdapterEx
-   NdisRegisterProtocolDriver
-   NdisUnbindAdapter

<span id="Irql_SendRcv_Function_"></span><span id="irql_sendrcv_function_"></span><span id="IRQL_SENDRCV_FUNCTION_"></span>Irql\_SendRcv\_Function   
The Irql\_SendRcv\_Function rule specifies that the send and receive functions for NDIS drivers must be called at correct IRQL levels.

<span id="Irql_StatusIndication_Function_"></span><span id="irql_statusindication_function_"></span><span id="IRQL_STATUSINDICATION_FUNCTION_"></span>Irql\_StatusIndication\_Function   
The Irql\_StatusIndication\_Function rule specifies that the NDIS status indication functions for miniport and filter drivers must be called at correct IRQL levels. This rule verifies the following NDIS functions; NdisFIndicateStatus and,NdisMIndicateStatusEx

<span id="Irql_Synch_Function_"></span><span id="irql_synch_function_"></span><span id="IRQL_SYNCH_FUNCTION_"></span>Irql\_Synch\_Function   
The Irql\_Synch\_Function rule specifies that the NDIS interrupt and synchronization DDIs must be called at correct IRQL levels.

<span id="Irql_Timer_Function_"></span><span id="irql_timer_function_"></span><span id="IRQL_TIMER_FUNCTION_"></span>Irql\_Timer\_Function   
The Irql\_Timer\_Function rule specifies that the NDIS timer service functions must be called at correct IRQL levels. This rule verifies the following NDIS functions;

-   NdisAllocateTimerObject
-   NdisCancelTimerObject
-   NdisFreeTimerObject
-   NdisSetTimerObject

<span id="MiniportPause_Return_"></span><span id="miniportpause_return_"></span><span id="MINIPORTPAUSE_RETURN_"></span>MiniportPause\_Return   
The MiniportPause\_Return rule specifies that the MiniportPause callback function should return only NDIS\_STATUS\_SUCCESS if the pause operation is complete, or NDIS\_STATUS\_PENDING if the miniport driver is in the pausing state. Any other returned status is invalid.

<span id="NdisAllocateCloneNetBufferList_"></span><span id="ndisallocateclonenetbufferlist_"></span><span id="NDISALLOCATECLONENETBUFFERLIST_"></span>NdisAllocateCloneNetBufferList   
This rule checks that NdisAllocateCloneNetBufferList and NdisFreeCloneNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffer are free when MiniportHaltEx ends. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the MiniportHaltEx exits, then the rule will fail.

<span id="NdisAllocateCloneNetBufferList_InitFail_"></span><span id="ndisallocateclonenetbufferlist_initfail_"></span><span id="NDISALLOCATECLONENETBUFFERLIST_INITFAIL_"></span>NdisAllocateCloneNetBufferList\_InitFail   
This rule checks that NdisAllocateCloneNetBufferList and NdisFreeCloneNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffers are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the Initialization functions fails this rule will report a defect.

<span id="NdisAllocateFragmentNetBufferList_"></span><span id="ndisallocatefragmentnetbufferlist_"></span><span id="NDISALLOCATEFRAGMENTNETBUFFERLIST_"></span>NdisAllocateFragmentNetBufferList   
This rule checks that NdisAllocateFragmentNetBufferList and NdisFreeFragmentNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffer are freed when MiniportHaltEx ends. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the MiniportHaltEx exits, then the rule will fail.

<span id="NdisAllocateFragmentNetBufferList_InitFail_"></span><span id="ndisallocatefragmentnetbufferlist_initfail_"></span><span id="NDISALLOCATEFRAGMENTNETBUFFERLIST_INITFAIL_"></span>NdisAllocateFragmentNetBufferList\_InitFail   
This rule checks that NdisAllocateFragmentNetBufferList and NdisFreeFragmentNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffers are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the Initialization functions fails this rule will report a defect.

<span id="NdisAllocateFromNPagedLookasideList_"></span><span id="ndisallocatefromnpagedlookasidelist_"></span><span id="NDISALLOCATEFROMNPAGEDLOOKASIDELIST_"></span>NdisAllocateFromNPagedLookasideList   
This rule checks that NdisAllocateFromNPagedLookasideList and NdisFreeToNPagedLookasideList are called in alternate order. The ultimate goal is to make sure all LookasideList are freed. The rule uses three different states. State changes when a LookasideList is allocated or freed and deleted.

<span id="NdisAllocateFromNPagedLookasideList_InitFail_"></span><span id="ndisallocatefromnpagedlookasidelist_initfail_"></span><span id="NDISALLOCATEFROMNPAGEDLOOKASIDELIST_INITFAIL_"></span>NdisAllocateFromNPagedLookasideList\_InitFail   
This rule checks that NdisAllocateFromNPagedLookasideList and NdisFreeToNPagedLookasideList are called in alternate order. The ultimate goal is to make sure all LookasideList are freed. The rule uses three different states. State changes when a LookasideList entry is allocated or freed.

<span id="NdisAllocateGenericObject_"></span><span id="ndisallocategenericobject_"></span><span id="NDISALLOCATEGENERICOBJECT_"></span>NdisAllocateGenericObject   
The NdisAllocateGenericObject rule specifies that NdisAllocateGenericObject and NdisFreeGenericObject are called in alternate order. The ultimate goal is to make sure all generic objects are freed when MiniportHaltEx ends. The rule uses three different states. The state changes when an NDIS generic object is allocated or freed. If an NDIS generic object is still allocated when the MiniportHaltEx exits, the rule will fail.

<span id="NdisAllocateMdl_"></span><span id="ndisallocatemdl_"></span><span id="NDISALLOCATEMDL_"></span>NdisAllocateMdl   
The NdisAllocateMdl rule specifies that NdisAllocateMdl and NdisFreeMdl are called in alternate order. The ultimate goal is to make sure all MDLs are freed when MiniportHaltEx ends. The rule uses three different states. The state changes when an MDL is allocated or freed. If an MDL is still allocated when the MiniportHaltEx exits, the rule reports the defect.

<span id="NdisAllocateMemoryWithTagPriority_"></span><span id="ndisallocatememorywithtagpriority_"></span><span id="NDISALLOCATEMEMORYWITHTAGPRIORITY_"></span>NdisAllocateMemoryWithTagPriority   
The NdisAllocateMemoryWithTagPriority rule specifies that a driver must not call NdisAllocateMemoryWithTagPriority without providing a Tag. Every memory allocation should use a unique pool tag to ensure that kernel debuggers and Driver Verifier can identify a distinct allocated block of memory.

<span id="NdisAllocateMemoryWithTagPriority_Cleanup"></span><span id="ndisallocatememorywithtagpriority_cleanup"></span><span id="NDISALLOCATEMEMORYWITHTAGPRIORITY_CLEANUP"></span>NdisAllocateMemoryWithTagPriority\_Cleanup  
This rule checks that NdisAllocateMemoryWithTagPriority and NdisFreeMemoryWithTagPriority or NdisFreeMemory are called in alternate order. The ultimate goal is to make sure all NetBuffers are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the Initialization functions fails this rule will report a defect.

<span id="NdisAllocateMemoryWithTagPriority_InitFail_"></span><span id="ndisallocatememorywithtagpriority_initfail_"></span><span id="NDISALLOCATEMEMORYWITHTAGPRIORITY_INITFAIL_"></span>NdisAllocateMemoryWithTagPriority\_InitFail   
This rule checks that NdisAllocateMemoryWithTagPriority and NdisFreeMemoryWithTagPriority or NdisFreeMemory are called in alternate order. The ultimate goal is to make sure all NetBuffers are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the Initialization functions fails this rule will report a defect.

<span id="NdisAllocateNetBuffer_"></span><span id="ndisallocatenetbuffer_"></span><span id="NDISALLOCATENETBUFFER_"></span>NdisAllocateNetBuffer   
The NdisAllocateNetBuffer rule specifies that NdisAllocateNetBuffer and NdisFreeNetBuffer are called in alternate order. The ultimate goal is to make sure all instances of NET\_BUFFER are freed when MiniportHaltEx ends. The rule uses three different states. The state changes when a NET\_BUFFER is allocated or freed. If a NET\_BUFFER is still allocated when the MiniportHaltEx exits, the rule reports the defect.

<span id="NdisAllocateNetBufferList_"></span><span id="ndisallocatenetbufferlist_"></span><span id="NDISALLOCATENETBUFFERLIST_"></span>NdisAllocateNetBufferList   
This rule checks that NdisAllocateNetBufferList and NdisFreeNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffer are freed when MiniportHaltEx ends.

<span id="NdisAllocateNetBufferList2_"></span><span id="ndisallocatenetbufferlist2_"></span><span id="NDISALLOCATENETBUFFERLIST2_"></span>NdisAllocateNetBufferList2   
This rule checks that NdisAllocateNetBufferList and NdisFreeNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffer are freed when MiniportHaltEx ends. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the MiniportHaltEx exits, then the rule will fail.

<span id="NdisAllocateNetBufferList2_InitFail_"></span><span id="ndisallocatenetbufferlist2_initfail_"></span><span id="NDISALLOCATENETBUFFERLIST2_INITFAIL_"></span>NdisAllocateNetBufferList2\_InitFail   
This rule checks that NdisAllocateNetBufferList and NdisFreeNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffers are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the MiniportHaltEx exits, then the rule will fail.

<span id="NdisAllocateNetBufferListPool_"></span><span id="ndisallocatenetbufferlistpool_"></span><span id="NDISALLOCATENETBUFFERLISTPOOL_"></span>NdisAllocateNetBufferListPool   
This rule checks that NdisAllocateNetBufferListPool and NdisFreeNetBufferListPool are called in alternate order. The ultimate goal is to make sure all NetBuffer are freed when MiniportHaltEx ends. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the MiniportHaltEx exits, then the rule will fail.

<span id="NdisAllocateNetBufferListPool_InitFail_"></span><span id="ndisallocatenetbufferlistpool_initfail_"></span><span id="NDISALLOCATENETBUFFERLISTPOOL_INITFAIL_"></span>NdisAllocateNetBufferListPool\_InitFail   
This rule checks that NdisAllocateNetBufferListPool and NdisFreeNetBufferListPool are called in alternate order. The ultimate goal is to make sure all NetBuffers are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the Initialization functions fails this rule will report a defect.

<span id="NdisAllocateNetBufferList_InitFail_"></span><span id="ndisallocatenetbufferlist_initfail_"></span><span id="NDISALLOCATENETBUFFERLIST_INITFAIL_"></span>NdisAllocateNetBufferList\_InitFail   
This rule checks that NdisAllocateNetBufferAndNetBufferList and NdisFreeNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffer are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the Initialization functions fails.

<span id="NdisAllocateNetBufferMdlAndData_"></span><span id="ndisallocatenetbuffermdlanddata_"></span><span id="NDISALLOCATENETBUFFERMDLANDDATA_"></span>NdisAllocateNetBufferMdlAndData   
This rule checks that NdisAllocateNetBufferMdlAndData and NdisFreeNetBuffer are called in alternate order. The ultimate goal is to make sure all NetBuffer are freed when MiniportHaltEx ends. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the MiniportHaltEx exits, then the rule will fail.

<span id="NdisAllocateNetBufferMdlAndData_InitFail_"></span><span id="ndisallocatenetbuffermdlanddata_initfail_"></span><span id="NDISALLOCATENETBUFFERMDLANDDATA_INITFAIL_"></span>NdisAllocateNetBufferMdlAndData\_InitFail   
This rule checks that NdisAllocateNetBufferMdlAndData and NdisFreeNetBuffer are called in alternate order. The ultimate goal is to make sure all NetBuffers are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the Initialization functions fails this rule will report a defect.

<span id="NdisAllocateNetBufferPool_"></span><span id="ndisallocatenetbufferpool_"></span><span id="NDISALLOCATENETBUFFERPOOL_"></span>NdisAllocateNetBufferPool   
This rule checks that NdisAllocateNetBufferPool and NdisFreeNetBufferListPool are called in alternate order. The ultimate goal is to make sure all NetBuffer are freed when MiniportHaltEx ends. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the MiniportHaltEx exits, then the rule will fail.

<span id="NdisAllocateNetBufferPool_InitFail_"></span><span id="ndisallocatenetbufferpool_initfail_"></span><span id="NDISALLOCATENETBUFFERPOOL_INITFAIL_"></span>NdisAllocateNetBufferPool\_InitFail   
This rule checks that NdisAllocateNetBufferPool and NdisFreeNetBufferListPool are called in alternate order. The ultimate goal is to make sure all NetBuffers are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the Initialization functions fails this rule will report a defect.

<span id="NdisAllocateReassembledNetBufferList_"></span><span id="ndisallocatereassemblednetbufferlist_"></span><span id="NDISALLOCATEREASSEMBLEDNETBUFFERLIST_"></span>NdisAllocateReassembledNetBufferList   
This rule checks that NdisAllocateReassembledNetBufferList and NdisFreeReassembledNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffer are freed when MiniportHaltEx ends. The rule uses three different states. State changes when a NetBuffer is allocated or freed. If a NetBuffer is still allocated when the MiniportHaltEx exits, then the rule will fail.

<span id="NdisAllocateReassembledNetBufferList_InitFail_"></span><span id="ndisallocatereassemblednetbufferlist_initfail_"></span><span id="NDISALLOCATEREASSEMBLEDNETBUFFERLIST_INITFAIL_"></span>NdisAllocateReassembledNetBufferList\_InitFail   
This rule checks that NdisAllocateReassembledNetBufferList and NdisFreeReassembledNetBufferList are called in alternate order. The ultimate goal is to make sure all NetBuffers are freed when the initialization functions fails. The rule uses three different states. State changes when a NetBuffer is allocated or freed If a NetBuffer is still allocated when the Initialization functions fails this rule will report a defect.

<span id="NdisFDeregisterFilterDriver_"></span><span id="ndisfderegisterfilterdriver_"></span><span id="NDISFDEREGISTERFILTERDRIVER_"></span>NdisFDeregisterFilterDriver   
A filter driver must call NdisFDeregisterFilterDriver from its FilterDriverUnload routine.

<span id="NdisMDeregisterInterruptEx_"></span><span id="ndismderegisterinterruptex_"></span><span id="NDISMDEREGISTERINTERRUPTEX_"></span>NdisMDeregisterInterruptEx   
After NdisMDeregisterInterruptEx returns control, the miniport driver cannot call the NdisMSynchronizeWithInterruptEx function.

<span id="NdisMFreeSharedMemory_"></span><span id="ndismfreesharedmemory_"></span><span id="NDISMFREESHAREDMEMORY_"></span>NdisMFreeSharedMemory   
NdisMFreeSharedMemory cannot be called from a MiniportShutdownEx function.

<span id="NdisMIndicateStatusEx_"></span><span id="ndismindicatestatusex_"></span><span id="NDISMINDICATESTATUSEX_"></span>NdisMIndicateStatusEx   
The driver must not call NdisMIndicateStatusEx after it returns from the MiniportHaltEx function.

<span id="NdisMMapIoSpace_"></span><span id="ndismmapiospace_"></span><span id="NDISMMAPIOSPACE_"></span>NdisMMapIoSpace   
The NdisMMapIoSpace function should only be called in the context of MiniportInitializeEx.

<span id="NdisMNetPnPEventInOIDRequest_"></span><span id="ndismnetpnpeventinoidrequest_"></span><span id="NDISMNETPNPEVENTINOIDREQUEST_"></span>NdisMNetPnPEventInOIDRequest   
This rule checks that NdisMNetPnPEvent is not called in the context of an OID request.

<span id="NdisMRegisterIoPortRange_"></span><span id="ndismregisterioportrange_"></span><span id="NDISMREGISTERIOPORTRANGE_"></span>NdisMRegisterIoPortRange   
A miniport driver calls NdisMRegisterIoPortRange from its MiniportInitializeEx or MINIPORT\_ADD\_DEVICE functions. MiniportInitializeEx or MINIPORT\_ADD\_DEVICE must call NdisMSetMiniportAttributes before calling NdisMRegisterIoPortRange.

<span id="NdisOpenConfigurationEx_"></span><span id="ndisopenconfigurationex_"></span><span id="NDISOPENCONFIGURATIONEX_"></span>NdisOpenConfigurationEx   
This rule checks that NdisOpenConfigurationEx and NdisCloseConfiguration are called in alternate order. The ultimate goal is to make sure that configuration handles are closed when MiniportHaltEx exits. The rule uses three different states. The state changes when a configuration is opened or closed. If a configuration handle is still open when the MiniportHaltEx exits, a defect is reported.

<span id="NdisQueryBindInstanceName_"></span><span id="ndisquerybindinstancename_"></span><span id="NDISQUERYBINDINSTANCENAME_"></span>NdisQueryBindInstanceName   
NdisQueryBindInstanceName allocates memory for the string that specifies the friendly name. After the caller finishes using this memory, the caller must call the NdisFreeMemory function to release the memory.

<span id="NdisReEnumerateProtocolBindings_"></span><span id="ndisreenumerateprotocolbindings_"></span><span id="NDISREENUMERATEPROTOCOLBINDINGS_"></span>NdisReEnumerateProtocolBindings   
Protocol drivers cannot call NdisReEnumerateProtocolBindings from within the context of the ProtocolBindAdapterEx, or ProtocolUnbindAdapterEx functions. Also, protocol drivers cannot call NdisReEnumerateProtocolBindings from within the context of the ProtocolNetPnPEvent function if the ProtocolBindingContext parameter of ProtocolNetPnPEvent is not NULL. However, protocol drivers can call NdisReEnumerateProtocolBindings from within the context of ProtocolNetPnPEvent if ProtocolBindingContext is NULL. A NULL ProtocolBindingContext value indicates that the event applies to all bindings.

<span id="PeriodicTimer_"></span><span id="periodictimer_"></span><span id="PERIODICTIMER_"></span>PeriodicTimer   
The PeriodicTimer rule specifies that the caller of NdisCancelTimerObject must be running at IRQL = PASSIVE\_LEVEL if a nonzero value was specified in the MillisecondsPeriod parameter of the NdisSetTimerObject function. If the MillisecondsPeriod parameter of the NdisSetTimerObject function was zero, callers of NdisCancelTimerObject can be running at IRQL &lt;= DISPATCH\_LEVEL.

<span id="Irqlapclte_"></span><span id="irqlapclte_"></span><span id="IRQLAPCLTE_"></span>Irqlapclte   
The IrqlApcLte rule specifies that the driver calls ObGetObjectSecurity and ObReleaseObjectSecurity only when it is executing at IRQL &lt;= APC\_LEVEL.

<span id="Irqldispatch_"></span><span id="irqldispatch_"></span><span id="IRQLDISPATCH_"></span>Irqldispatch   
The IrqlDispatch rule specifies that the driver calls the following DDIs only when it is executing at IRQL = DISPATCH\_LEVEL;

-   FreeAdapterChannel,
-   FreeMapRegisters,
-   GetScatterGatherList,
-   IoAllocateAdapterChannel,
-   IoAllocateController,
-   IoFreeController,
-   IoStartNextPacket,
-   KeAcquireSpinLockAtDpcLevel,
-   KeInsertByKeyDeviceQueue,
-   KeInsertDeviceQueue,
-   KeReleaseSpinLockFromDpcLevel,
-   KeRemoveByKeyDeviceQueue,
-   KeRemoveDeviceQueue,
-   PutScatterGatherList

<span id="Irqlexallocatepool_"></span><span id="irqlexallocatepool_"></span><span id="IRQLEXALLOCATEPOOL_"></span>Irqlexallocatepool   
The IrqlExAllocatePool rule specifies that the driver calls ExAllocatePoolWithTag and ExAllocatePoolWithTagPriority only when it is executing at IRQL &lt;= DISPATCH\_LEVEL.. A caller executing at DISPATCH\_LEVEL must specify a NonPagedXxx value for PoolType. A caller executing at IRQL &lt;= APC\_LEVEL can specify any POOL\_TYPE value.

<span id="Irqlexapclte1_"></span><span id="irqlexapclte1_"></span><span id="IRQLEXAPCLTE1_"></span>Irqlexapclte1   
The IrqlExApcLte1 rule specifies that the driver calls ExAcquireFastMutex and ExTryToAcquireFastMutex only at IRQL &lt;= APC\_LEVEL.

<span id="Irqlexapclte2_"></span><span id="irqlexapclte2_"></span><span id="IRQLEXAPCLTE2_"></span>Irqlexapclte2   
The IrqlExApcLte2 rule specifies that the driver calls the following routines only at IRQL &lt;= APC\_LEVEL;

-   CmRegisterCallback,
-   CmUnRegisterCallback,
-   ExAllocateFromPagedLookasideList,
-   ExAllocatePoolWithQuota,
-   ExAllocatePoolWithQuotaTag,
-   ExDeletePagedLookasideList,
-   ExFreeToPagedLookasideList,
-   ExInitializePagedLookasideList,
-   ExRegisterCallback,
-   ExSetTimerResolution,
-   ExUnregisterCallback,
-   ProbeForRead,
-   ProbeForWrite

<span id="Irqlexapclte3_"></span><span id="irqlexapclte3_"></span><span id="IRQLEXAPCLTE3_"></span>Irqlexapclte3   
The IrqlExApcLte3 rule specifies that the driver calls the following executive support routines only at IRQL &lt;= APC\_LEVEL;

-   ExAcquireResourceExclusiveLite,
-   ExAcquireResourceSharedLite,
-   ExAcquireSharedStarveExclusive,
-   ExAcquireSharedWaitForExclusive,
-   ExConvertExclusiveToSharedLite,
-   ExDeleteResourceLite

Drivers that have errors related to IRQL can cause serious problems and could cause a computer to crash.

<span id="Irqlexapclteinline_"></span><span id="irqlexapclteinline_"></span><span id="IRQLEXAPCLTEINLINE_"></span>Irqlexapclteinline   
The IrqlExApcLteInline rule specifies that DDIs are only called at proper IRQL levels

<span id="irqlexpassive_"></span><span id="IRQLEXPASSIVE_"></span>irqlexpassive   
The IrqlExPassive rule specifies that the driver calls the following executive support routines only at IRQL = PASSIVE\_LEVEL;

-   ExCreateCallback,
-   ExIsProcessorFeaturePresent,
-   ExRaiseAccessViolation,
-   ExRaiseDatatypeMisalignment,
-   ExRaiseStatus,
-   ExUuidCreate

The IrqlExPassive rule also specifies that the driver calls ExRaiseStatus at IRQL &lt;= APC\_LEVEL.

<span id="irqlioapclte_"></span><span id="IRQLIOAPCLTE_"></span>irqlioapclte   
The IrqlIoApcLte rule specifies that the driver calls the following I/O manager routines only when it is executing at IRQL &lt;= APC\_LEVEL;

-   IoDeleteDevice,
-   IoGetInitialStack,
-   IoRaiseHardError,
-   IoRaiseInformationalHardError

<span id="irqliodispatch_"></span><span id="IRQLIODISPATCH_"></span>irqliodispatch   
The IrqlIoDispatch rule specifies that the driver calls the following I/O Manager routines only when it is executing at IRQL &lt;= DISPATCH\_LEVEL;

-   IoGetDeviceToVerify,
-   IoSetDeviceToVerify.

<span id="irqliopassive1_"></span><span id="IRQLIOPASSIVE1_"></span>irqliopassive1   
The IrqlIoPassive1 rule specifies that the driver calls the following routines only when it is executing at IRQL = PASSIVE\_LEVEL;

-   IoAttachDevice,
-   IoCreateDevice,
-   IoSetDeviceInterfaceState

The rule also specifies that the driver calls the following routine only when it is executing at IRQL = PASSIVE\_LEVEL or IRQL = APC\_LEVEL: IoBuildDeviceIoControlRequest

<span id="irqliopassive2_"></span><span id="IRQLIOPASSIVE2_"></span>irqliopassive2   
The IrqlIoPassive2 rule specifies that the driver calls the following I/O Manager routines only at IRQL = PASSIVE\_LEVEL;

-   IoCheckShareAccess,
-   IoConnectInterrupt,
-   IoCreateController

<span id="irqliopassive3_"></span><span id="IRQLIOPASSIVE3_"></span>irqliopassive3   
The IrqlIoPassive3 rule specifies that the driver calls the following routines only when it is executing at IRQL = PASSIVE\_LEVEL;

-   IoDetachDevice,
-   IoAssignArcName,
-   IoRegisterDeviceInterface

<span id="irqliopassive4_"></span><span id="IRQLIOPASSIVE4_"></span>irqliopassive4   
The IrqlIoPassive4 rule specifies that the driver calls the following routines only when it is executing at IRQL = PASSIVE\_LEVEL;

-   IoCreateFile,
-   IoCreateNotificationEvent,
-   IoCreateSymbolicLink,
-   IoCreateSynchronizationEvent,
-   IoCreateUnprotectedSymbolicLink,
-   IoDeassignArcName,
-   IoDeleteController,
-   IoDeleteSymbolicLink,
-   IoDisconnectInterrupt

<span id="irqliopassive5_"></span><span id="IRQLIOPASSIVE5_"></span>irqliopassive5   
The IrqlIoPassive5 rule specifies that the driver calls specific I/O Manager routines only when it is executing at IRQL = PASSIVE\_LEVEL.

<span id="irqlkeapclte1_"></span><span id="IRQLKEAPCLTE1_"></span>irqlkeapclte1   
The IrqlKeApcLte1 rule specifies that the driver calls the following kernel routines only when it is executing at IRQL &lt;= APC\_LEVEL;

-   KeAcquireGuardedMutex,
-   KeAcquireGuardedMutexUnsafe,
-   KeDelayExecutionThread,
-   KeQueryActiveProcessors,
-   KeReleaseGuardedMutex,
-   KeReleaseGuardedMutexUnsafe,
-   KeTryToAcquireGuardedMutex

<span id="irqlkeapclte2_"></span><span id="IRQLKEAPCLTE2_"></span>irqlkeapclte2   
The IrqlKeApcLte2 rule specifies that the driver calls the following kernel routines only when it is executing at IRQL &lt;= APC\_LEVEL;

-   KeAreAllApcsDisabled,
-   KeAreApcsDisabled,
-   KeDeregisterNmiCallback,
-   KeEnterCriticalRegion,
-   KeEnterGuardedRegion,
-   KeLeaveCriticalRegion,
-   KeLeaveGuardedRegion,
-   KeRegisterNmiCallback

<span id="irqlkedispatchlte_"></span><span id="IRQLKEDISPATCHLTE_"></span>irqlkedispatchlte   
The IrqlKeDispatchLte rule specifies that the driver calls the following kernel routines only when it is executing at IRQL &lt;= DISPATCH\_LEVEL;

-   KeAcquireSpinLock,
-   KeCancelTimer,
-   KeClearEvent,
-   KeFlushIoBuffers,
-   KeInitializeDeviceQueue,
-   KeInitializeTimer,
-   KeInitializeTimerEx,
-   KePulseEvent,
-   KeRaiseIrqlToDpcLevel,
-   KeReadStateEvent,
-   KeReadStateTimer,
-   KeReleaseMutex,
-   KeRemoveEntryDeviceQueue,
-   KeResetEvent,
-   KeSaveFloatingPointState,
-   KeSetTimer,
-   KeSetTimerEx

<span id="irqlkeraiselower_"></span><span id="IRQLKERAISELOWER_"></span>irqlkeraiselower   
The IrqlKeRaiseLower rule specifies that the driver does the following when raising and lowering the IRQL;

When the driver calls KeRaiseIrql, it is executing at an IRQL that is lower than or equal to the value of the NewIrql parameter.

The driver calls KeLowerIrql only after calling KeRaiseIrql or KeRaiseIrqlToDpcLevel.

This rule permits nested calls to KeRaiseIrql, KeRaiseIrqlToDpcLevel, and KeLowerIrql.

<span id="irqlkeraiselower2_"></span><span id="IRQLKERAISELOWER2_"></span>irqlkeraiselower2   
The IrqlKeRaiseLower2 rule specifies that drivers use KeLowerIrql to restore the original IRQL raised by a preceding call to KeRaiseIrql or KeRaiseIrqlToDpcLevel. This rule permits nested calls to KeRaiseIrql, KeRaiseIrqlToDpcLevel and KeLowerIrql.

<span id="irqlkereleasespinlock_"></span><span id="IRQLKERELEASESPINLOCK_"></span>irqlkereleasespinlock   
The IrqlKeReleaseSpinLock rule specifies that the driver calls KeReleaseSpinLock only when it is executing at IRQL = DISPATCH\_LEVEL. This rule also specifies that the value of the NewIrql parameter in the call to KeReleaseSpinLock is equal to the IRQL at which the driver was executing before the call to KeAcquireSpinLock. (This value is also the value of the OldIrql parameter that is supplied by KeAcquireSpinLock.)

<span id="irqlkewaitformultipleobjects_"></span><span id="IRQLKEWAITFORMULTIPLEOBJECTS_"></span>irqlkewaitformultipleobjects   
The IrqlKeWaitForMultipleObjects rule specifies that callers of the KeWaitForMultipleObjects routine must be running at proper IRQL based upon the Timeout parameter.

Callers of IrqlKeWaitForMultipleObjects routine can be running at IRQL &lt;= DISPATCH\_LEVEL, except in the following situations;

If Timeout &lt;&gt; 0, the caller of the KeWaitForMultipleObjects routine must be running at IRQL &lt;= APC\_LEVEL.

If Timeout != NULL and \*Timeout = 0, the caller of the KeWaitForMultipleObjects routine must be running at IRQL = DISPATCH\_LEVEL.

If Timeout = NULL, or \*Timeout != 0, the caller of the KeWaitForMultipleObjects routine must running at IRQL &lt;= APC\_LEVEL.

<span id="irqlkewaitformutexobject_"></span><span id="IRQLKEWAITFORMUTEXOBJECT_"></span>irqlkewaitformutexobject   
The IrqlKeWaitForMutexObject rule specifies the driver to call the KeWaitForMutexObject routine at the proper IRQL based on the value of the Timeout parameter:

If Timeout points to a zero value, the driver is executing at IRQL = DISPATCH\_LEVEL.

If Timeout is NULL, or points to any value other than zero, the driver is executing at IRQL &lt;= APC\_LEVEL.

<span id="irqlmmapclte_"></span><span id="IRQLMMAPCLTE_"></span>irqlmmapclte   
The IrqlMmApcLte rule specifies that the driver calls the following memory manager routines only when it is executing at IRQL &lt;= APC\_LEVEL;

-   MmAllocateNonCachedMemory,
-   MmFreeNonCachedMemory,
-   MmAllocatePagesForMdl,
-   MmFreePagesFromMdl,
-   MmLockPagableDataSection,
-   MmLockPagableSectionByHandle,
-   MmPageEntireDriver,
-   MmResetDriverPaging,
-   MmSecureVirtualMemory,
-   MmUnlockPagableImageSection,
-   MmUnsecureVirtualMemory

<span id="irqlmmdispatch_"></span><span id="IRQLMMDISPATCH_"></span>irqlmmdispatch   
The IrqlMmDispatch rule specifies that the driver calls MmFreeContiguousMemory only when it is executing at IRQL &lt;= DISPATCH\_LEVEL.

<span id="irqlobpassive_"></span><span id="IRQLOBPASSIVE_"></span>irqlobpassive   
The IrqlObPassive rule specifies that the driver calls ObReferenceObjectByHandle only when it is executing at IRQL = PASSIVE\_LEVEL.

<span id="irqlpspassive_"></span><span id="IRQLPSPASSIVE_"></span>irqlpspassive   
The IrqlPsPassive rule specifies that the driver calls the following Process Structure routines only when it is executing at IRQL = PASSIVE\_LEVEL;

-   PsCreateSystemThread,
-   PsGetVersion,
-   PsSetCreateProcessNotifyRoutine,
-   PsSetCreateThreadNotifyRoutine,
-   PsSetLoadImageNotifyRoutine,
-   PsTerminateSystemThread

<span id="irqlrtlapc_"></span><span id="IRQLRTLAPC_"></span>irqlrtlapc   
The IrqlRtlApc rule specifies that the driver calls RtlCreateUnicodeString only when it is executing at IRQL &lt;= APC\_LEVEL.

<span id="irqlrtlpassive_"></span><span id="IRQLRTLPASSIVE_"></span>irqlrtlpassive   
The IrqlRtlPassive rule specifies that the driver calls RtlDeleteRegistryValue only when it is executing at IRQL = PASSIVE\_LEVEL.

<span id="irqlrtlpassive2_"></span><span id="IRQLRTLPASSIVE2_"></span>irqlrtlpassive2   
The IrqlRtlPassive rule specifies that the driver calls Rtl\* functions only when it is executing at IRQL = PASSIVE\_LEVEL.

<span id="irqlzwpassive_"></span><span id="IRQLZWPASSIVE_"></span>irqlzwpassive   
The IrqlZwPassive rule specifies that the driver calls ZwClose only when it is executing at IRQL = PASSIVE\_LEVEL.

### <span id="Storage"></span><span id="storage"></span><span id="STORAGE"></span>Storage

Note – the Must-Fix Rules are based on examining the information for each Rule from this URL, <http://msdn.microsoft.com/en-us/library/windows/hardware/jj126200(v=vs.85).aspx>

### <span id="DDIs"></span><span id="ddis"></span><span id="DDIS"></span>DDIs

<span id="HwStorPortProhibitedDDIs"></span><span id="hwstorportprohibitedddis"></span><span id="HWSTORPORTPROHIBITEDDDIS"></span>HwStorPortProhibitedDDIs  
This rule contains a list of WDM DDIs (excluding interlocked functions) that should not be called in physical StorPort miniport drivers.

<span id="StorPortDDIsPortOnly"></span><span id="storportddisportonly"></span><span id="STORPORTDDISPORTONLY"></span>StorPortDDIsPortOnly  
This rule contains a list of StorPort port-only DDIs (excluding interlocked functions) that should not be called in StorPort miniports.

<span id="StorPortDeprecated"></span><span id="storportdeprecated"></span><span id="STORPORTDEPRECATED"></span>StorPortDeprecated  
This rule verifies that the driver does not call either of these deprecated routines; StorPortValidateRange or StorPortLogError.

### <span id="IrqL"></span><span id="irql"></span><span id="IRQL"></span>IrqL

<span id="IrqlDispatch"></span><span id="irqldispatch"></span><span id="IRQLDISPATCH"></span>IrqlDispatch  
This rule verifies that the following routines are only called at IRQL = DISPATCH\_LEVEL.

<span id="IrqlKeReleaseSpinLock"></span><span id="irqlkereleasespinlock"></span><span id="IRQLKERELEASESPINLOCK"></span>IrqlKeReleaseSpinLock  
This rule verifies that KeReleaseSpinLock is called at IRQL = DISPATCH\_LEVEL only. It must also set the IRQL to the previous IRQL level. Typically this call would be preceded by a call to KeAcquireSpinLock.

<span id="SpChangeIrql"></span><span id="spchangeirql"></span><span id="SPCHANGEIRQL"></span>SpChangeIrql  
This rule verifies that the StorPort callback routines return at the same IRQL level as the level at which they are called.

<span id="SpIrql"></span><span id="spirql"></span><span id="SPIRQL"></span>SpIrql  
This rule verifies that the routines TdiRegisterPnPHandlers and TdiDeregisterPnPHandlers are only called at IRQL lower than DISPATCH\_LEVEL. However, if ExFreeToNPagedLookasideList is called, the rule passes.

<span id="StorPortIrql"></span><span id="storportirql"></span><span id="STORPORTIRQL"></span>StorPortIrql  
The StorPortIrql rule checks that StorPort routines are called at the correct IRQL levels.

### <span id="Locking"></span><span id="locking"></span><span id="LOCKING"></span>Locking

<span id="CancelSpinLock"></span><span id="cancelspinlock"></span><span id="CANCELSPINLOCK"></span>CancelSpinLock  
The CancelSpinLock Rule (Storport) rule verifies that each call to IoAcquireCancelSpinLock is promptly followed by a call to IoReleaseCancelSpinLock.

<span id="QueuedSpinLock"></span><span id="queuedspinlock"></span><span id="QUEUEDSPINLOCK"></span>QueuedSpinLock  
The QueuedSpinLock rule verifies that in-stack queued spin locks that are acquired using KeAcquireInStackQueuedSpinLock are promptly released using KeReleaseInStackQueuedSpinLock. In addition, at the end of a dispatch or cancel routine, the driver should not hold any locks.

<span id="QueuedSpinLockRelease"></span><span id="queuedspinlockrelease"></span><span id="QUEUEDSPINLOCKRELEASE"></span>QueuedSpinLockRelease  
This rule verifies that the driver does not call KeReleaseInStackQueuedSpinLock without first acquiring the lock via KeAcquireInStackQueuedSpinLock.

<span id="SpinLock"></span><span id="spinlock"></span><span id="SPINLOCK"></span>SpinLock  
This rule verifies that a call to KeAcquireSpinLock is promptly followed by a call to KeReleaseSpinlock. If a driver calls KeAcquireSpinLockRaiseToDpc or KeAcquireSpinLock again prior to releasing the lock, it fails the rule. In addition, before exiting the dispatch or cancel routine, the driver must release the spin lock.

<span id="SpinLockDpc"></span><span id="spinlockdpc"></span><span id="SPINLOCKDPC"></span>SpinLockDpc  
This rule verifies that a call to KeAcquireSpinLockRaiseToDpc is promptly followed by a call to KeReleaseSpinlock. If a driver calls KeAcquireSpinLock or KeAcquireSpinLockRaiseToDpc again prior to releasing the lock, it fails the rule. In addition, before exiting the dispatch or cancel routine, the driver must release the spin lock.

<span id="StorPortMSILock"></span><span id="storportmsilock"></span><span id="STORPORTMSILOCK"></span>StorPortMSILock  
Miniport drivers are required to acquire the MSI spin lock for a message if, and only if, the InterruptSynchronizationMode member of the PORT\_CONFIGURATION\_INFORMATION (Storport) structure is set to InterruptSynchronizePerMessage. This rule verifies that calls to StorPortAcquireMSISpinLock are only made if the synchronization mode is InterruptSynchronizePerMessage.

<span id="StorPortSpinLock"></span><span id="storportspinlock"></span><span id="STORPORTSPINLOCK"></span>StorPortSpinLock  
This rule verifies that locks that are acquired via StorPortAcquireSpinLock are promptly released via StorPortReleaseSpinLock. The miniport driver fails the rule if it attempts to acquire a lock that it had already acquired, or if it attempts to release a lock that it had not acquired. In addition, at the end of the dispatch or cancel routine, the driver should not hold any spin locks.

<span id="StorPortSpinLock3"></span><span id="storportspinlock3"></span><span id="STORPORTSPINLOCK3"></span>StorPortSpinLock3  
The StorPortSpinLock3 rule verifies the lock acquisition hierarchy that is described in the documentation for the StorPortAcquireSpinLock routine.

### <span id="SRB_Processing"></span><span id="srb_processing"></span><span id="SRB_PROCESSING"></span>SRB Processing

<span id="SpDuplex"></span><span id="spduplex"></span><span id="SPDUPLEX"></span>SpDuplex  
This rule verifies that this miniport is in Full Duplex mode. Any driver built according to the StorPort-miniport model must be in Full Duplex mode. Half Duplex should only be used when porting an existing SCSI driver to StorPort.

<span id="SpNoWait"></span><span id="spnowait"></span><span id="SPNOWAIT"></span>SpNoWait  
This rule verifies that waits or data allocation are not performed inside StartIo.

<span id="SpReturnValue"></span><span id="spreturnvalue"></span><span id="SPRETURNVALUE"></span>SpReturnValue  
This rule verifies that the driver's implementations of HwStorFindAdapter and VirtualHwStorFindAdapter return a valid status. A valid status is one of the following; SP\_RETURN\_FOUND, SP\_RETURN\_ERROR, SP\_RETURN\_BAD\_CONFIG, or SP\_RETURN\_NOT\_FOUND.

<span id="StorPortAllocatePool2"></span><span id="storportallocatepool2"></span><span id="STORPORTALLOCATEPOOL2"></span>StorPortAllocatePool2  
This rule verifies that the miniport makes the correct number of calls to StorPortAllocatePool and StorPortFreePool. If StorPortAllocatePool returns a failure (STOR\_STATUS\_INSUFFICIENT\_RESOURCES), the miniport must not attempt to call StorPortFreePool. In addition, upon exit from a callback, the number of calls to StorPortAllocatePool and StorPortFreePool must be equal.

<span id="StorPortBuildIo"></span><span id="storportbuildio"></span><span id="STORPORTBUILDIO"></span>StorPortBuildIo  
This rule verifies that if the StorPort miniport's StorPortBuildIo routine returns FALSE, the SRB in question is not passed to StartIo. (In such cases, the miniport driver must complete the SRB by calling StorPortNotification with a notification type of RequestComplete from StorPortBuildIo or someplace else).

<span id="StorPortCompleteRequest"></span><span id="storportcompleterequest"></span><span id="STORPORTCOMPLETEREQUEST"></span>StorPortCompleteRequest  
This rule verifies that no calls to StorPortCompleteRequest are made by the miniport. Usage of the StorPortCompleteRequest is not recommended; miniports should instead call StorPortNotification with notificationType = RequestComplete.

<span id="StorPortEnablePassive"></span><span id="storportenablepassive"></span><span id="STORPORTENABLEPASSIVE"></span>StorPortEnablePassive  
This rule verifies that StorPortEnablePassiveInitialization is not called from any StorPort miniport driver routine other than HwInitialize.

<span id="StorPortNotification2"></span><span id="storportnotification2"></span><span id="STORPORTNOTIFICATION2"></span>StorPortNotification2  
This rule verifies that calls to StorPortNotification use only allowed (i.e. documented) notification types.

<span id="StorPortPassiveFromHwInit"></span><span id="storportpassivefromhwinit"></span><span id="STORPORTPASSIVEFROMHWINIT"></span>StorPortPassiveFromHwInit  
StorPortEnablePassiveInitialization should not be called within the HW Initialization entry point for Storport drivers if the HW Initialization entry point can be called directly from the HW Adapter Control entry point.

<span id="StorPortPerfOpts"></span><span id="storportperfopts"></span><span id="STORPORTPERFOPTS"></span>StorPortPerfOpts  
This rule verifies that the PerfConfigData parameter that is passed to StorPortInitializePerfOpts is not NULL.

<span id="StorPortStartIo"></span><span id="storportstartio"></span><span id="STORPORTSTARTIO"></span>StorPortStartIo  
Waits or data allocation must never be performed in the miniport's StartIo routine. The driver fails the rule if it calls StorPortStallExecution or another function that involves time-consuming operations. Since StartIo is synchronized, these calls should mostly be done in BuildIo.

### <span id="Virtual_Miniport"></span><span id="virtual_miniport"></span><span id="VIRTUAL_MINIPORT"></span>Virtual Miniport

<span id="DoubleExFreePool"></span><span id="doubleexfreepool"></span><span id="DOUBLEEXFREEPOOL"></span>DoubleExFreePool  
This rule verifies that the driver does not attempt to free the same block of pool memory twice.

<span id="StorPortVirtualDevice"></span><span id="storportvirtualdevice"></span><span id="STORPORTVIRTUALDEVICE"></span>StorPortVirtualDevice  
This rule verifies that upon exit from the HwStorFindAdapter routine, the VirtualDevice field in the PORT\_CONFIGURATION\_INFORMATION (Storport) structure has been set to FALSE. The rule applies only to physical StorPort miniports.

<span id="StorPortVirtualDevice2"></span><span id="storportvirtualdevice2"></span><span id="STORPORTVIRTUALDEVICE2"></span>StorPortVirtualDevice2  
This rule verifies that upon exit from the HwStorFindAdapter routine, the VirtualDevice field in the PORT\_CONFIGURATION\_INFORMATION (Storport) structure has been set to TRUE. The rule applies only to virtual StorPort miniports.

<span id="WithinCriticalRegion"></span><span id="withincriticalregion"></span><span id="WITHINCRITICALREGION"></span>WithinCriticalRegion  
This rule verifies that the driver's calls to certain synchronization functions are made only while normal kernel APC delivery is disabled.

## <span id="Screenshots_of_Analysis_Tool_Interfaces"></span><span id="screenshots_of_analysis_tool_interfaces"></span><span id="SCREENSHOTS_OF_ANALYSIS_TOOL_INTERFACES"></span>Screenshots of Analysis Tool Interfaces


### <span id="SDV"></span><span id="sdv"></span>SDV

![](images/server-must-fix-sdv.png)

### <span id="Create_Driver_Verification_Log__DVL__file_for_submission_package"></span><span id="create_driver_verification_log__dvl__file_for_submission_package"></span><span id="CREATE_DRIVER_VERIFICATION_LOG__DVL__FILE_FOR_SUBMISSION_PACKAGE"></span>Create Driver Verification Log (DVL) file for submission package

![](images/server-must-fix-create-dvl.png)

### <span id="DVL_File_data"></span><span id="dvl_file_data"></span><span id="DVL_FILE_DATA"></span>DVL File data

![](images/server-must-fix-dvl-file-data.png)

 

 






