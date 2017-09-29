---
title: Precision Touchpad Test Error Messages
description: Precision Touchpad Test Error Messages
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e36d3155-1284-4c7c-9ef3-058a0dbfeb9f
---

# Precision Touchpad Test Error Messages


**In this topic:**

-   [General error messages](#gen)

-   [HID-specific error messages](#hid)

## <span id="gen"></span><span id="GEN"></span>General error messages


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Error number</th>
<th>Message</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Explicitly failed by user</p></td>
<td><p>Operator failed the iteration/test by using a hotkey.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Failed too many iterations: #</p></td>
<td><p>Too many iterations failed. Includes the number of failed iterations.</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>Received input at an unexpected time</p></td>
<td><p>The test did not expect to receive data, but data was received.</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>Received too many contacts:#</p></td>
<td><p>Operator placed too many contacts down. Includes the number of detected contacts.</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>Received too few contacts:#</p></td>
<td><p>Operator placed too few contacts down. Includes the number of detected contacts.</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>Test didn't receive enough data</p></td>
<td><p>If the error occurs on contact lift, it indicates that the test required contacts to last a particular duration, but that duration was not met. If it occurs on contact down, the error indicates that the test received a zero-contact frame as the first data – this can be caused by a non-capacitive button press, but is more likely a protocol error (device sending an empty frame).</p></td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td><p>Received unexpected contact</p></td>
<td><p>On a test that requires a specific number of contacts, this error indicates that a contact came down after a contact went up. All contact-downs should occur before all contact-ups.</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p>Geometry data outside expected range:#</p></td>
<td><p>This error only occurs during the Geometry Reporting test. Width and/or height were outside the range expected by the test. Includes the detected width and height in himetric units.</p></td>
</tr>
<tr class="odd">
<td><p>11</p></td>
<td><p>Contact displacement too large:#</p></td>
<td><p>The contact’s overall X/Y displacement was too large. Includes the detected displacement in himetric units.</p></td>
</tr>
<tr class="even">
<td><p>12</p></td>
<td><p>Interaction too short:#</p></td>
<td><p>The interaction length (the time from first contact down to last contact up) was too short. Includes the detected interaction length in milliseconds.</p></td>
</tr>
<tr class="odd">
<td><p>13</p></td>
<td><p>Interaction too long:#</p></td>
<td><p>The interaction length (the time from first contact down to last contact up) was too long. Includes the detected interaction length in milliseconds.</p></td>
</tr>
<tr class="even">
<td><p>14</p></td>
<td><p>Packet too far from edge:#</p></td>
<td><p>Indicates that the first packet was too far from the edge of the touchpad. Includes the distance from the edge in himetric units.</p></td>
</tr>
<tr class="odd">
<td><p>15</p></td>
<td><p>Contact didn't move in straight line:#</p></td>
<td><p>The contact deviated too much from a line of best fit. Includes the maximum detected deviation from the line in himetric units.</p></td>
</tr>
<tr class="even">
<td><p>16</p></td>
<td><p>Line drifted off axis too much:#</p></td>
<td><p>This error only occurs during the Linearity tests. The contact’s displacement in either X or Y was too large. Includes the deviation in himetric units.</p></td>
</tr>
<tr class="odd">
<td><p>17</p></td>
<td><p>Not enough separation of points:#</p></td>
<td><p>This error only occurs during the Converge/Diverge tests. If converging, the beginning points were too close to each other. If diverging, the ending points were too close to each other. Includes the distance between points in himetric units.</p></td>
</tr>
<tr class="even">
<td><p>18</p></td>
<td><p>Too much separation of points:#</p></td>
<td><p>This error only occurs during the Converge/Diverge tests. If converging, the beginning points were too far from each other. If diverging, the ending points were too far from each other. Includes the distance between points in himetric units.</p></td>
</tr>
<tr class="odd">
<td><p>20</p></td>
<td><p>Positional delta too large:#</p></td>
<td><p>The position delta between two packets was too large for the test. Includes the detected delta in himetric units.</p></td>
</tr>
<tr class="even">
<td><p>23</p></td>
<td><p>Device doesn't support minimum number of contacts:#</p></td>
<td><p>The device doesn’t support the required minimum number of contacts. Includes the number of supported contacts.</p></td>
</tr>
<tr class="odd">
<td><p>24</p></td>
<td><p>Device supports too many contacts:#</p></td>
<td><p>The device supports more than the required maximum number of contacts. Includes the number of supported contacts.</p></td>
</tr>
<tr class="even">
<td><p>25</p></td>
<td><p>Packet not in expected position:#</p></td>
<td><p>This error only occurs during the Positional Accuracy test. Indicates that the packet’s location was not in the required position. Includes the packet’s location in himetric units.</p></td>
</tr>
<tr class="odd">
<td><p>26</p></td>
<td><p>No packets outside border region</p></td>
<td><p>On tests that involve drawing a straight line with the precision contact rig, this error indicates that the entire line was in the border region of the touchpad.</p></td>
</tr>
<tr class="even">
<td><p>27</p></td>
<td><p>Saw packet travel backwards</p></td>
<td><p>This error only occurs during the Linearity tests. Indicates that a packet was seen travelling backwards in relation to the rest of the packet stream.</p></td>
</tr>
<tr class="odd">
<td><p>28</p></td>
<td><p>Too low DPI:#</p></td>
<td><p>This error only occurs during the Input Resolution test. Indicates that the logical range of X/Y on the touchpad, combined with its physical dimensions, do not support the required DPI. Includes the calculated DPI.</p></td>
</tr>
<tr class="even">
<td><p>29</p></td>
<td><p>Saw confidence bit set after cleared</p></td>
<td><p>This error only occurs during the Confidence Reporting test. Indicates that a contact was seen setting the confidence bit after it had been cleared for that contact.</p></td>
</tr>
<tr class="odd">
<td><p>30</p></td>
<td><p>Confidence bit set too long:#</p></td>
<td><p>This error only occurs during the Confidence Reporting test. Indicates that the confidence bit was not cleared early enough in the contacts lifetime. Includes the length of time the confidence bit was set in milliseconds.</p></td>
</tr>
<tr class="even">
<td><p>31</p></td>
<td><p>Too low percent of logical coordinates found:#</p></td>
<td><p>This error only occurs during the Input Resolution test. The X or Y coordinate in packets received in a given iteration must include a minimum percent of the total range. Includes the percent actually found.</p></td>
</tr>
<tr class="odd">
<td><p>32</p></td>
<td><p>You must run this test elevated</p></td>
<td><p><strong>PTLogo.exe</strong> must be started from an elevated command prompt window for this test.</p></td>
</tr>
<tr class="even">
<td><p>33</p></td>
<td><p>Device does not support selective reporting</p></td>
<td><p>Device does not support selective reporting.</p></td>
</tr>
<tr class="odd">
<td><p>34</p></td>
<td><p>Duplicate packets:#</p></td>
<td><p>This error only occurs during the Linearity tests. Indicates that two consecutive packets had the same X/Y location, even though the contact was moving. Includes the scantime of the detected duplicate packet.</p></td>
</tr>
<tr class="even">
<td><p>35</p></td>
<td><p>Logical coordinate not found:#</p></td>
<td><p>This error only occurs during the Input Resolution test. Indicates that a required X or Y coordinate was never reported by any packet during the iteration. Includes the required coordinate in logical units.</p></td>
</tr>
<tr class="odd">
<td><p>36</p></td>
<td><p>Confidence always set</p></td>
<td><p>This error only occurs during the Confidence Reporting test. Indicates that the confidence bit was never cleared.</p></td>
</tr>
</tbody>
</table>

 

## <span id="hid"></span><span id="HID"></span>HID-specific error messages


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Error number</th>
<th>Message</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Invalid X bitsize</p></td>
<td><p>The bit count for Tx/Cx is outside the range [1,32]. Only checked if C is present.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Invalid Y bitsize</p></td>
<td><p>The bit count for Ty/Cy is outside the range [1,32]. Only checked if C is present.</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>Invalid packet transition</p></td>
<td><p>This can present itself with any of the following error messages:</p>
<ul>
<li><p><em>Last move location different</em></p>
<p>The coordinates of the tip switch clear report for a given contact are not the same as the coordinates of the last tip switch set report.</p></li>
<li><p><em>Missing tip-on</em></p>
<p>The first report didn't have the tip switch set, or there were two packets in a row without the tip switch set.</p></li>
<li><p><em>Missing tip</em></p>
<p>A contact present in the previous reported frame with the tip switch set was not found in the current frame.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>Invalid scan time</p></td>
<td><p>This can present itself with any of the following error messages:</p>
<ul>
<li><p><em>(Not present)</em></p>
<p>The device does not support the scan time usage in its descriptor.</p></li>
<li><p><em>(Range)</em></p>
<p>The scan time reported is outside the logical range.</p></li>
<li><p><em>(Delta &gt; 10ms more than 1% of the time)</em></p>
<p>The delta in scan time from frame to frame exceeds 10ms more than 1% of the time.</p></li>
<li><p><em>(Delta &gt; 16.7ms)</em></p>
<p>The delta in scan time from frame to frame was larger than 16.7ms.</p></li>
<li><p><em>(Duplicate)</em></p>
<p>The scan time was duplicated in two sequential frames.</p></li>
<li><p><em>(Differing values in frame)</em></p>
<p>The scan time value was not identical for all reported contacts of a given frame.</p></li>
<li><p><em>(Drifted from wall clock)</em></p>
<p>The deltas in scan time drifted too far from system time. &gt; 5% clock drift.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>Invalid XY</p></td>
<td><p>This can present itself with any of the following error messages:</p>
<ul>
<li><p><em>(Invalid T)</em></p>
<p>With C, Width, or Height present, Tx and/or Ty were not present or not within their logical range.</p></li>
<li><p><em>(Invalid C)</em></p>
<p>With T, Width, or Height present, Cx and/or Cy were not present or not within their logical range.</p></li>
<li><p><em>(Invalid T/C combo)</em></p>
<p>T was not contained within bounding box formed by C, Width, and Height.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p>Invalid width or height</p></td>
<td><p>This can present itself with any of the following error messages:</p>
<ul>
<li><p><em>&quot;&quot;</em></p>
<p>Width and/or height was present, and either one was not present, or one/both were outside their logical range.</p></li>
<li><p><em>(0)</em></p>
<p>Width and/or height were present, but the logical value for one/both was zero.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>8</p></td>
<td><p>Invalid contact ID</p></td>
<td><p>This can present itself with any of the following error messages:</p>
<ul>
<li><p><em>(Not present)</em></p>
<p>The device does not support the ContactID usage in its descriptor.</p></li>
<li><p><em>(Dupe in frame)</em></p>
<p>A contact ID was duplicated in a single frame (sometimes caused by an incomplete frame being reported).</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>14</p></td>
<td><p>No data in frame</p></td>
<td><p>There were no contacts in the frame, and the physical button is not down, but the physical button was not previously up.</p></td>
</tr>
<tr class="odd">
<td><p>16</p></td>
<td><p>Invalid # of contacts in frame</p></td>
<td><p>The number of contacts in the frame did not match the reported Actual Count.</p></td>
</tr>
<tr class="even">
<td><p>17</p></td>
<td><p>More than max contacts in frame</p></td>
<td><p>The number of contacts in the frame exceeded the maximum number of contacts the device supports per MAX COUNT.</p></td>
</tr>
<tr class="odd">
<td><p>18</p></td>
<td><p>Sampling rate out of range</p></td>
<td><p>The sampling rate was not in the allowed range for the number of contacts reported.</p></td>
</tr>
<tr class="even">
<td><p>21</p></td>
<td><p>Invalid actual count</p></td>
<td><p>The device does not support the ActualCount usage in its descriptor.</p></td>
</tr>
<tr class="odd">
<td><p>22</p></td>
<td><p>Invalid confidence</p></td>
<td><p>The confidence switch was not set (and the test was not the confidence test).</p></td>
</tr>
</tbody>
</table>

 

## <span id="related_topics"></span>Related topics


[Windows Precision Touchpad Device Validation Guide](windows-precision-touchpad-device-validation-guide.md)

 

 







