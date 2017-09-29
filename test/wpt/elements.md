---
title: Elements
description: Elements
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 93024039-529c-439f-9c91-f6174f4a91e7
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.author: sapaetsc
ms.date: 9/29/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Elements


The following represents the element hierarchy.

* <[WindowsPerformanceRecorder](windowsperformancerecorder.md)>
  * <[Profiles](profiles.md)>
    * <[SystemCollector](systemcollector.md)>
      * <[BufferSize](buffersize.md)>
      * <[Buffers](buffers.md)>
      * <[StackCaching](stackcaching.md)>
    * <[EventCollector](eventcollector.md)>
      * <[BufferSize](buffersize.md)>
      * <[Buffers](buffers.md)>
      * <[StackCaching](stackcaching.md)>
    * <[HeapEventCollector](heapeventcollector.md)>
      * <[BufferSize](buffersize.md)>
      * <[Buffers](buffers.md)>
      * <[StackCaching](stackcaching.md)>
    * <[SystemProvider](systemprovider.md)>
      * <[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)>
        * <[Keyword (in SystemProvider)](keyword--in-systemprovider-.md)>
        * <[CustomKeyword](customkeyword.md)>
      * <[Stacks](stacks.md)>
        * <[Stack](stack-wpa.md)>
      * <[PoolTags](pooltags.md)>
        * <[PoolTag](pooltag.md)>
    * <[EventProvider](eventprovider.md)>
      * <[Keywords (in EventProvider)](keywords--in-eventprovider-.md)>
        * <[Keyword (in EventProvider)](keyword--in-eventprovider-.md)>
      * <[CaptureStateOnStart](capturestateonstart.md)>
        * <[Keyword (in EventProvider)](keyword--in-eventprovider-.md)>
      * <[CaptureStateOnSave](capturestateonsave.md)>
        * <[Keyword (in EventProvider)](keyword--in-eventprovider-.md)>
    * <[HeapEventProvider](heapeventprovider.md)>
      * <[HeapProcessIds](heapprocessids.md)>
        * <[HeapProcessId](heapprocessid.md)>
    * <[Profile](profile-wpr.md)>
      * <[ProblemCategories](problemcategories.md)>
        * <[ProblemCategory](problemcategory.md)>
      * <[Collectors](collectors.md)>
        * <[SystemCollectorId](systemcollectorid.md)>
          * <[BufferSize](buffersize.md)>
          * <[Buffers](buffers.md)>
          * <[StackCaching](stackcaching.md)>
          * <[SystemProviderId](systemproviderid.md)>
            * <[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)>
              * <[Keyword (in SystemProvider)](keyword--in-systemprovider-.md)>
              * <[CustomKeyword](customkeyword.md)>
            * <[Stacks](stacks.md)>
              * <[Stack](stack-wpa.md)>
            * <[PoolTags](pooltags.md)>
              * <[PoolTag](pooltag.md)>
          * <[SystemProvider](systemprovider.md)>
            * <[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)>
              * <[Keyword (in SystemProvider)](keyword--in-systemprovider-.md)>
              * <[CustomKeyword](customkeyword.md)>
            * <[Stacks](stacks.md)>
              * <[Stack](stack-wpa.md)>
            * <[PoolTags](pooltags.md)>
              * <[PoolTag](pooltag.md)>
        * <[EventCollectorId](eventcollectorid.md)>
          * <[BufferSize](buffersize.md)>
          * <[Buffers](buffers.md)>
          * <[StackCaching](stackcaching.md)>
          * <[EventProviders](eventproviders.md)>
            * <[EventProviderId](eventproviderid.md)>
              * <[Keywords (in EventProvider)](keywords--in-eventprovider-.md)>
                * <[Keyword (in EventProvider)](keyword--in-eventprovider-.md)>
              * <[CaptureStateOnStart](capturestateonstart.md)>
                * <[Keyword (in EventProvider)](keyword--in-eventprovider-.md)>
              * <[CaptureStateOnSave](capturestateonsave.md)>
                * <[Keyword (in EventProvider)](keyword--in-eventprovider-.md)>
            * <[EventProvider](eventprovider.md)>
              * <[Keywords (in EventProvider)](keywords--in-eventprovider-.md)>
                * <[Keyword (in EventProvider)](keyword--in-eventprovider-.md)>
              * <[CaptureStateOnStart](capturestateonstart.md)>
                * <[Keyword (in EventProvider)](keyword--in-eventprovider-.md)>
              * <[CaptureStateOnSave](capturestateonsave.md)>
                * <[Keyword (in EventProvider)](keyword--in-eventprovider-.md)>
        * <[HeapEventCollectorId](heapeventcollectorid.md)>
          * <[BufferSize](buffersize.md)>
          * <[Buffers](buffers.md)>
          * <[StackCaching](stackcaching.md)>
          * <[HeapEventProviders](heapeventproviders.md)>
            * <[HeapEventProviderId](heapeventproviderid.md)>
              * <[HeapProcessIds](heapprocessids.md)>
                * <[HeapProcessId](heapprocessid.md)>
            * <[HeapEventProvider](heapeventprovider.md)>
              * <[HeapProcessIds](heapprocessids.md)>
                * <[HeapProcessId](heapprocessid.md)>
  * <[TraceMergeProperties](tracemergeproperties.md)>
    * <[TraceMergeProperty](tracemergeproperty.md)>
      * <[DeletePreMergedTraceFiles](deletepremergedtracefiles.md)>
      * <[CustomEvents](customevents.md)>
        * <[CustomEvent](customevent.md)>
      * <[FileCompression](filecompression.md)>
  * <[OnOffTransitionConfigurations](onofftransitionconfigurations.md)>
    * <[OnOffTransitionConfiguration](onofftransitionconfiguration.md)>
      * <[PrepareSystem](preparesystem.md)>
      * <[NumberOfRuns](numberofruns.md)>
      * <[PostBootDelay](postbootdelay.md)>
      * <[WakeupDelay](wakeupdelay.md)>
      * <[TransitionTag](transitiontag.md)>



