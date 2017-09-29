---
title: ProductType
description: ProductType
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7B788FE7-591F-4CFB-9C1B-5F2C85564241
---

# ProductType


The **ProductType** object represents a type of product (for example, a printer or a scanner), and is a collection of **Feature** objects. For example, **ProductType** for a basic printer might require only the "device.prints" feature, but **ProductType** for a business printer might require "device.prints" and "device.prints-2-sided" features. ProductType is mostly used for reporting and categorizing a submission, and it has no bearing on test selection or other processing.

**ProductType** is determined at the product instance level. For example, if **ProductType** for a small business printer requires both "device.prints" and "device.scanner" features, a product instance that has one **Target** object of type printer and another **Target** object of type scanner is allowed

The product taxonomy is a means of categorizing product types into well-known groups and is provided by the Windows® Certification Program team.

 

 






