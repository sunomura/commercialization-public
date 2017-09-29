---
title: Filtering
description: Filtering
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f822f9ee-50f2-437b-8e70-485f9e718669
---

# Filtering


These code samples show how to apply filters to a project and retrieve filters from a project.

## <span id="C_"></span><span id="c_"></span>C#


``` syntax
// ------------------------------------------------------------------------------------------------
// <copyright file="Filtering.cs" company="Microsoft">
//   Copyright © Microsoft Corporation. All rights reserved.
// </copyright>
// ------------------------------------------------------------------------------------------------

[assembly: System.CLSCompliant(true)]

namespace Microsoft.Windows.Kits.Samples
{
    using System;
    using System.Collections.ObjectModel;

    using Microsoft.Windows.Kits.Hardware.FilterEngine;
    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;

    /// <summary>
    /// Sample for using a Target Family
    /// </summary>
    public class Filtering
    {
        /// <summary>
        /// Prevents a default instance of the <see cref="Filtering"/> class from being created. 
        /// </summary>
        private Filtering()
        { 
        }

        /// <summary>
        /// Entry point method for the sample application
        /// </summary>
        /// <param name="args">standard parameter arguments</param>
        public static void Main(string[] args)
        {
            /*
             * On-demand filtering. Using the filter engine API, apply filters to a project with failures (task results with Failed status).
             * For a project that doesn't have any failures, project.GetAppliedFilters() will return an empty collection.
             * For a project that was filtered, project.GetAppliedFilters() should return the filters that were applied to the project.
             */
            string controllerName = args[1];

            FilterLargeProject(controllerName);
            FilterSmallProject(controllerName);
        }

/// <summary>
/// Filters a small project
/// </summary>
/// <param name="controllerName">Controller name</param>
        private static void FilterSmallProject(string controllerName)
{
string projectName = "existing small project";
            // first we need to connect to the Server
            ProjectManager manager = new DatabaseProjectManager(controllerName);

            // load the project that has failing task results
            Project project = manager.GetProject(projectName);

            // instantiate filter engine for the database project manager
            DatabaseFilterEngine filterEngine = new DatabaseFilterEngine(manager);
            
            // apply filters to the project. Will try to find matching filters for the failing task results in the project.
            // It is synchronous (or blocking) call, and depending on the size of the log files and the number of task results to be filtered in the project, the Filter method could take a while.
            filterEngine.Filter(project);

            // retrieve the filters that were applied to the project.
            ReadOnlyCollection<IFilter> appliedFilters = project.GetAppliedFilters();
            Console.Out.WriteLine("{0} filters were applied for project {1}", appliedFilters.Count, projectName);
}

        /// <summary>
        /// Filters a large project with greater than 1000 test results
        /// </summary>
        /// <param name="controllerName">Controller name</param>
private static void FilterLargeProject(string controllerName)
{
string projectName = "existing large project";

            // first we need to connect to the Server
            ProjectManager manager = new DatabaseProjectManager(controllerName);

            // instantiate filter engine for the database project manager
            DatabaseFilterEngine filterEngine = new DatabaseFilterEngine(manager);
            
            // load the project that has failing task results
            Project project = manager.GetProject(projectName);
            foreach (ProductInstance productInstance in project.GetProductInstances())
            {
                foreach (TargetFamily targetFamily in productInstance.GetTargetFamilies())
                {
                    foreach (TestResult testResult in targetFamily.GetTestResults())
                    {
                        // apply filters to the test result. Will try to find matching filters for the failing task results in the project.
                        // It is synchronous (or blocking) call, and depending on the size of the log files and the number of task results to be filtered in the project, the Filter method could take a while.
                        filterEngine.Filter(testResult);
                    }
                }        
            }
}
    }
}
```

## <span id="Windows_PowerShell___Large_Project"></span><span id="windows_powershell___large_project"></span><span id="WINDOWS_POWERSHELL___LARGE_PROJECT"></span>Windows PowerShell – Large Project


``` syntax
# NOTE: Filters can be applied only to projects on the controller. Filtering against a project in a submission package is not supported.

# load object model dll's
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dll")
$DbConnection = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dbconnection.dll")
$Submission = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.submission.dll")
$FilterEngineDll = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.FilterEngine.dll")

write-host "Usage: %SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe -file Filtering.ps1 [ControllerMachineName] [ProjectName]"
write-host "\tNOTE: Filters can be applied only to projects on the controller. Filtering against a project in a submission package is not supported."

if ($args.count -ne 2)
{
   write-host "error: need to provide the controller name and name of the project to filter"
   return
}

$controllerName = $args[0]
$projectName = $args[1]

write-host "Connecting to the controller: $controllerName"
$Manager = new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection.DatabaseProjectManager -Args $controllerName, "HLKJobs"

#initialize filter engine for the database project manager
$filterEngine = new-object -typename Microsoft.Windows.Kits.Hardware.FilterEngine.DatabaseFilterEngine -Args $Manager;

# next, load the project that needs to be filtered
write-host "Opening project :$projectName"
$project = $Manager.GetProject($projectName)
if ($project -eq $null)
{
   write-host "unable to load project `n" $error.ToString()
}

foreach ($productInstance in $project.GetProductInstances())
{
   foreach ($targetFamily in $productInstance.GetTargetFamilies())
   {
      foreach ($testResult in $targetFamily.GetTestResults())
      {
#Reload the project in HLK Studio after running the script.
#apply filters to the test result. Will try to find matching filters for the failing task results in the project.
#It is synchronous (or blocking) call, and depending on the size of the log files and the number of task results to be filtered in the project, the Filter method could take a while.
# For very large projects, if you know the InstanceId for the testResult that you would like to filter, you can enumerate and find that testResult (by InstanceId) and apply filters only to that testResult.
         $result = $filterEngine.Filter($testResult)
      }
   }        
}
```

## <span id="Windows_PowerShell___Small_Project"></span><span id="windows_powershell___small_project"></span><span id="WINDOWS_POWERSHELL___SMALL_PROJECT"></span>Windows PowerShell – Small Project


``` syntax
# NOTE: Filters can be applied only to projects on the controller. Filtering against a project in a submission package is not supported.

# load object model dll's
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dll")
$DbConnection = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dbconnection.dll")
$Submission = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.submission.dll")
$FilterEngineDll = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.FilterEngine.dll")

write-host "Usage: %SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe -file Filtering.ps1 [ControllerMachineName] [ProjectName]"
write-host "NOTE: Filters can be applied only to projects on the controller. Filtering against a project in a submission package is not supported."

if ($args.count -ne 2)
{
   write-host "error: need to provide the controller name and name of the project to filter"
   return
}

$controllerName = $args[0]
$projectName = $args[1]

write-host "Connecting to the controller: $controllerName"
$Manager = new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection.DatabaseProjectManager -Args $controllerName, "HLKJobs"

#initialize filter engine for the database project manager
$filterEngine = new-object -typename Microsoft.Windows.Kits.Hardware.FilterEngine.DatabaseFilterEngine -Args $Manager;

# next, load the project that needs to be filtered
write-host "Opening project :$projectName"
$project = $Manager.GetProject($projectName)
if ($project -eq $null)
{
   write-host "unable to load project `n" $error.ToString()
}

# apply filter to the project. Reload the project in HLK Studio after running the script.
$result = $filterEngine.Filter($project)
```

 

 






