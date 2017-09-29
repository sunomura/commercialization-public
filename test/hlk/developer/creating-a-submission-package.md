---
title: Creating a Submission Package
description: Creating a Submission Package
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2d5271aa-1102-4ad8-940d-68f75bdfdbcf
---

# Creating a Submission Package

>[!NOTE]
>  We highly encourage you to include driver symbols as part of package creation. Including symbols enables Microsoft to triage and root cause issues related to your driver.

 

A submission package contains all of the results, logs, and data from a project. A submission package can also contain drivers, symbols, and supplemental material that are required for certification. The submission package can then be accessed through the same set of Certification Manager APIs.

The steps to create a submission package are:

1.  Create an instance of a **PackageWriter** class and specify the project to use.

2.  Add any necessary driver packages.

3.  Add any supplemental content.

4.  Set a notification callback (if desired) by using the **PackageWriter.SetProgressActionHandler()** method.

5.  Call the **PackageWriter.Save()** method, which saves all project and test information and logs to a compressed .wlkx package file. The **Save()** method also has an override to take an X.509 signing certificate as a parameter.

If you include a driver package, you specify a directory that contains all of the files and/or symbols in the **AddDriver()** method. Each driver package is associated with one or more targets in a project. From this mapping, Microsoft can identify which operating systems and architectures your driver has been tested against.

Each driver package has a list of locales (available with the **ProjectManager.GetLocaleList()** method). Every target and locale combination should have only one driver associated with it.

 

 






