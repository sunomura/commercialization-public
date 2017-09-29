---
title: Working with Projects
description: Working with Projects
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 27db1630-98e7-4d77-aec1-65e894c2056e
---

# Working with Projects


This topic describes the classes that you use to work with projects.

## <span id="ProjectManager_Class"></span><span id="projectmanager_class"></span><span id="PROJECTMANAGER_CLASS"></span>ProjectManager Class


The **ProjectManager** class represents a connection to a server and provides access to all data. Other classes (for example, filters, instances of the **MachinePool** class, and instances of the **Requirement** class) can be accessed or enumerated through **ProjectManager**.

The **ProjectManager** class is abstract. To create a **ProjectManager** instance, you invoke a child class. Each instance is a connection to a specific data set.

One implementation of **ProjectManager** accesses a Windows Hardware Lab Kit (Windows HLK) controller computer. Another **ProjectManager** implementation accesses a submission package. In both cases, you use the same methods, and automation code that's written for one instance should work without modification for the other instance.

To connect to a Windows HLK controller, you can use this code:

``` syntax
using Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection;
ProjectManager manager = new DatabaseProjectManager(controllerName);
```

To connect to a submission package, you can use this code:

``` syntax
using Microsoft.Windows.Kits.Hardware.ObjectModel.Submission;
ProjectManager manager = new PackageProjectManager(pathToSubmissionPackage);
```

## <span id="Project_Class"></span><span id="project_class"></span><span id="PROJECT_CLASS"></span>Project Class


Each instance of the **Project** class represents a certification submission you send to Microsoft. It contains platform information like operating system, architecture, and edition. You use classes from the **Microsoft.Windows.Kits.Hardware.ObjectModel.Submission** namespace to combine projects from different systems into submissions.

You can create a project property (that is, a named value), set or update a project property, or delete a project property. You can't create duplicate property names.

You can create, rename, or delete a project. If you delete a project, all subordinate objects, including results, are deleted. You can't create duplicate project names.

## <span id="ProjectInfo_Class"></span><span id="projectinfo_class"></span><span id="PROJECTINFO_CLASS"></span>ProjectInfo Class


Each instance of the **Project** class has a collection of associated properties.

You can use the **ProjectInfo** class to include supplemental project information. (For example, you can create a "manufacturer" property). You can also set, update, or delete a **ProjectInfo** property. You can't create duplicate property names.

 

 