This following section describes the elements that you can use to author recording profiles for Windows Performance Recorder (WPR).

## In This Section


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Buffers](buffers.md)</p></td>
<td><p>Describes either the number of buffers to be allocated when starting a session or the percentage of total memory that should be allocated for the session, depending on the value of the <strong>PercentageOfTotalMemory</strong> attribute.</p></td>
</tr>
<tr class="even">
<td><p>[BufferSize](buffersize.md)</p></td>
<td><p>Describes the size of each buffer, in KB.</p></td>
</tr>
<tr class="odd">
<td><p>[CaptureStateOnSave](capturestateonsave.md)</p></td>
<td><p>Represents a collection of keywords that describe the events to be captured when a trace is saved.</p></td>
</tr>
<tr class="even">
<td><p>[CaptureStateOnStart](capturestateonstart.md)</p></td>
<td><p>Represents a collection of keywords that describe the events to be captured at the start of a recording.</p></td>
</tr>
<tr class="odd">
<td><p>[Collectors](collectors.md)</p></td>
<td><p>Represents a collection of system collector identifiers, event collector identifiers, and optionally heap event collector identifiers.</p></td>
</tr>
<tr class="even">
<td><p>[CustomEvent](customevent.md)</p></td>
<td><p>Represents a custom event.</p></td>
</tr>
<tr class="odd">
<td><p>[CustomEvents](customevents.md)</p></td>
<td><p>Represents a collection of custom events.</p></td>
</tr>
<tr class="even">
<td><p>[CustomKeyword](customkeyword.md)</p></td>
<td><p>Represents a custom keyword for the profile.</p></td>
</tr>
<tr class="odd">
<td><p>[DeletePreMergedTraceFiles](deletepremergedtracefiles.md)</p></td>
<td><p>Indicates whether to deleted premerged event trace log (ETL) files.</p></td>
</tr>
<tr class="even">
<td><p>[EventCollector](eventcollector.md)</p></td>
<td><p>Represents an event collector for the profile.</p></td>
</tr>
<tr class="odd">
<td><p>[EventCollectorId](eventcollectorid.md)</p></td>
<td><p>Represents an event collector identifier for the profile.</p></td>
</tr>
<tr class="even">
<td><p>[EventProvider](eventprovider.md)</p></td>
<td><p>Configures the Event Tracing for Windows (ETW) user-mode provider.</p></td>
</tr>
<tr class="odd">
<td><p>[EventProviderId](eventproviderid.md)</p></td>
<td><p>Represents an event provider identifier for the profile.</p></td>
</tr>
<tr class="even">
<td><p>[EventProviders](eventproviders.md)</p></td>
<td><p>Represents a collection of event provider identifiers and event providers.</p></td>
</tr>
<tr class="odd">
<td><p>[FileCompression](filecompression.md)</p></td>
<td><p>Indicates whether to compress the ETL file.</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventCollector](heapeventcollector.md)</p></td>
<td><p>Represents a collector for heap events.</p></td>
</tr>
<tr class="odd">
<td><p>[HeapEventCollectorId](heapeventcollectorid.md)</p></td>
<td><p>Represents an identifier for a collector of heap events for the profile.</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventProvider](heapeventprovider.md)</p></td>
<td><p>Represents a provider of heap events for the profile.</p></td>
</tr>
<tr class="odd">
<td><p>[HeapEventProviderId](heapeventproviderid.md)</p></td>
<td><p>Represents an identifier for a provider of heap events.</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventProviders](heapeventproviders.md)</p></td>
<td><p>Represents a collection of heap event provider identifiers and heap event providers.</p></td>
</tr>
<tr class="odd">
<td><p>[HeapProcessId](heapprocessid.md)</p></td>
<td><p>Uniquely identifies a heap process.</p></td>
</tr>
<tr class="even">
<td><p>[HeapProcessIds](heapprocessids.md)</p></td>
<td><p>Represents a collection of heap process identifiers.</p></td>
</tr>
<tr class="odd">
<td><p>[Keyword (in EventProvider)](keyword--in-eventprovider-.md)</p></td>
<td><p>Describes the ETW keyword for a user-mode provider.</p></td>
</tr>
<tr class="even">
<td><p>[Keyword (in SystemProvider)](keyword--in-systemprovider-.md)</p></td>
<td><p>Describes the kernel flags that can be enabled for the kernel-mode session.</p></td>
</tr>
<tr class="odd">
<td><p>[Keywords (in EventProvider)](keywords--in-eventprovider-.md)</p></td>
<td><p>Represents a collection of event provider keywords.</p></td>
</tr>
<tr class="even">
<td><p>[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)</p></td>
<td><p>Represents a collection of system provider keywords.</p></td>
</tr>
<tr class="odd">
<td><p>[NumberOfRuns](numberofruns.md)</p></td>
<td><p>Indicates the number of times that an on/off transition is run.</p></td>
</tr>
<tr class="even">
<td><p>[OnOffTransitionConfiguration](onofftransitionconfiguration.md)</p></td>
<td><p>Represents an on/off transition configuration.</p></td>
</tr>
<tr class="odd">
<td><p>[OnOffTransitionConfigurations](onofftransitionconfigurations.md)</p></td>
<td><p>Represents a collection of on/off transition configurations.</p></td>
</tr>
<tr class="even">
<td><p>[PoolTag](pooltag.md)</p></td>
<td><p>Describes the pool tags to be enabled for analyzing pool pages.</p></td>
</tr>
<tr class="odd">
<td><p>[PoolTags](pooltags.md)</p></td>
<td><p>Represents a collection of a maximum of four pool tags.</p></td>
</tr>
<tr class="even">
<td><p>[PostBootDelay](postbootdelay.md)</p></td>
<td><p>Indicates whether the length of the delay, in seconds, after booting for an on/off transition.</p></td>
</tr>
<tr class="odd">
<td><p>[PrepareSystem](preparesystem.md)</p></td>
<td><p>Indicates whether to prepare the system for an on/off transition.</p></td>
</tr>
<tr class="even">
<td><p>[ProblemCategories](problemcategories.md)</p></td>
<td><p>Represents a collection of problem categories.</p></td>
</tr>
<tr class="odd">
<td><p>[ProblemCategory](problemcategory.md)</p></td>
<td><p>Represents a problem category for the profile.</p></td>
</tr>
<tr class="even">
<td><p>[Profile](profile-wpr.md)</p></td>
<td><p>Represents a collection of problem categories and collectors.</p></td>
</tr>
<tr class="odd">
<td><p>[Profiles](profiles.md)</p></td>
<td><p>Represents a collection of collectors, providers, and profiles.</p></td>
</tr>
<tr class="even">
<td><p>[Stack](stack-wpa.md)</p></td>
<td><p>Describes the kernel events on which stacks are to be enabled.</p></td>
</tr>
<tr class="odd">
<td><p>[StackCaching](stackcaching.md)</p></td>
<td><p>Describes stack caching attributes of collectors.</p></td>
</tr>
<tr class="even">
<td><p>[Stacks](stacks.md)</p></td>
<td><p>Represents a collection of stacks.</p></td>
</tr>
<tr class="odd">
<td><p>[SystemCollector](systemcollector.md)</p></td>
<td><p>Describes the configurations to enable the Event Tracing for Windows (ETW) kernel-mode session.</p></td>
</tr>
<tr class="even">
<td><p>[SystemCollectorId](systemcollectorid.md)</p></td>
<td><p>Represents the identifier of a system collector.</p></td>
</tr>
<tr class="odd">
<td><p>[SystemProvider](systemprovider.md)</p></td>
<td><p>Describes the configuration to enable the kernel-mode provider.</p></td>
</tr>
<tr class="even">
<td><p>[SystemProviderId](systemproviderid.md)</p></td>
<td><p>Uniquely identifies the system provider.</p></td>
</tr>
<tr class="odd">
<td><p>[TraceMergeProperties](tracemergeproperties.md)</p></td>
<td><p>Represents a collection of trace merge properties.</p></td>
</tr>
<tr class="even">
<td><p>[TraceMergeProperty](tracemergeproperty.md)</p></td>
<td><p>Contains configurations that are applied when recordings from multiple profiles are merged.</p></td>
</tr>
<tr class="odd">
<td><p>[TransitionTag](transitiontag.md)</p></td>
<td><p>Indicates the transition tag for an [OnOffTransitionConfiguration](onofftransitionconfiguration.md) element.</p></td>
</tr>
<tr class="even">
<td><p>[WakeupDelay](wakeupdelay.md)</p></td>
<td><p>Indicates the delay, in seconds, when emerging from a sleep state for an [OnOffTransitionConfiguration](onofftransitionconfiguration.md) element.</p></td>
</tr>
<tr class="odd">
<td><p>[WindowsPerformanceRecorder](windowsperformancerecorder.md)</p></td>
<td><p>Represents metadata about the authoring of profiles.</p></td>
</tr>
</tbody>
</table>

 

## Related topics


[Recording Profile XML Reference](recording-profile-xml-reference.md)

 

 







