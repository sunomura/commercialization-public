---
title: Using Robot Automation for Touch Hardware Certification Tests
description: Using Robot Automation for Touch Hardware Certification Tests
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1e77c273-9e8a-41b1-b683-3c7b319067b2
---

# Using Robot Automation for Touch Hardware Certification Tests


During Windows 7, multiple partners built robots to automate the touch hardware certification tests. The involved lines and points were laid out using predefined locations so the process was fairly straightforward. In Windows 8, many of the locations are randomized so an API is required to help the robots to find these points and lines. This topic covers the API that was designed to provide that information to the robot and let it command the test in a meaningful way.

## <span id="Glossary"></span><span id="glossary"></span><span id="GLOSSARY"></span>Glossary


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Term</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Touch certification tool</p></td>
<td><p>The tool used for testing touch digitizers as part of the Windows Hardware Certification program.</p></td>
</tr>
<tr class="even">
<td><p>Robot controller</p></td>
<td><p>The server controlling the robot. This is the main consumer of the ILogoAutomation interface.</p></td>
</tr>
<tr class="odd">
<td><p>HLK controller</p></td>
<td><p>The server that controls the testing.</p></td>
</tr>
<tr class="even">
<td><p>Interaction</p></td>
<td><p>Single input tests, such as a tap, double tap, or drag. This is the most granular part of touch hardware certification testing. A touch hardware certification test is comprised of a set of interactions.</p></td>
</tr>
<tr class="odd">
<td><p>Test</p></td>
<td><p>A collection of interactions.</p></td>
</tr>
</tbody>
</table>

 

## <span id="How_to_use_these_APIs"></span><span id="how_to_use_these_apis"></span><span id="HOW_TO_USE_THESE_APIS"></span>How to use these APIs


### <span id="Callbacks"></span><span id="callbacks"></span><span id="CALLBACKS"></span>Callbacks

Callbacks are asynchronous, will not always occur on the same thread, and will originate from a multithreaded apartment.

### <span id="Control_Flow_Overview"></span><span id="control_flow_overview"></span><span id="CONTROL_FLOW_OVERVIEW"></span>Control Flow Overview

Each touch hardware certification run consists of a series of tests that is configurable by the Hardware Certification Kit (HLK) controller. Each test is designed to test a specific aspect of a touch digitizer, such as a tap, double tap, or drag test. Every test is composed of an interaction the robot is expected to perform and repeat a set number of times. The goal of the robot is to complete all of the tests by iterating through each one sequentially and performing each interaction.

>[!NOTE]
>  
While the basic idea of the interaction remains the same throughout the test, details such as the start and end points, are changed randomly.

 

### <span id="Connecting_to_the_Touch_Certification_Tool"></span><span id="connecting_to_the_touch_certification_tool"></span><span id="CONNECTING_TO_THE_TOUCH_CERTIFICATION_TOOL"></span>Connecting to the Touch Certification Tool

The touch certification tool must be started from the HLK controller, or manually by using command line. The robot should not start the touch certification tool remotely. If the **ILogoAutomation** interface is created when the touch certification tool is not running, the interface will not be created.

>[!NOTE]
>  
It is not possible to automatically start the robot when the touch certification tool starts. The robot must be started manually for every test run or you must try to create the **ILogoAutomation** interface until it succeeds.

 

### <span id="Selecting_a_test"></span><span id="selecting_a_test"></span><span id="SELECTING_A_TEST"></span>Selecting a test

Each test that the robot performs is identified by a unique name that remains the same between touch certification test runs. The initial screen in the touch certification tool is the test selection page and is treated as a test with a constant name of **Table of Contents**. To get the list of tests, use **QueryAvailableTests**. To start a test, use **StartTest**.

### <span id="Running_a_test"></span><span id="running_a_test"></span><span id="RUNNING_A_TEST"></span>Running a test

Each test includes a set of interactions. The touch certification tool sends a notification when an interaction starts and finishes. The robot should call **ILogoAutomation::QueryInteraction** between the notifications and then perform an interaction. When all of the required interactions are complete, the touch certification tool will stop the test and send a test completed notification by using **ILogoEventHandler::TestCompleted**. At this point, the robot can move to the next test.

### <span id="BKMK_ErrorHandling"></span><span id="bkmk-errorhandling"></span><span id="BKMK_ERRORHANDLING"></span>Error handling

Some of the error cases are as follows:

-   The robot performs an interaction but does not receive an **ILogoEventHandler::InteractionCompleted** callback. The robot controller should have a timeout to detect this. After the timeout, the robot can determine the reason by calling **ILogoAutomation::QueryCurrentState**.

    -   If the digitizer could not recognize a contact, the touch certification tool will wait indefinitely for input on most tests. If the current state has 0 contacts down and **ILogoAutomation::QueryCurrentInteraction** returns the same interaction ID as before, the robot should fail the test because the digitizer could not recognize a contact.

    -   If the digitizer reports that contact has not departed, no interactions will pass until the contact has departed.

-   The robot gets more **ILogoEventHandler::InteractionCompleted** callbacks than the number of interactions it has performed.

    -   This is likely due to device ghosting. The robot should resynchronize its state with the touch certification tool by using **ILogoAutomation::QueryCurrentState** and **ILogoAutomation::QueryCurrentInteraction**.

### <span id="Automated_Logo_Flow_Diagram"></span><span id="automated_logo_flow_diagram"></span><span id="AUTOMATED_LOGO_FLOW_DIAGRAM"></span>Automated Logo Flow Diagram

![automated flow diagram](images/hck-win8-robot-flowdiagram.jpg)

## <span id="API_Definitions"></span><span id="api_definitions"></span><span id="API_DEFINITIONS"></span>API Definitions


There are three interfaces that you can use:

