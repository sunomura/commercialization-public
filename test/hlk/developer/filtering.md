---
title: Filtering
description: Filtering
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f3ff1ef1-894b-4836-b8f3-2b17e994193a
---

# Filtering


Filtering is post-processing of failed task results that match predefined filter criteria and override "fail" task result status to "pass". You can then submit a package for certification for various targets.

A filter represents a set of constraints that you can use to reduce a set of task results. When a task result fails, the log nodes in the selected filters are matched against the task result logs. The fail/pass count for the task results are adjusted based on the number of test cases that are filtered in the log.

A filter is uniquely identified by its filter number and version. Filter status and expiration date indicate whether a filter is active or expired. The title gives a brief description about the filter. Issue description and resolution give more details about the issue and its resolution.

These are the types of filters:

-   Errata, for handling test failures that are due to bugs in test content, operating system, or Windows Hardware Lab Kit (Windows HLK) infrastructure.

-   Contingency, to grant exceptions for specific hardware failures.

-   Auto triage, for troubleshooting the causes of failures. Unlike the errata and contingency filters, the auto triage filters don't change the task results from fail to pass.

## <span id="Applying_Filters"></span><span id="applying_filters"></span><span id="APPLYING_FILTERS"></span>Applying Filters


You can apply filters to a project that has failed task results. Before you apply a filter, make sure that you have updated the controller with the latest filters from Windows Quality Online Services (Winqual). If there are matching filters on the controller for a failed task result, the task result is filtered. However, a task result can be partially filtered (that is, the number of filtered failures is less than the total number of failures in the task result).

``` syntax
string projectName = "existing project";
string controllerName = args[1];

// first, connect to the server
ProjectManager manager = new DatabaseProjectManager(controllerName);

// load the project that has failing task results
Project project = manager.GetProject(projectName);

// instantiate the filter engine for the database project manager
DatabaseFilterEngine filterEngine = new DatabaseFilterEngine(manager);
            
// apply filters to the project; will try to find matching filters for 
// the failing task results in the project
// it's a synchronous (or blocking) call, and depending on the size of 
// the log files and the number of task results to be filtered in the 
// project, the Filter method might take a while
filterEngine.Filter(project);

// retrieve the filters that were applied to the project
ReadOnlyCollection<IFilter> appliedFilters = project.GetAppliedFilters();
Console.Out.WriteLine("{0} filters were applied for project {1}", 
 appliedFilters.Count, projectName);
```

## <span id="Downloading_the_latest_filters"></span><span id="downloading_the_latest_filters"></span><span id="DOWNLOADING_THE_LATEST_FILTERS"></span>Downloading the latest filters


You can download the latest filters from the following location:

-   [Windows Hardware Lab Kit Filters](..\user\windows-hardware-lab-kit-filters.md)

 

 






