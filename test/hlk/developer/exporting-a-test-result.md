---
title: Exporting a Test Result
description: Exporting a Test Result
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6C809273-0594-4AD7-B481-80752CFEA085
---

# Exporting a Test Result


This sample shows how to export a test so that it can be run on a machine outside of the full HLK environment.

## <span id="C_"></span><span id="c_"></span>**C#**


``` syntax
//-----------------------------------------------------------------------
// <copyright file="ExportResultsSample.cs" company="Microsoft">
//    Copyright (c) Microsoft Corporation. All rights reserved.
// </copyright>
//-----------------------------------------------------------------------
[assembly: System.CLSCompliant(true)]

namespace Microsoft.Windows.Kits.Samples
{
    using System;
    using System.Collections.Generic;
    using System.Globalization;
    using System.IO;
    using System.Linq;
    using System.Reflection;
    using System.Xml;

    using Microsoft.Windows.Kits.Hardware.ObjectModel;
    using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;

    /// <summary>
    /// This sample uses the Machine Pool Growth feature to add and automatically redistribute tests to targets after 
    /// a test has been scheduled. 
    /// See the ShowUsage() method for setup details.
    /// </summary>
    static class ResultExportSample
    {
        static void ShowUsage()
        {
            Console.WriteLine("{0} <Project name> \"<Output directory name>\"", System.Reflection.Assembly.GetExecutingAssembly().GetName());
            Console.WriteLine("Before running this sample:");
            Console.WriteLine(" 1. Create a project and run several tests -- these should be single machine tests");
            Console.WriteLine(" 2. Run this tool on a system running HLK Studio, passing in the project name and the directory to output the standalone executable version of the test as parameters in that order");
        }

        /// <summary>
        /// Connects to the DBConnection HLK Manager.
        /// </summary>
        /// <returns></returns>
        static ProjectManager ConnectToLocalServer()
        {
            XmlDocument doc = new XmlDocument();
            doc.Load(Environment.ExpandEnvironmentVariables(@"%WTTSTDIO%\\connect.xml"));
            XmlNode root = doc.SelectSingleNode("/Connection");
            string controllerName = root.Attributes["Server"].Value;
            string databaseName = root.Attributes["Source"].Value;

            DatabaseProjectManager manager = new DatabaseProjectManager(controllerName, databaseName);
            Console.WriteLine("Connected to database {0} on controller {1}", databaseName, controllerName);

            return manager;
        }

        /// <summary>
        /// Main entry point.  
        /// </summary>
        /// <param name="args">
        /// The command line arguments for the application.  
        /// The first argument is the controller name to connect to.
        /// The second argument is the project to redistribute tests for newly added targets.
        /// </param>
        /// <exception cref="ArgumentException">Thrown if two arguments are not specified.</exception>
        static void Main(string[] args)
        {
            if (args.Length != 2)
            {
                ShowUsage();
                throw new ArgumentException("Incorrect number of arguments", "args");
            }

            try
            {
                string runningProject = args[0];
                string outputDirectory = args[1];

                if (!Directory.Exists(outputDirectory))
                {
                    Directory.CreateDirectory(outputDirectory);
                }

                // get a server name
                ProjectManager manager = ConnectToLocalServer();
                Project project = manager.GetProject(runningProject);

                // iterate through all tests in project
                foreach (Test test in project.GetTests())
                {
                    // iterate through test results in project
                    foreach (TestResult testResult in test.GetTestResults())
                    {
                        IRunExport exportable = testResult as IRunExport;

                        // either non-database test result or tagged as non-exportable
                        if (exportable == null || !exportable.CanExport)
                        {
                            Console.WriteLine("Test result for {0} is not exportable", test.Name);
                        }
                        else
                        {
                            // pre conditions satisifed, try exporting test to specified directory
                            try
                            {
                                Console.WriteLine("Exporting test {0}", test.Name);
                                exportable.Export(outputDirectory);
                                Console.WriteLine("Successfully exported test {0}", test.Name);
                                break;
                            }
                            catch (Exception exception)
                            {
                                Console.WriteLine("Failed to export test {0}:{1}{2}", test.Name, Environment.NewLine, exception);
                            }
                        }
                    }
                }
            }
            catch (Exception exception)
            {
                Console.WriteLine("Failed to export tests: {0}", exception);
            }
        }
    }
}       
        
```

## <span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>**PowerShell**


``` syntax
# ExportResults.ps1
# Usage:
#  powershell.exe (path)\ExportResults.ps1 [-projectName] <string> [-exportLocation] <string> [<CommonParameters>]

[CmdletBinding()]
Param
(
    [Parameter(Mandatory=$true)] 
    [System.String] $projectName, 
    [Parameter(Mandatory=$true)]
    [System.String] $exportLocation
)

# Load controller information
$connectFileName = $env:WTTSTDIO + "connect.xml"

Write-Host Opening connection file $connectFileName

$connectFile = [xml](Get-Content $connectFileName)
$controllerName = $connectFile.Connection.GetAttribute("Server")
$databaseName = $connectFile.Connection.GetAttribute("Source")

# Load object model assemblies
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "microsoft.windows.kits.hardware.sqmwrapper.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "microsoft.windows.kits.hardware.logging.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.dbconnection.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.submission.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.objectmodel.export.dll")
$ObjectModel = [Reflection.Assembly]::LoadFrom($env:WTTSTDIO + "Microsoft.Windows.Kits.Hardware.DiagnosticSummary.dll")

# create resolver for hlk assemblies so config section in exporter loads
$OnAssemblyResolve = [System.ResolveEventHandler]{
  param($sender, $resolveArgs)

  $file = [System.IO.Path]::Combine($env:wttstdio, $resolveArgs.Name + ".dll");

  if( [System.IO.File]::Exists($file))
  {
     try
     {
        return [Reflection.Assembly]::LoadFrom( $file);
     }
     catch
     {
        return $null;
     }
  }
   
  return $null;
}

# Add resolve handler
[System.AppDomain]::CurrentDomain.add_AssemblyResolve($OnAssemblyResolve)

# Connect to HLK controller
$manager =  new-object -typename Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection.DatabaseProjectManager -Args $controllerName, $databaseName

# Get the specified project 
$project = $manager.GetProject($projectName);

if($project -eq $null)
{
    Write-Host "Could not find project $projectName";
}
else
{
# create output directory if it doesn't exist
    if( -not (Test-Path $exportLocation) )
    {
        new-item -path $exportLocation -ItemType directory
    }

# Get all tests in the project - for each test get all test results that are exportable and call export
    $project.GetTests() | 
        %{$_.GetTestResults() | ?{ $_.CanExport} } | 
            %{ 
                try
                {
                    Write-Host
                    Write-Host "Exporting test '$($_.Test.Name)'"
                    $_.Export($exportLocation)
                    Write-host "Export Complete"
                }
                catch
                { 
                    Write-Host "Export Failed:"
                    Write-Host $_
                } 
            } 
}

[System.AppDomain]::CurrentDomain.remove_AssemblyResolve($OnAssemblyResolve)
```

 

 