-   [Interface: ILogoAutomation](#bkmk-ilogoautomation)

-   [Interface: IInteractionObject](#bkmk-iinteractionobject)

-   [Interface: ILogoEventHandler](#bkmk-ilogoevenhandler)

### <span id="BKMK_ILogoAutomation"></span><span id="bkmk-ilogoautomation"></span><span id="BKMK_ILOGOAUTOMATION"></span>Interface: ILogoAutomation

The ILogoAutomation interface allows you to do the following:

-   Query information about the state of the touch certification tool by using **QueryCurrentVersion**, **QueryCurrentState**, **QueryAvailableTests**.

-   Control the flow of the touch certification tool similar to the buttons a human would use by using **StartTest**, **ExitTest**, **Exit**, **HideStatusUI**, **ShowStatusUI**.

-   Register touch certification tool events, allowing the robot and the touch certification tool states to be more easily synchronized by using **RegisterEventSink** and **UnregisterEventSink**.

### <span id="Overview"></span><span id="overview"></span><span id="OVERVIEW"></span>Overview

``` syntax
interface ILogoAutomation : IDispatch {
    HRESULT QueryCurrentVersion(
        [out] ULONG* version);
    HRESULT QueryCurrentState(
        [out] BSTR* testName,
        [out] ULONG* nContactsDown);
    HRESULT QueryAvailableTests(
        [out] VARIANT* testNames);

    HRESULT StartTest(
        [in] BSTR testName);
    HRESULT ExitTest();
    HRESULT Exit();
    HRESULT HideStatusUI();
    HRESULT ShowStatusUI();

    HRESULT QueryInteraction(
        [out] IInteractionObject** interaction);
    HRESULT FailInteraction(
        [in] ULONG interactionId,
        [in] BSTR reason);

    HRESULT RegisterEventSink(
        [in] ILogoEventHandler* eventSink, 
        [out] ULONG* cookie);
    HRESULT UnregisterEventSink(
        [in] ULONG cookie);
};
```

### <span id="Methods"></span><span id="methods"></span><span id="METHODS"></span>Methods

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>QueryCurrentVersion</p></td>
<td><p>Returns the current version of the touch certification tool.</p></td>
</tr>
<tr class="even">
<td><p>QueryCurrentState</p></td>
<td><p>Returns the current state of the touch certification tool, including the test that is displaying and the number of contacts that it thinks are down.</p>
<p><strong>testName</strong> The name of either the test selection page (named “Table of Contents”) or an interaction-driven test. The client is responsible for deallocating <strong>testName</strong> with a call to <strong>SysFreeString</strong>.</p>
<p><strong>nContactsDown</strong> The number of contacts that the touch certification tool thinks are down. This can be different from the actual number of contacts down. For more information, see [Error handling](#bkmk-errorhandling).</p></td>
</tr>
<tr class="odd">
<td><p>QueryAvailableTests</p></td>
<td><p>Returns an array of available test names as a Variant. You can get string pointers from this parameter by using <strong>VariantToStringArrayAlloc</strong>. The client is responsible for clearing and deallocating this memory. The touch certification tool will not pass until all tests are completed successfully.</p></td>
</tr>
<tr class="even">
<td><p>StartTest</p></td>
<td><p>Starts the test identified by <strong>testName</strong>. The touch certification tool must be on the test selection screen to start a test. You can use <strong>QueryCurrentState</strong> to get the current screen or <strong>ExitTest</strong> to return to the test selection screen.</p>
<div class="alert">
<strong>Important</strong>  
<p>The value for <strong>testName</strong> is case sensitive.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>ExitTest</p></td>
<td><p>Return from a test to the test selection page.</p></td>
</tr>
<tr class="even">
<td><p>Exit</p></td>
<td><p>Exit the touch certification tool.</p></td>
</tr>
<tr class="odd">
<td><p>HideStatusUI</p></td>
<td><p>Hide the status UI. The UI remains hidden until ShowStatusUI is called. It is important to hide this UI before performing any interactions because the status UI may take focus and interfere with the interaction.</p></td>
</tr>
<tr class="even">
<td><p>ShowStatusUI</p></td>
<td><p>Show the status UI. You can use this if the touch certification tool needs human interaction. The status UI is the recommended way to use the touch certification tool interactively.</p></td>
</tr>
<tr class="odd">
<td><p>QueryInteraction</p></td>
<td><p>Returns a pointer to an <strong>IInteractionObject</strong>. This is used to describe what kind of input the touch certification tool is expecting. The following table summarizes the error conditions for this method and the error code that is returned:</p>
<ul>
<li><p><strong>E_FAIL (0x80004005)</strong> This method cannot be called if the current test is the test selection page. If you call this method at the test selection page, this error code is returned.</p></li>
<li><p><strong>0x80040003</strong> The test does not require any interactions. For example, some touch certification tests ask a question and require human input to answer. For those tests, there is no robot interaction and calling this method for those tests will return this error code.</p></li>
<li><p><strong>0x80040001</strong> The test has already been completed. You cannot rerun a test that has completed. If you calling this method when the test has been completed, this error code is returned.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>FailInteraction</p></td>
<td><p>This can be used to fail any one interaction. Used repeatedly it can fail an entire test. This call will fail if the interaction ID does not match the current interaction number (returns 0x80040005). The message is an optional informative reason that is written to the log.</p></td>
</tr>
<tr class="odd">
<td><p>RegisterEventSink</p></td>
<td><p>Register an event sink with the touch certification tool. For more information, see [Interface: ILogoEventHandler](#bkmk-ilogoevenhandler).</p></td>
</tr>
<tr class="even">
<td><p>UnregisterEventSink</p></td>
<td><p>Pass in the cookie returned from <strong>RegisterEventSink</strong> to unregister an event sink.</p>
<div class="alert">
<strong>Note</strong>  
<p>Make sure to call this method to unregister the event sink before the robot controller is finished. Failing to do so may cause the status UI to freeze for several minutes before DCOM times out. The touch certification tool may try to call the event sink to deliver status updates and will be blocked by an event sink that is not responding. Eventually, the RPC call will timeout and the touch certification tool will recover and automatically unregister the event sink that is not responding.</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

### <span id="When_to_implement"></span><span id="when_to_implement"></span><span id="WHEN_TO_IMPLEMENT"></span>When to implement

You should not implement the interface. It is implemented by the touch certification tool itself.

### <span id="Error_codes"></span><span id="error_codes"></span><span id="ERROR_CODES"></span>Error codes

The following table summarizes the custom error codes defined for the ILogoAutomation interface:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Error code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0x80040000</p></td>
<td><p>The test does not exist.</p></td>
</tr>
<tr class="even">
<td><p>0x80040001</p></td>
<td><p>The test has already been completed.</p></td>
</tr>
<tr class="odd">
<td><p>0x80040002</p></td>
<td><p>The parameter name is not found.</p></td>
</tr>
<tr class="even">
<td><p>0x80040003</p></td>
<td><p>There is no information for the interaction.</p></td>
</tr>
<tr class="odd">
<td><p>0x80040005</p></td>
<td><p>The interaction ID is not correct.</p></td>
</tr>
</tbody>
</table>

 

### <span id="BKMK_IInteractionObject"></span><span id="bkmk-iinteractionobject"></span><span id="BKMK_IINTERACTIONOBJECT"></span>Interface: IInteractionObject

This object defines the interaction that a test expects in order for it to pass. A robot looks at the interaction name and properties to determine the required movements.

IInteractionObject provides access to a property bag that holds the information required to complete an interaction. Not all parameters are used for all gesture types. The parameter names are case sensitive.

### <span id="Overview"></span><span id="overview"></span><span id="OVERVIEW"></span>Overview

``` syntax
interface IInteractionObject : IDispatch {
    HRESULT SetParameter(
        [in] BSTR name,
        [in] VARIANT value);
    HRESULT GetParameter(
        [in] BSTR name,
        [out] VARIANT* value);
}
```

### <span id="Methods"></span><span id="methods"></span><span id="METHODS"></span>Methods

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SetParameter</p></td>
<td><p>Sets a parameter value of <strong>IInteractionObject</strong>. The object keeps a mapping from parameter name to its value. A robot controller should not need to call this method to change the <strong>IInteractionObject</strong>.</p></td>
</tr>
<tr class="even">
<td><p>GetParameter</p></td>
<td><p>Gets a parameter value from <strong>IInteractionObject</strong>. For example, the following sample code shows how to call this method to get the values of the parameters named <strong>id</strong> and <strong>interactionType</strong>:</p>
<pre class="syntax" space="preserve"><code>IInteractionObject* pInteraction = NULL;
VARIANT varTemp;
ULONG id = 0;
PWSTR pszInteractionType = NULL;

m_pLogo-&gt;QueryInteraction(&amp;pInteraction);

// Get interaction id, which is of ULONG type.
pInteraction-&gt;GetParameter(CComBSTR(L&quot;id&quot;), &amp;varTemp));
VariantToUInt32(varTemp, &amp;id);
VariantClear(&amp;varTemp);

// Get interactionType, which is of BSTR type.
pInteraction-&gt;GetParameter(CComBSTR(L&quot;interactionType&quot;), &amp;varTemp);
VariantToStringAlloc(varTemp, &amp;pszInteractionType);
VariantClear(&amp;varTemp);

// Insert logic here to get more/less parameters as needed, and
// use the data to drive the robot to perform the desired input. 

pInteraction-&gt;Release();
CoTaskMemFree(pszInteractionType);</code></pre>
<div class="alert">
<strong>Important</strong>  
<p>If the parameter name does not exist in the <strong>IInteractionObject</strong> internal mapping, this method will return error code 0x80040002 (The parameter name is not found).</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

The following are a list of parameters for the **IInteractionObject** interface:

>[!NOTE]
>  
The type given is a subtype within Variant. You can get the values for **startTimes** by using **VariantToDoubleArrayAlloc**.

 

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>id</p></td>
<td><p>ULONG</p></td>
<td><p>The interaction id is set to 0 at the start of each test and increments for every interaction.</p></td>
</tr>
<tr class="even">
<td><p>interactionType</p></td>
<td><p>BSTR</p></td>
<td><p>The interactionType, such as tap, arc, and line, defines how to get from each starting point to each ending point and gives the intent of the interaction object. See the section named Interaction Types for a full listing.</p></td>
</tr>
<tr class="odd">
<td><p>count</p></td>
<td><p>ULONG</p></td>
<td><p>The number of contacts in each array.</p></td>
</tr>
<tr class="even">
<td><p>xFrom</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The starting X position of each contact with respect to the top left of the screen and the positive axis running to the right and down.</p>
<div class="alert">
<strong>Note</strong>  
<p>The starting X and Y positions can be negative, representing points on the device bezel. This is used in some of the edgy tests.</p>
</div>
<div>
 
</div>
<p>Unit: millimeters</p></td>
</tr>
<tr class="odd">
<td><p>xTo</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The ending X position of each contact.</p>
<p>Unit: millimeters</p></td>
</tr>
<tr class="even">
<td><p>yFrom</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The starting Y position of each contact.</p>
<div class="alert">
<strong>Note</strong>  
<p>The starting X and Y positions can be negative, representing points on the device bezel. This is used in some of the edgy tests.</p>
</div>
<div>
 
</div>
<p>Unit: millimeters</p></td>
</tr>
<tr class="odd">
<td><p>yTo</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The ending Y position of each contact.</p>
<p>Unit: millimeters</p></td>
</tr>
<tr class="even">
<td><p>startTimes</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The start time offset from 0 of each contact.</p>
<div class="alert">
<strong>Note</strong>  
<p>The touch certification tool will wait indefinitely for input.</p>
</div>
<div>
 
</div>
<p>Unit: milliseconds</p></td>
</tr>
<tr class="odd">
<td><p>endTimes</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The end time offset from 0 of each contact. The duration of any contact is given by <strong>endTimes</strong>[contact] –<strong>startTimes</strong>[contact].</p>
<p>The contact speed can be calculated from <strong>startTime</strong> or <strong>endTime</strong> and <strong>startPosition</strong> and <strong>endPosition</strong>. Unless a specific acceleration profile is given, the robot uses whatever is convenient within the time bounds. The speed should remain relatively smooth.</p>
<p>Unit: milliseconds</p></td>
</tr>
<tr class="even">
<td><p>endHoldTimes</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The length of time each contact should be pressed on the surface before releasing.</p>
<p>Unit: milliseconds</p></td>
</tr>
<tr class="odd">
<td><p>rotation</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The amount of rotation moving clockwise from start to end.</p>
<p>Unit: radians</p></td>
</tr>
<tr class="even">
<td><p>xCenter</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The x center point to rotate around for circle and arcs for each contact.</p>
<p>Unit: millimeters</p></td>
</tr>
<tr class="odd">
<td><p>yCenter</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The y center point to rotate around for circle and arcs for each contact.</p>
<p>Unit: millimeters</p></td>
</tr>
<tr class="even">
<td><p>zDistance</p></td>
<td><p>DOUBLE*</p>
<p>(Array of count elements)</p></td>
<td><p>The distance a contact should remain from the screen.</p>
<p>Unit: millimeters</p></td>
</tr>
<tr class="odd">
<td><p>accelerationProfile</p></td>
<td><p>ULONG</p></td>
<td><p>The expected acceleration profile. For a list of definitions, see the Acceleration Profiles section.</p></td>
</tr>
</tbody>
</table>

 

### <span id="Interaction_Types"></span><span id="interaction_types"></span><span id="INTERACTION_TYPES"></span>Interaction Types

More than one interaction type can cover an interaction that the robot could perform. For example, a tap on the screen could be performed with a line interaction with the same start and stop points. In these cases, a more specific type is given to hint at the intent of the test. The interaction type of **IInteractionObject** can be retrieved by calling the **GetParameter** method with the name parameter as **interactionType**. The returned out-parameter is of the BSTR type indicating what interaction type it is.

The following table lists the interaction types:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Tap</p></td>
<td><p>A set of quick down up motions</p></td>
<td><p><strong>Used IInteractionObject parameters:</strong> count, xFrom, yFrom, xTo, yTo, startTimes, endTimes</p>
<p><strong>Unused IInteractionObject parameters:</strong> rotation, xCenter, yCenter, zDistance, accelerationProfile, endHoldTimes</p>
<p>For example, at the starting time offset <strong>startTimes\[i]</strong> (i &lt; count), the robot should place contact i at the coordinate location (<strong>xFrom[i]</strong>, <strong>yFrom[i]</strong>). It should remain in contact until <strong>endTimes[i]</strong>, when the contact should be released. It is expected (<strong>xFrom[i]</strong> == <strong>xTo[i]</strong>) and (<strong>yFrom[i]</strong> == <strong>yTo[i]</strong>) so the <strong>xTo</strong> and <strong>yTo</strong> parameters can be ignored.</p></td>
</tr>
<tr class="even">
<td><p>Line</p></td>
<td><p>A [set] of non-intersecting lines</p></td>
<td><p><strong>Used IInteractionObject parameters:</strong> count, xFrom, yFrom, xTo, yTo, startTimes, endTimes</p>
<p><strong>Unused IInteractionObject parameters:</strong> rotation, xCenter, yCenter, zDistance, accelerationProfile, endHoldTimes</p>
<p>For example, at the starting time offset <strong>startTimes\[i]</strong> (i &lt; count) the robot should place contact i at the coordinate location (<strong>xFrom[i]</strong>, <strong>yFrom[i]</strong>). It should remain in contact and move in straight line to (<strong>xTo[i]</strong>, <strong>yTo[i]</strong>) at the time offset of <strong>endTimes[i]</strong>, when the contact should be released. There is no restriction on the moving speed and robot can do whatever is convenient.</p></td>
</tr>
<tr class="odd">
<td><p>Rotate</p></td>
<td><p>A [set] of circular arcs</p></td>
<td><p><strong>Used IInteractionObject parameters:</strong> count, xFrom, yFrom, xCenter, yCenter, rotation, startTimes, endTimes</p>
<p><strong>Unused IInteractionObject parameters:</strong> xTo, yTo, zDistance accelerationProfile, endHoldTimes</p>
<p>For example. at the starting time offset <strong>startTimes\[i]</strong> (i&lt;count), the robot should place contact i at the coordinate location (<strong>xFrom[i]</strong>, <strong>yFrom[i]</strong>). It should remain in contact and move in arc clockwise by radian indicated by the value of <strong>rotation[i]</strong>. The arc center is at (<strong>xCenter[i]</strong>, <strong>yCenter[i]</strong>). The interaction must finish by <strong>endTimes[i]</strong>, when the contact should be released.</p>
<p></p>
<p>Figure 1 shows how these parameters are used to perform the rotate interaction.</p></td>
</tr>
<tr class="even">
<td><p>Hover</p></td>
<td><p>Hold contacts above the screen without touching</p></td>
<td><p><strong>Used IInteractionObject parameters:</strong> count, xFrom, yFrom, xTo, yTo, zDistance, startTimes, endTimes</p>
<p><strong>Unused IInteractionObject parameters:</strong> rotation, xCenter, yCenter, accelerationProfile, endHoldTimes</p>
<p>For example, at the starting time offset <strong>startTimes\[i]</strong> (i&lt;count), the robot should hover contact i at the coordinate location (<strong>xFrom[i]</strong>, <strong>yFrom[i]</strong>). The distance of the contact from the screen surface is defined by <strong>zDistance[i]</strong>. Note this represents the distance for an average human finger. For a robotic finger – the robot should adjust this height with respect to the difference in capacitance (if any). The hovering contact should remain stable and be removed at <strong>endTimes[i]</strong>. For this release, the hovering is stationary, and the <strong>xTo</strong> and <strong>yTo</strong> parameters can be ignored.</p></td>
</tr>
<tr class="odd">
<td><p>Zoom</p></td>
<td><p>Diverging or converging non-intersecting lines</p></td>
<td><p><strong>Used IInteractionObject parameters:</strong> count, xFrom, yFrom, xTo, yTo, startTimes, endTimes</p>
<p><strong>Unused IInteractionObject Parameters:</strong> Rotation, xCenter, yCenter, zDistance, accelerationProfile, endHoldTimes</p>
<p>For example, zoom interaction is similar to Line interaction, with the exception that one contact will be stationary. If the contact i is stationary, then the following will be true: (<strong>xFrom[i]</strong> == <strong>xTo[i]</strong>) and (<strong>yFrom[i]</strong> == <strong>yTo[i]</strong>).</p>
<p>Please refer to the Line interaction on how to perform the Zoom interaction.</p>
<p>For a pan interaction, the parameters are the same but the contact will not be stationary. Therefore, (xFrom[i] != xTo[i]) and (yFrom[i] != yTo[i]).</p></td>
</tr>
<tr class="even">
<td><p>TouchKeyboard</p></td>
<td><p>Multiple taps, linearly offset from one another</p></td>
<td><p><strong>Used IInteractionObject parameters:</strong> count, xFrom, yFrom, xTo, yTo, startTimes, endTimes</p>
<p><strong>Unused IInteractionObject parameters:</strong> rotation, xCenter, yCenter, zDistance, accelerationProfile, endHoldTimes</p>
<p>For example, the TouchKeyboard interaction is a sequence of tapping on the screen, just like a person tapping the on-screen soft keyboard.</p>
<p>At the starting time offset <strong>startTimes\[i]</strong> (i&lt;count), the robot should place contact i at the coordinate location (<strong>xFrom[i]</strong>, <strong>yFrom[i]</strong>). It should remain in contact until the time offset of <strong>endTimes[i]</strong>, when the contact should be released. Just like Tap interaction, it is expected (<strong>xFrom[i]</strong> == <strong>xTo[i]</strong>) and (<strong>yFrom[i]</strong> == <strong>yTo[i]</strong>) so the <strong>xTo</strong> and <strong>yTo</strong> parameters can be ignored.</p>
<p>Suppose there are 4 contacts required by the interaction and the parameters have the following value:</p>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Contact index</th>
<th>0</th>
<th>1</th>
<th>2</th>
<th>3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>startTimes</p></td>
<td><p>0</p></td>
<td><p>200</p></td>
<td><p>400</p></td>
<td><p>600</p></td>
</tr>
<tr class="even">
<td><p>endTimes</p></td>
<td><p>100</p></td>
<td><p>300</p></td>
<td><p>500</p></td>
<td><p>70000</p></td>
</tr>
<tr class="odd">
<td><p>xFrom</p></td>
<td><p>20</p></td>
<td><p>40</p></td>
<td><p>60</p></td>
<td><p>80</p></td>
</tr>
<tr class="even">
<td><p>yFrom</p></td>
<td><p>40</p></td>
<td><p>40</p></td>
<td><p>40</p></td>
<td><p>40</p></td>
</tr>
</tbody>
</table>
<p> </p>
<p>It is a sequence of tapping 4 points in line from (20, 40) to (80, 40). The unit is in millimeters.</p>
<p>The robot should perform the interaction as follows:</p>
<ol>
<li><p>At time offset 0 ms, it should place contact 0 down at (20, 40), hold for 100ms and up at 100ms.</p></li>
<li><p>At time offset 200 ms, it should place contact 1 down at (40, 40), hold for 100ms and up at 300ms.</p></li>
<li><p>At time offset 400 ms, it should place contact 2 down at (60, 40), hold for 100ms and up at 500ms.</p></li>
<li><p>At time offset 600 ms, it should place contact 4 down at (80, 40), hold for 100ms and up at 600ms.</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Non-Interaction</p></td>
<td><p>No interaction needed</p></td>
<td><p><strong>Used IInteractionObject parameters:</strong> count, startTimes, endTimes</p>
<p><strong>Unused IInteractionObject parameters:</strong> rotation, xCenter, yCenter, zDistance, xFrom, yFrom, xTo, yTo, accelerationProfile, endHoldTimes</p>
<p><strong>endTimes</strong>[0] gives the length of time to not perform any interaction. The robot should not place any contacts on the screen. If hovering, the contacts must be far enough away from the screen so the device will not recognize a hovering contact.</p>
<p><strong>startTimes</strong>[0] is expected to be 0.</p></td>
</tr>
<tr class="even">
<td><p>Toss</p></td>
<td><p>A single line with a defined accelerationProfile. Toss interactions have their speed checked by logo.</p>
<p>For this release, only acceleration profile 2 (Accelerate) is used.</p></td>
<td><p><strong>Used IInteractionObject parameters:</strong> count, xFrom, yFrom, xTo, yTo, accelerationProfile, startTimes, endTimes</p>
<p><strong>Unused IInteractionObject parameters:</strong> rotation, xCenter, yCenter, zDistance, endHoldTimes</p>
<p>For example, suppose the <strong>accelerationProfile</strong>[0] is 2 (accelerate), at start time offset <strong>startTimes</strong>[0], the robot should place contact 0 down at start point (<strong>xFrom</strong>[0], <strong>yFrom</strong>[0]). It should move the contact towards end point (<strong>xTo</strong>[0], <strong>yTo</strong>[0]), accelerating. By the time <strong>endTimes</strong>[0], the contact should reach end point and the robot should lift the contact up, without stopping.</p></td>
</tr>
<tr class="odd">
<td><p>MoveAndHold</p></td>
<td><p>Similar to Line, but the contacts should be held at the end of movement for a specific length of time before releasing</p></td>
<td><p><strong>Used IInteractionObject parameters:</strong> count, xFrom, yFrom, xTo, yTo, startTimes, endTimes, endHoldTimes</p>
<p><strong>Unused IInteractionObject parameters:</strong> rotation, xCenter, yCenter, zDistance, accelerationProfile</p>
<p>This interaction is similar to Line interaction, except that at the end of movement, the contacts are not released immediately. Instead, they are held pressed down to the surface for an amount of time specified by the <strong>endHoldTimes</strong> parameter. The end time of movement for contact i is calculated by (<strong>endTimes</strong>[i] –<strong>endHoldTimes</strong>[i]).</p>
<p>For example, at the starting time offset <strong>startTimes\[i]</strong> (i&lt;count), the robot should place contact i at the coordinate location (<strong>xFrom</strong>[i], <strong>yFrom</strong>[i]). It should remain in contact and move in straight line to (<strong>xTo</strong>[i], <strong>yTo</strong>[i]) at the time offset of (<strong>endTimes</strong>[i] - <strong>endHoldTimes</strong>[i]). Then the contact should be held stable until time offset <strong>endTimes</strong>[i], when it is released from the surface. There is no restriction on the moving speed and robot can do whatever is convenient, as long as the contacts reach destination at or before the required time offset.</p>
<p>For this release, you can expect the number of contacts (<strong>count</strong>) to be 1.</p></td>
</tr>
</tbody>
</table>

>[!NOTE]
>  
Even parameters marked as unused may be defined. The API consumer should be robust against extra information stored in the **InteractionObject**.

 

### <span id="Rotate_Interaction_Type_and_Parameters"></span><span id="rotate_interaction_type_and_parameters"></span><span id="ROTATE_INTERACTION_TYPE_AND_PARAMETERS"></span>Rotate Interaction Type and Parameters

The following figure (Figure 1) shows how the parameters of a rotation interaction are used to perform a rotate interaction.

![how to perform a rotate interaction](images/hck-win8-robot-figure1.jpg)

### <span id="Acceleration_Profiles"></span><span id="acceleration_profiles"></span><span id="ACCELERATION_PROFILES"></span>Acceleration Profiles

The following table lists the four acceleration profiles:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Profile Name</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Default</p></td>
<td><p>0</p></td>
<td><p>The contact goes straight down to the screen surface, moves to the end point, stops and lifts up from the surface.</p></td>
</tr>
<tr class="even">
<td><p>Decelerate</p></td>
<td><p>1</p></td>
<td><p>The contact moves at certain speed horizontally, decelerating and is lowered to make a contact on the screen surface, moves to the end point, stops and lifts up from the surface.</p></td>
</tr>
<tr class="odd">
<td><p>Accelerate</p></td>
<td><p>2</p></td>
<td><p>The contact goes straight down to the screen surface and then starts to move to the end point accelerating. It is lifted up while moving at the end point.</p></td>
</tr>
<tr class="even">
<td><p>Constant speed</p></td>
<td><p>3</p></td>
<td><p>The contact moves at a certain speed horizontally. While lowering down to make a contact with the screen surface, it maintains the same horizontal speed. On the surface it moves to the end point and lifts up while moving. Its horizontal speed does not change during the entire interaction.</p></td>
</tr>
</tbody>
</table>

 

The following figure (Figure 2) shows the robot contact movement for the acceleration profiles. Start contact point and end contact point refer to the circles in the diagram. The diagram shows the robot contact movement viewed from the side of the device screen surface.

![illustration of acceleration profiles](images/hck-win8-robot-figure2.jpg)

### <span id="When_to_implement"></span><span id="when_to_implement"></span><span id="WHEN_TO_IMPLEMENT"></span>When to implement

You should not implement the interface. You will be passed a pointer to this interface in response to a call to **ILogoAutomation::QueryInteraction**.

### <span id="Error_codes"></span><span id="error_codes"></span><span id="ERROR_CODES"></span>Error codes

The following table summarizes the interface custom error codes defined for the **IInteractionObject** interface:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Error code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0x80040000</p></td>
<td><p>The test does not exist.</p></td>
</tr>
<tr class="even">
<td><p>0x80040001</p></td>
<td><p>The test has already been completed.</p></td>
</tr>
<tr class="odd">
<td><p>0x80040002</p></td>
<td><p>The parameter name is not found.</p></td>
</tr>
<tr class="even">
<td><p>0x80040003</p></td>
<td><p>There is no information for the interaction.</p></td>
</tr>
<tr class="odd">
<td><p>0x80040005</p></td>
<td><p>The interaction ID is not correct.</p></td>
</tr>
</tbody>
</table>

 

### <span id="BKMK_ILogoEvenHandler"></span><span id="bkmk-ilogoevenhandler"></span><span id="BKMK_ILOGOEVENHANDLER"></span>Interface: ILogoEventHandler

This interface specifies how the touch certification tool will notify the robot controller about what is happening in the test run. The robot controller should implement this interface to get callbacks from the touch certification tool for status updates.

Implementation of this interface should not place time consuming work or any **ILogoAutomation** method calls inside of these methods since it will block the touch certification tool. Unless these methods return, the touch certification tool will not respond to inputs or any **ILogoAutomation** method calls.

**Caution**  
Failing to follow this rule may cause the touch certification tool to stop responding.

 

### <span id="Overview"></span><span id="overview"></span><span id="OVERVIEW"></span>Overview

``` syntax
interface ILogoEventHandler : IDispatch{
    HRESULT LogoExit();
    HRESULT TestStarted(
        [in] BSTR testName);
    HRESULT TestCompleted(
        [in] BSTR testName,
        [in] BOOL testSucceeded);
    HRESULT InteractionStarted(
        [in] BSTR testName,
        [in] ULONG interactionId);
    HRESULT InteractionCompleted(
        [in] BSTR testName,
        [in] ULONG interactionId,
        [in] BOOL interactionSucceeded, 
        [in] BSTR failureReason);
};
```

### <span id="Methods"></span><span id="methods"></span><span id="METHODS"></span>Methods

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>LogoExit</p></td>
<td><p>Called when the touch certification tool is about to exit, usually in response to a call to <strong>ILogoAutomation::Exit()</strong>. The robot should clean all of its state related to the touch certification tool.</p></td>
</tr>
<tr class="even">
<td><p>TestStarted</p></td>
<td><p>Called whenever the touch certification tool switches to a different test page, including the Table of Contents. At this point, the robot should call <strong>ILogoAutomation::StartTest</strong> if <strong>testName</strong> is “Table of Contents,” or call <strong>ILogoAutomation::QueryInteraction</strong> to get information on the interaction expected and then perform the interaction.</p></td>
</tr>
<tr class="odd">
<td><p>TestCompleted</p></td>
<td><p>Called whenever a test is completed. At this point, the robot should call <strong>ILogoAutomation::ExitTest</strong> to return to the table of contents, and then <strong>StartTest</strong> to start a new test.</p></td>
</tr>
<tr class="even">
<td><p>InteractionStarted</p></td>
<td><p>Called when the touch certification tool sees the first contact of a new interaction going.</p></td>
</tr>
<tr class="odd">
<td><p>InteractionCompleted</p></td>
<td><p>Called whenever the touch certification tool sees that all input has departed and the interaction is over. This call may be followed by <strong>TestCompleted</strong>. If this event is not being fired, it is an error case that the robot should handle. For more information about error handling, see [Error handling](#bkmk-errorhandling).</p></td>
</tr>
</tbody>
</table>

 

### <span id="Generate_Files_to_Integrate_Robot_to_HLK"></span><span id="generate_files_to_integrate_robot_to_hlk"></span><span id="GENERATE_FILES_TO_INTEGRATE_ROBOT_TO_HLK"></span>Generate Files to Integrate Robot to HLK

To integrate the robot to the HCK, the files logo3.tlb, logo3.h and logo3\_i.c are used. These define the interfaces described above.

### <span id="Define_logo3.idl_library"></span><span id="define_logo3.idl_library"></span><span id="DEFINE_LOGO3.IDL_LIBRARY"></span>Define logo3.idl library

Define the logo3.idl. For more information on IDL (Interface Definition Language) file, see [this web page](http://msdn.microsoft.com/en-us/library/windows/desktop/aa378712.aspx).

Refer to the following sample:

``` syntax
import "oaidl.idl";
import "ocidl.idl";
import "Propidl.idl";
 
[
    object,
    dual,
    uuid(25d2b24d-679d-4131-89a7-eeaf10f4cb85),
    pointer_default(unique)
]
interface ILogoEventHandler : IDispatch{
    HRESULT LogoExit();
    HRESULT TestStarted(
        [in] BSTR testName);
    HRESULT TestCompleted(
        [in] BSTR testName,
        [in] BOOL testSucceeded);
    HRESULT InteractionStarted(
        [in] BSTR testName,
        [in] ULONG interactionId);
    HRESULT InteractionCompleted(
        [in] BSTR testName,
        [in] ULONG interactionId,
        [in] BOOL interactionSucceeded, 
        [in] BSTR failureReason);
};
 
[
    object,
    uuid(2F900384-8ED7-417D-87EA-F2C9F419F356),
    dual,
    nonextensible,
    pointer_default(unique)
]
interface IInteractionObject : IDispatch{
        HRESULT SetParameter(
        [in] BSTR name,
        [in] VARIANT value);
    HRESULT GetParameter(
        [in] BSTR name,
        [out] VARIANT* value);
};
 
[
    object,
    uuid(453D0AC0-AF7C-465B-AA61-2641C5F24366),
    dual,
    pointer_default(unique)
]
interface ILogoAutomation : IDispatch {
    HRESULT QueryCurrentVersion(
        [out] ULONG* version);
    HRESULT QueryCurrentState(
        [out] BSTR* testName,
        [out] ULONG* nContactsDown);
    HRESULT QueryAvailableTests(
        [out] VARIANT* testNames);
 
   HRESULT StartTest(
        [in] BSTR testName);
    HRESULT ExitTest();
    HRESULT Exit();
    HRESULT HideStatusUI();
    HRESULT ShowStatusUI();
 
    HRESULT QueryInteraction(
        [out] IInteractionObject** interaction);
    HRESULT FailInteraction(
        [in] ULONG interactionId,
        [in] BSTR reason);
 
    HRESULT RegisterEventSink(
        [in] ILogoEventHandler* eventSink, 
        [out] ULONG* cookie);
    HRESULT UnregisterEventSink(
        [in] ULONG cookie);
};
 
 
[
    uuid(58147694-B012-4922-8A48-48E3ABCC1B57),
    version(1.0),
]
library logo3Lib
{
    importlib("stdole2.tlb");
    interface ILogoEventHandler;
 
    [
        uuid(D371B1A6-30AF-4F43-8202-E13A3C93DA8C)        
    ]
    coclass LogoAutomation
    {
        [default] interface ILogoAutomation;
    };
    [
        uuid(8F34541E-0742-470D-9AA9-100E7984EA22)        
    ]
    coclass InteractionObject
    {
        [default] interface IInteractionObject;
    };
};
 
```

### <span id="Generate_logo3.tlb__logo3.h_and_logo3_i.c"></span><span id="generate_logo3.tlb__logo3.h_and_logo3_i.c"></span><span id="GENERATE_LOGO3.TLB__LOGO3.H_AND_LOGO3_I.C"></span>Generate logo3.tlb, logo3.h and logo3\_i.c

Once the interfaces and the library have been defined, use the [MIDL (Microsoft Interface Definition Language) compiler](http://msdn.microsoft.com/en-us/library/windows/desktop/aa367300.aspx) to create logo3.tlb, logo3.h and logo3\_i.c. Use the following process:

1.  Install Visual Studio and the SDK.

2.  Define logo3.idle file as shown above.

3.  Use the Visual Studio command prompt to run midl. If not, ensure that path to cl.exe is accessible.

4.  Run midl.exe. For example, `midl.exe /out c:\Folder c:\Folder\logo3.idl`.

5.  Create a Visual Studio project

6.  Add the logo3.idl file to the resources of the project.

7.  Copy logo3\_i.c and logo3.h to the project’s folder

8.  In Visual Studio, add project **Properties** &gt; **Additional dependencies** **Propsys.lib**

9.  Build the project.

### <span id="When_to_implement"></span><span id="when_to_implement"></span><span id="WHEN_TO_IMPLEMENT"></span>When to implement

Developers should implement this interface and register it with the touch certification tool by calling **ILogoAutomation::RegisterEventSink**. This allows the robot controller to respond to touch certification tool events, instead of polling the state of the tool.

After registration, the interface will get callbacks for any events that happen.

>[!NOTE]
>  
Make sure to call this method to unregister the event sink before the robot controller is finished. Failing to do so may cause the status UI to freeze for several minutes before DCOM times out. The touch certification tool may try to call the event sink to deliver status updates and will be blocked by an event sink that is not responding. Eventually, the RPC call will timeout and the touch certification tool will recover and automatically unregister the event sink that is not responding.

If the robot controller crashes, or the network is not available, the call to **UnregisterEventSink** cannot be guaranteed so the status UI may stop responding for a while. In such cases, if you want to preserve the previous touch certification tool test results, you should wait at least 6 minutes to allow the touch certification tool to recover from an RPC call timeout. If you do not need to preserve the previous test results, you can stop the touch certification tool process.

 

## <span id="Code_Sample"></span><span id="code_sample"></span><span id="CODE_SAMPLE"></span>Code Sample


This is a partial example of how a robot controller could use the robot APIs.

>[!NOTE]
>  
This example does not cover error handling. For more information about error handling, see [Error handling](#bkmk-errorhandling).

 

``` syntax
#include <stdio.h>
#include <tchar.h>

#include <Windows.h>
#include <Propvarutil.h>
#include <string>
#include <vector>
#include <assert.h>

// Make sure you have set the correct header file path to the SDK.
#include #logo3.h#
#include #logo3_i.c#

#define CHECK_HR(EXPR)              \
    do                              \
    {                               \
        hr = (EXPR);                \
        if (FAILED(hr))             \
        {                           \
            printf("File = %s, Line# = %u, %s failed with 0x%x\n", __FILE__, __LINE__, #EXPR, hr);  \
            goto Exit;              \
        }                           \
    } while (FALSE, FALSE);         \
    
class AutoBSTR
{
public:
    AutoBSTR(PCWSTR str)
    {
        m_str = SysAllocString(str);
    }

    ~AutoBSTR()
    {
        SysFreeString(m_str);
    }

    operator BSTR() const throw()
    {
return m_str;
    }

private:
    BSTR m_str;
};

class LogoEventHandler : public ILogoEventHandler
{
public:
    LogoEventHandler(ILogoAutomation* plogo) : 
      m_refCount(1), 
      m_eventTestStarted(NULL),
      m_eventInteractionCompleted(NULL),
      m_currentInteractionId(0)
    {
    }

    ~LogoEventHandler()
    {
        if (m_eventTestStarted != NULL)
        {
            CloseHandle(m_eventTestStarted);
        }

        if (m_eventInteractionCompleted != NULL)
        {
            CloseHandle(m_eventInteractionCompleted);
        }
    }

    HRESULT Initialize()
    {
        m_eventTestStarted = CreateEvent(NULL, FALSE, FALSE, NULL);
        if (m_eventTestStarted == NULL)
        {
            return HRESULT_FROM_WIN32(GetLastError());
        }

        m_eventInteractionCompleted = CreateEvent(NULL, FALSE, FALSE, NULL);
        if (m_eventInteractionCompleted == NULL)
        {
            return HRESULT_FROM_WIN32(GetLastError());
        }

        return S_OK;
    }

public:
    // ILogoEventHandler Methods
    STDMETHOD(TestStarted)(BSTR testName)
    {
        wprintf(L"[Logo] Test started. Name = %s\n", testName);
        SetEvent(m_eventTestStarted);
        return S_OK;
    }

    STDMETHOD(TestCompleted)(BSTR testName, BOOL testSucceeded)
    {
        wprintf(L"[Logo] Test Completed. Name = %s, Result = %s\n", testName,
            testSucceeded ? L"Passed" : L"Failed");

        return S_OK;
    }

    STDMETHOD(InteractionStarted)(BSTR testName, ULONG interactionId)
    {
        wprintf(L"[Logo] Interaction started. id = %u\n", interactionId);
        return S_OK;
    }

    STDMETHOD(InteractionCompleted)(BSTR testName, ULONG interactionId, BOOL interactionSucceeded, BSTR failureReason)
    {
        wprintf(L"[Logo] Interaction completed. id = %u, %s\n", interactionId,
            interactionSucceeded ? L"succeeded" : L"failed");

        if (!interactionSucceeded)
        {
            wprintf(L"[Logo] Failure reason: %s\n", failureReason);
        }

        SysFreeString(failureReason);

        m_currentInteractionId = interactionId;
        SetEvent(m_eventInteractionCompleted);

        return S_OK;
    }

    STDMETHOD(LogoExit)()
    {
        wprintf(L"[Logo] Logo exited.\n");

        return S_OK;
    }
    // end of ILogoEventHandler Methods

    // IUnknown methods
    STDMETHODIMP_(ULONG) AddRef()
    {
        InterlockedIncrement(&m_refCount);
        return m_refCount;
    }

    STDMETHODIMP_(ULONG) Release()
    {
        InterlockedDecrement(&m_refCount);

        if (m_refCount == 0)
        {
            delete this;
        }

        return m_refCount;
    }

    STDMETHODIMP QueryInterface(
      __in   REFIID riid,
      __out  void **ppvObject)
    {
        if (ppvObject == NULL)
        {
            return E_POINTER;
        }

        if (riid == IID_ILogoEventHandler || riid == IID_IUnknown)
        {
            AddRef();
            *ppvObject = this;
            return S_OK;
        }

        *ppvObject = NULL;
        return E_NOINTERFACE;
    }
    // End of IUnknown methods

    // IDispatch methods
    STDMETHODIMP GetTypeInfoCount( 
        __RPC__out UINT *pctinfo)
    {
        return E_NOTIMPL;
    }

    STDMETHODIMP GetTypeInfo( 
        __in UINT iTInfo,
        __in LCID lcid,
        __RPC__deref_out_opt ITypeInfo **ppTInfo)
    {
        return E_NOTIMPL;
    }

    STDMETHODIMP GetIDsOfNames( 
        __RPC__in REFIID riid,
        __RPC__in_ecount_full(cNames) LPOLESTR *rgszNames,
        __RPC__in_range(0,16384) UINT cNames,
        LCID lcid,
        __RPC__out_ecount_full(cNames) DISPID *rgDispId)
    {
        return E_NOTIMPL;
    }

    STDMETHODIMP Invoke( 
        /* [in] */ DISPID dispIdMember,
        /* [in] */ REFIID riid,
        /* [in] */ LCID lcid,
        /* [in] */ WORD wFlags,
        /* [out][in] */ DISPPARAMS *pDispParams,
        /* [out] */ VARIANT *pVarResult,
        /* [out] */ EXCEPINFO *pExcepInfo,
        /* [out] */ UINT *puArgErr)
    {
        return E_NOTIMPL;
    }
    // End of IDispatch methods

public:
    HRESULT WaitForTestStarted()
    {
        DWORD index = 0;
        HRESULT hr = CoWaitForMultipleHandles(
            0, //flags
            10 * 1000, //timeout
            1, //nHandles
            &m_eventTestStarted, //handles
            &index);

        return hr;
    }

    HRESULT WaitForInteractionCompleted(
        __out ULONG* interactionId)
    {
        DWORD index = 0;
        HRESULT hr = CoWaitForMultipleHandles(
            0, //flags
            10 * 1000, //timeout
            1, //nHandles
            &m_eventInteractionCompleted, //handles
            &index);

        *interactionId = m_currentInteractionId;
        return hr;
    }

private:
    volatile ULONG m_refCount;
    HANDLE m_eventTestStarted;
    HANDLE m_eventInteractionCompleted;
    ULONG m_currentInteractionId;
};

class RobotController
{
public:
    RobotController()
        :
        m_logo(NULL),
        m_logoEventHandler(NULL),
        m_registrationCookie(0),
        m_testNames(NULL),
        m_nTests(0)
    {
    }

    ~RobotController()
    {
        if (m_logo != NULL)
        {
            // Make sure we unregister the event sink before exit.
            m_logo->UnregisterEventSink(m_registrationCookie);
            m_logo->Release();
        }

        if (m_logoEventHandler != NULL)
        {
            m_logoEventHandler->Release();
        }

        VariantClear(&m_testNamesVar);
    }

    HRESULT ConnectToLogo()
    {
        HRESULT hr = S_OK;

        printf("[Robot Controller] Connecting to logo\n");

        // Logo should be running before robot controller trying to connect to it. Otherwise, this call will fail.
        CHECK_HR(CoCreateInstance(
            CLSID_LogoAutomation,
            NULL,
            CLSCTX_LOCAL_SERVER, // | CLSCTX_REMOTE_SERVER for DCOM
            IID_ILogoAutomation,
            (LPVOID*)&m_logo));

        printf("[Robot Controller] Connected to logo\n");

        m_logoEventHandler = new LogoEventHandler(m_logo);

        if (m_logoEventHandler == NULL)
        {
            printf("Cannot allocate memory for LogoEventHandler.\n");
            hr = E_OUTOFMEMORY;
            goto Exit;
        }

        CHECK_HR(m_logoEventHandler->Initialize());

        // Register event sink to logo so we can get status updates from logo.
        CHECK_HR(m_logo->RegisterEventSink(m_logoEventHandler, &m_registrationCookie));

        CHECK_HR(QueryTestNames());

Exit:
        return hr;
    }

    HRESULT RunTest(UINT index)
    {
        HRESULT hr = S_OK;

        if (index >= m_nTests)
        {
            return E_INVALIDARG;
        }

        // First we need to make sure logo is on the "Table of Contents" page. Calling ExitTest() will
        // cause logo to display the "Table of Contents" page.
        CHECK_HR(m_logo->ExitTest());

        // Start the target test - logo will go to the test page.
        CHECK_HR(m_logo->StartTest(m_testNames[index]));
        CHECK_HR(m_logoEventHandler->WaitForTestStarted());

        CHECK_HR(RunInteractions());

Exit:
        return hr;
    }

    HRESULT RunTests()
    {
        HRESULT hr = S_OK;

        // Test 0 is the "Table of Contents" page. Real tests start from index 1.
        for (UINT i = 1; i < m_nTests; i++)
        {
            CHECK_HR(RunTest(i));
        }

        // Shows "Table of Contents" page for status of all tests.
        CHECK_HR(m_logo->ExitTest());

Exit:
        return hr;
    }

private:
    HRESULT QueryTestNames()
    {
        HRESULT hr = S_OK;

        CHECK_HR(m_logo->QueryAvailableTests(&m_testNamesVar));

        m_nTests = m_testNamesVar.parray->rgsabound->cElements;
        m_testNames = (BSTR*)(m_testNamesVar.parray->pvData);

        printf("Test names---- (%u)\n", m_nTests);
        for (UINT i = 0; i < m_nTests; i++)
        {
            wprintf(L"test %u: %s\n", i, m_testNames[i]);
        }

Exit:
        return hr;
    }

    HRESULT QueryAndPerformInteraction()
    {
        HRESULT hr = S_OK;
        IInteractionObject* interaction = NULL;

        {
            ULONG nContacts = 0;
            BSTR currentTestName = NULL;

            // Check current state to make sure no contacts down before a new interaction.
            CHECK_HR(m_logo->QueryCurrentState(&currentTestName, &nContacts));
            if (nContacts != 0)
            {
                printf("[Robot Controller] There are contacts down on the screen surface. Cannot perform a new interaction.");

                // Real robot controller can instruct robot to remove any contacts from the screen surface instead
                // of failing here.
                hr = E_UNEXPECTED;
                goto Exit;
            }

            hr = m_logo->QueryInteraction(&interaction);
            
            if (hr == 0x80040001)
            {
                printf("[Robot Controller] No more interactions - test has completed.\n");
                goto Exit;
            }
            else if (hr == 0x80040003)
            {
                printf("[Robot Controller] This test does not have any interaction object and requires human input.\n");
                goto Exit;
            }

            CHECK_HR(hr);

            VARIANT var = {};
            ULONG id;
            CHECK_HR(interaction->GetParameter(AutoBSTR(L"id"), &var));
            CHECK_HR(VariantToUInt32(var, &id));
            VariantClear(&var);

            CHECK_HR(interaction->GetParameter(AutoBSTR(L"interactionType"), &var));
            std::wstring interactionType(var.bstrVal);
            VariantClear(&var);

            wprintf(L"[Robot Controller] Interaction id = %u, type = %s\n", id, interactionType.c_str());

            bool interactionPerformed = false;

            // Get interaction parameters based on the type of interaction and used the parameters to 
            // instruct the robot to perform the interaction.
            if (interactionType == L"Line")
            {
                CHECK_HR(GetParamAndPerformLineInteraction(interaction, &interactionPerformed));
            }
            else if (interactionType == L"Non-Interaction")
            {
                CHECK_HR(GetParamAndPerformNonInteraction(interaction, &interactionPerformed));
            }
            // else ...
            // The sample code only demonstrates how to get interaction parameters for Line and Non-Interaction
            // interactions. For other interaction types, please refer to the documentation for what parameters
            // to retrieve from the IInteractionObject. They are similar to how it is done in this sample.

            if (interactionPerformed)
            {
                // If interaction was performed, we should wait for the interaction to complete. A callback
                // from logo to the m_logoEventHandler tells that.
                ULONG completedInteractionId = 0;
                CHECK_HR(m_logoEventHandler->WaitForInteractionCompleted(&completedInteractionId));

                if (id != completedInteractionId)
                {
                    // Interaction id mismatch - it might be device issue or robot performed multiple interactions.
                    hr = E_UNEXPECTED;
                    goto Exit;
                }
            }
            else
            {
                // We couldn't perform the interaction. Set hr to 0x80040001 (Test has already been completed)
                // to allow the sample code to move to the next test.
                hr = 0x80040001;
                goto Exit;
            }
        }

Exit:
        if (interaction != NULL)
        {
            interaction->Release();
        }
        return hr;
    }

    HRESULT GetParamAndPerformNonInteraction(
        __in IInteractionObject* interaction,
        __out bool* interactionPerformed)
    {
        HRESULT hr = S_OK;
        DOUBLE* endTimes = NULL;
        ULONG nEndTimes = 0;

        CHECK_HR(GetDoubles(interaction, L"endTimes", &endTimes, &nEndTimes));

        // It is expected for Non-interaction, there is only 1 element in endTimes array.
        assert(nEndTimes == 1);

        DWORD sleepTime = (DWORD)(endTimes[0]);
        printf("[Robot Controller] Perform non-interaction - no contact of the screen for %ums\n", sleepTime);
        Sleep(sleepTime);

        *interactionPerformed = true;

Exit:
        if (endTimes != NULL)
        {
            CoTaskMemFree(endTimes);
        }
        return hr;
    }

    HRESULT GetParamAndPerformLineInteraction(
        __in IInteractionObject* interaction,
        __out bool* interactionPerformed)
    {
        HRESULT hr = S_OK;
        DOUBLE* xFrom = NULL;
        DOUBLE* yFrom = NULL;
        DOUBLE* xTo = NULL;
        DOUBLE* yTo = NULL;
        DOUBLE* startTimes = NULL;
        DOUBLE* endTimes = NULL;
        ULONG count = 0;
        ULONG n = 0;

        // Get all the interaction parameters used by a Line interaction.
        CHECK_HR(GetDoubles(interaction, L"xFrom", &xFrom, &n));
        count = n;

        CHECK_HR(GetDoubles(interaction, L"yFrom", &yFrom, &n));
        assert(count == n);

        CHECK_HR(GetDoubles(interaction, L"xTo", &xTo, &n));
        assert(count == n);

        CHECK_HR(GetDoubles(interaction, L"yTo", &yTo, &n));
        assert(count == n);

        CHECK_HR(GetDoubles(interaction, L"startTimes", &startTimes, &n));
        assert(count == n);

        CHECK_HR(GetDoubles(interaction, L"endTimes", &endTimes, &n));
        assert(count == n);

        printf("Interaction parameters:\n");
        PrintVector(L"xFrom", xFrom, count);
        PrintVector(L"yFrom", yFrom, count);
        PrintVector(L"xTo", xTo, count);
        PrintVector(L"yTo", yTo, count);
        PrintVector(L"startTimes", startTimes, count);
        PrintVector(L"endTimes", endTimes, count);

        // Instruct robot to perform interaction based on the parameters.
        // This sample does not show how to control the robot as it is very specific to 
        // the robot designer. This sample does not perform this interaction.
        *interactionPerformed = false;

Exit:
        if (xFrom != NULL)
        {
            CoTaskMemFree(xFrom);
        }

        if (yFrom != NULL)
        {
            CoTaskMemFree(yFrom);
        }

        if (xTo != NULL)
        {
            CoTaskMemFree(xTo);
        }

        if (yTo != NULL)
        {
            CoTaskMemFree(yTo);
        }

        if (startTimes != NULL)
        {
            CoTaskMemFree(startTimes);
        }

        if (endTimes != NULL)
        {
            CoTaskMemFree(endTimes);
        }

        return hr;
    }

    HRESULT RunInteractions()
    {
        HRESULT hr = S_OK;

        // Hide the status UI before doing interaction.
        CHECK_HR(m_logo->HideStatusUI());

        bool hasMoreIteration = true;

        while (hasMoreIteration)
        {
            // Usually a test needs multiple iterations of interactions. 
            hr = QueryAndPerformInteraction();

            if (hr == 0x80040001)
            {
                // The test has been completed.
                hasMoreIteration = false;
                hr = S_OK;
            }

            CHECK_HR(hr);
        }

Exit:
        // Re-display the status UI for human to review the test status.
        m_logo->ShowStatusUI();
        return hr;
    }

    HRESULT GetDoubles(
        __in IInteractionObject *interaction, 
        __in PCWSTR paramName,
        __out_ecount(*length) DOUBLE** doubleArray,
        __out ULONG* length)
    {
        VARIANT var = {};
        HRESULT hr = interaction->GetParameter(AutoBSTR(paramName), &var);

        if (SUCCEEDED(hr))
        {
            hr = VariantToDoubleArrayAlloc(var, doubleArray, length);
        }
    
        VariantClear(&var);

        return hr;
    }

    void PrintVector(
        __in PCWSTR name,
        __in_ecount(count) const DOUBLE* vector,
        __in ULONG count)
    {
        wprintf(L"%s\n", name);

        for (ULONG i = 0; i < count; i++)
        {
            printf("%.2f ", vector[i]);
        }

        printf("\n");
    }

private:
    ILogoAutomation* m_logo;
    LogoEventHandler* m_logoEventHandler;
    ULONG m_registrationCookie;
    BSTR* m_testNames;
    ULONG m_nTests;
    VARIANT m_testNamesVar;

};

int _tmain(int argc, _TCHAR* argv[])
{
    HRESULT hr = S_OK;
    CHECK_HR(CoInitializeEx(NULL, COINIT_APARTMENTTHREADED));

    // Extra scope to make sure COM objects are released before calling CoUninitialize.
    {
        RobotController robotController;

        CHECK_HR(robotController.ConnectToLogo());

        CHECK_HR(robotController.RunTests());
    }

Exit:
    CoUninitialize();
    printf("\n[Robot Controller] Shutting down\n");

    return hr;
}
```

## <span id="Robot_API_Configuration"></span><span id="robot_api_configuration"></span><span id="ROBOT_API_CONFIGURATION"></span>Robot API Configuration


Use the procedures in this section to configure the computer that are used with the robot API.

### <span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Prerequisites

To use the robot API, the following prerequisites must be met:

-   A server running the touch certification tool and a client computer to be used as the robot controller

-   A user account that will be used on both the server and the robot controller

-   The user account used on the server and the robot controller must be a member of the Distributed COM Users security group on both computer. You can add the user account to the group by using the Computer Management console or by using the command line.

### <span id="Configure_the_Robot_API_on_domain-joined_Windows_8_computers"></span><span id="configure_the_robot_api_on_domain-joined_windows_8_computers"></span><span id="CONFIGURE_THE_ROBOT_API_ON_DOMAIN-JOINED_WINDOWS_8_COMPUTERS"></span>Configure the Robot API on domain-joined Windows 8 computers

Use the following procedures to configure the Robot API to work on Windows 8 computers that are joined to the same domain.

**Open TCP port 135 by using Windows Firewall**

1.  On the Start screen, type **Windows Firewall**, click **Settings**, and then click **Windows Firewall** in the search results.

2.  In the **Windows Firewall** console, click **Advanced Settings**.

3.  Right-click Inbound **Rules**, and then click **New Rules**.

4.  On the **Rule Type** page of the **New Inbound Rule Wizard**, click **Port**, and then click **Next**.

5.  On the **Protocol and Ports** page, click **TCP**, click **Specific local ports**, type **135**, and then click **Next**.

6.  On the **Action** page, click **Allow the connection**, and then click **Next**.

7.  On the **Profile** page, select the **Domain**, **Private**, and **Public** check boxes, and then click **Next**.

8.  On the **Name** page, in the **Name** box, specify a name for this rule, such as **Robot API**, and then click **Finish**.

9.  Repeat these steps to create an outbound rule.

10. These steps should be completed on both the server and the robot controller.

You can also open the ports by using the command line by running the following commands:

-   **netsh advfirewall firewall add rule name=”Robot API” dir=in action=allow protocol=TCP localport=135 profile=any**

-   **netsh advfirewall firewall add rule name=”Robot API” dir=out action=allow protocol=TCP localport=135 profile=any**

**Register the touch certification tool**

1.  Log on to the server.

2.  From an elevated command prompt, type **logo3.exe /RegServer** and then press Enter.

    >[!NOTE]
    >  
    The **RegServer** parameter is case sensitive.

     

3.  Repeat these steps on the robot controller.

**Make the touch certification tool interactive by using dcomcnfg.exe**

1.  Log on to the server.

2.  On the Start screen, type **dcomcnfg.exe** and then click **dcomcnfg.exe** from the search results.

3.  Expand **Component Services**, expand **Computers**, expand **My Computer**, and then click **DCOM Config**.

4.  Right-click **Logo3**, and then click **Properties**.

5.  Click the **Identity** tab, and then click **The interactive user**.

6.  Click **OK**.

**Co-create the ILogoAutomation interface**

1.  Log on to the robot controller.

2.  On the Start screen, type **dcomcnfg.exe** and then click **dcomcnfg.exe** from the search results.

3.  Expand **Component Services**, expand **Computers**, expand **My Computer**, and then click **DCOM Config**.

4.  Right-click **Logo3**, and then click **Properties**.

5.  Click the **Location** tab, select the **Run application on the following computer** check box, and then type the name of the server.

6.  Click **OK**.

Alternatively, you can call **CoCreateEx()** and specify the server name. If TCP port 135 is open and the touch certification tool is registered, no further action is required.

Once you have completed all of the procedures in this section, the touch certification tool should be working and the robot controller should be able to connect.

>[!IMPORTANT]
>  
The touch certification tool does not allow com instantiations so it must be running on the server in order for the robot controller to connect.

 

### <span id="Configure_the_Robot_API_on_Windows_8_computers_that_are_not_joined_to_a_domain"></span><span id="configure_the_robot_api_on_windows_8_computers_that_are_not_joined_to_a_domain"></span><span id="CONFIGURE_THE_ROBOT_API_ON_WINDOWS_8_COMPUTERS_THAT_ARE_NOT_JOINED_TO_A_DOMAIN"></span>Configure the Robot API on Windows 8 computers that are not joined to a domain

To configure the Robot API on Windows 8 computers that are not joined to a domain, you must modify the Access Permissions and Launch and Activation Permissions to allow the user account access from the server.

>[!NOTE]
>  
The client and server devices must be either in the same domain or in the same workgroup.

 

**To modify the Access Permissions and Launch and Activation Permissions**

1.  Log on to the server.

2.  On the Start screen, type **dcomcnfg.exe** and then click **dcomcnfg.exe** from the search results.

3.  Expand **Component Services**, and then expand **Computers**.

4.  Right-click **My Computer**, and then click **Properties**.

5.  Click the **COM Security** tab.

6.  Under the **Access Permissions** heading, click **Edit Limits**.

7.  Add the user account, select the **Allow** check boxes for both **Local Access** and **Remote Access**, and then click **OK**.

8.  Under the **Launch and Activation Permissions** heading, click **Edit Limits**.

9.  Add the user account, select the **Allow** check boxes for **Local Launch**, **Remote Launch**, **Local Activation**, and **Remote Activation**, and then click **OK**.

10. Repeat these steps on the robot controller.

### <span id="ARM-based_devices"></span><span id="arm-based_devices"></span><span id="ARM-BASED_DEVICES"></span>ARM-based devices

ARM-based devices are not designed to join a domain so you can follow the procedures in the section named “Configure the Robot API on Windows 8 computers that are not joined to a domain”.

Additionally, you should ensure that the **Enable Distributed COM on this computer** check box is selected in the **Default Properties** tab. It is selected by default.

### <span id="Configure_Windows_7__Windows_XP__or_Windows_Server_robot_controllers"></span><span id="configure_windows_7__windows_xp__or_windows_server_robot_controllers"></span><span id="CONFIGURE_WINDOWS_7__WINDOWS_XP__OR_WINDOWS_SERVER_ROBOT_CONTROLLERS"></span>Configure Windows 7, Windows XP, or Windows Server robot controllers

It is possible that some robot controllers only run by using an earlier version of the Windows operating system. Since the touch certification tool only runs on Windows 8, you cannot register the **ILogoAutomation** interface in the normal way. You must import the type library directly into the Windows registry.

**To import the library directly to the registry**

1.  On the robot controller, create a temporary folder, such as C:\\Logo.

2.  Copy the logo3.tlb file into the temporary folder.

3.  Save the contents of the Touch Certification Tool section into a registry file in the temporary folder.

    >[!NOTE]
    >  
    If you are using a folder other than C:\\Logo as your temporary folder, you must update the registry file with the proper path.

     

4.  From an elevated command prompt, run the registry file to import it into the registry

### <span id="WOW_not_supported_for__RegServer"></span><span id="wow_not_supported_for__regserver"></span><span id="WOW_NOT_SUPPORTED_FOR__REGSERVER"></span>WOW not supported for /RegServer

Using an x86-version of the touch certification tool on an x64-based computer to register the **ILogoAutomation** interface is not supported and will not work. Always use the touch certification tool that matches your processor architecture.

### <span id="Touch_certification_tool_registry_file"></span><span id="touch_certification_tool_registry_file"></span><span id="TOUCH_CERTIFICATION_TOOL_REGISTRY_FILE"></span>Touch certification tool registry file

Here’s the registry file

``` syntax
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\AppID\{BF7FBA21-4E96-403E-8223-6E57C0EBFA82}]
@="Logo3"
[HKEY_CLASSES_ROOT\AppID\logo3.exe]
"AppID"="{BF7FBA21-4E96-403E-8223-6E57C0EBFA82}"
[HKEY_CLASSES_ROOT\Interface\{2F900384-8ED7-417D-87EA-F2C9F419F356}]
@="IInteractionObject"
[HKEY_CLASSES_ROOT\Interface\{2F900384-8ED7-417D-87EA-F2C9F419F356}\ProxyStubClsid]
@="{00020424-0000-0000-C000-000000000046}"
[HKEY_CLASSES_ROOT\Interface\{2F900384-8ED7-417D-87EA-F2C9F419F356}\ProxyStubClsid32]
@="{00020424-0000-0000-C000-000000000046}"
[HKEY_CLASSES_ROOT\Interface\{2F900384-8ED7-417D-87EA-F2C9F419F356}\TypeLib]
@="{58147694-B012-4922-8A48-48E3ABCC1B57}"
"Version"="1.0"
[HKEY_CLASSES_ROOT\Interface\{453D0AC0-AF7C-465B-AA61-2641C5F24366}]
@="ILogoAutomation"
[HKEY_CLASSES_ROOT\Interface\{453D0AC0-AF7C-465B-AA61-2641C5F24366}\ProxyStubClsid]
@="{00020424-0000-0000-C000-000000000046}"
[HKEY_CLASSES_ROOT\Interface\{453D0AC0-AF7C-465B-AA61-2641C5F24366}\ProxyStubClsid32]
@="{00020424-0000-0000-C000-000000000046}"
[HKEY_CLASSES_ROOT\Interface\{453D0AC0-AF7C-465B-AA61-2641C5F24366}\TypeLib]
@="{58147694-B012-4922-8A48-48E3ABCC1B57}"
"Version"="1.0"
[HKEY_CLASSES_ROOT\CLSID\{8F34541E-0742-470D-9AA9-100E7984EA22}]
@="InteractionObject Class"
"AppID"="{BF7FBA21-4E96-403E-8223-6E57C0EBFA82}"
[HKEY_CLASSES_ROOT\CLSID\{8F34541E-0742-470D-9AA9-100E7984EA22}\Programmable]
[HKEY_CLASSES_ROOT\CLSID\{8F34541E-0742-470D-9AA9-100E7984EA22}\TypeLib]
@="{58147694-B012-4922-8A48-48E3ABCC1B57}"
[HKEY_CLASSES_ROOT\CLSID\{8F34541E-0742-470D-9AA9-100E7984EA22}\Version]
@="1.0"
[HKEY_CLASSES_ROOT\CLSID\{D371B1A6-30AF-4F43-8202-E13A3C93DA8C}]
@="LogoAutomation Class"
"AppID"="{BF7FBA21-4E96-403E-8223-6E57C0EBFA82}"
[HKEY_CLASSES_ROOT\CLSID\{D371B1A6-30AF-4F43-8202-E13A3C93DA8C}\Programmable]
[HKEY_CLASSES_ROOT\CLSID\{D371B1A6-30AF-4F43-8202-E13A3C93DA8C}\TypeLib]
@="{58147694-B012-4922-8A48-48E3ABCC1B57}"
[HKEY_CLASSES_ROOT\CLSID\{D371B1A6-30AF-4F43-8202-E13A3C93DA8C}\Version]
@="1.0"
[HKEY_CLASSES_ROOT\Interface\{25D2B24D-679D-4131-89A7-EEAF10F4CB85}]
@="ILogoEventHandler"
[HKEY_CLASSES_ROOT\Interface\{25D2B24D-679D-4131-89A7-EEAF10F4CB85}\ProxyStubClsid]
@="{00020424-0000-0000-C000-000000000046}"
[HKEY_CLASSES_ROOT\Interface\{25D2B24D-679D-4131-89A7-EEAF10F4CB85}\ProxyStubClsid32]
@="{00020424-0000-0000-C000-000000000046}"
[HKEY_CLASSES_ROOT\Interface\{25D2B24D-679D-4131-89A7-EEAF10F4CB85}\TypeLib]
@="{58147694-B012-4922-8A48-48E3ABCC1B57}"
"Version"="1.0"
[HKEY_CLASSES_ROOT\TypeLib\{58147694-B012-4922-8A48-48E3ABCC1B57}]
[HKEY_CLASSES_ROOT\TypeLib\{58147694-B012-4922-8A48-48E3ABCC1B57}\1.0]
@="logo3Lib"
[HKEY_CLASSES_ROOT\TypeLib\{58147694-B012-4922-8A48-48E3ABCC1B57}\1.0\0]
[HKEY_CLASSES_ROOT\TypeLib\{58147694-B012-4922-8A48-48E3ABCC1B57}\1.0\0\win32]
@="C:\\logo\\logo3.tlb"
[HKEY_CLASSES_ROOT\TypeLib\{58147694-B012-4922-8A48-48E3ABCC1B57}\1.0\FLAGS]
@="0"
[HKEY_CLASSES_ROOT\TypeLib\{58147694-B012-4922-8A48-48E3ABCC1B57}\1.0\HELPDIR]
@="C:\\logo"
```

### <span id="DCOM_debugging"></span><span id="dcom_debugging"></span><span id="DCOM_DEBUGGING"></span>DCOM debugging

If you are experiencing issues with DCOM, you can enable DCOM debugging to assist you in troubleshooting.

**To enable DCOM debugging**

1.  On the Start screen, type regedit.exe, and then click regedit.exe from the search results.

2.  Navigate to HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Ole

3.  Create a new DWORD value named **CallFailureLoggingLevel** and set it to 1

Once DCOM debugging is enabled, more troubleshooting information will be written to the event log on the server.

## <span id="Latency_Testing"></span><span id="latency_testing"></span><span id="LATENCY_TESTING"></span>Latency Testing


At this time, latency testing is not supported with the robot API. You must use the specific latency hardware tools to perform latency testing.

## <span id="Flow_Control_and_Data_Validation"></span><span id="flow_control_and_data_validation"></span><span id="FLOW_CONTROL_AND_DATA_VALIDATION"></span>Flow Control and Data Validation


The robot or the robot controller is responsible for general flow control of the tests. This allows those building the robot to deal with all errors from the robot’s capabilities. The test itself will not be looking for any errors or return information from the robot. Similarly, the API will not validate that the robot is capable of performing actions. Any validation should be done by the robot or the robot controller.

 

 






