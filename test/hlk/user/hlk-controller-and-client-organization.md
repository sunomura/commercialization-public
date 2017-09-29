---
title: HLK Controller and Client Organization
description: HLK Controller and Client Organization
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 48D2FE29-B7D0-4E88-BDEE-067E2399066D
---

# HLK Controller and Client Organization


Before you install Windows HLK software in your lab, you should decide how you want to organize your lab's resources. Determine the number of controllers, the number of clients connecting to those controllers, and on which computer(s) to install Windows HLK Studio. These decisions are partly influenced by the type of devices and/or systems that you want to certify.

For example, to test specific devices, such as a USB-based flash-card reader, you might decide to allocate fewer controllers, each with more clients, because multiple testers can access the controllers, schedule jobs, and review job results, simultaneously.

>[!NOTE]
>  
This release of Windows HLK does not support enterprise scenarios, wherein controllers communicate directly with each other to share clients and distribute scheduled jobs. That is, Windows HLK does not support load-balancing.

 

Typically, there are two ways to organize your controller and client lab resources:

1.  Allocate fewer controllers, each with many clients connected to them.

    -   Advantages: You will have less overhead administering the controllers and clients. Also, the chances are higher for a client with the necessary hardware and software configuration to be available, or become available shortly, to execute a scheduled job.

    -   Disadvantages: Adds more latency to the Windows HLK controller. Windows HLK Studio menu items will be slower to respond and jobs slower to launch.

2.  Allocate more controllers, each with fewer clients connected to them.

    -   Advantages: Any given controller will be more responsive because it has fewer clients communicating with it. You can reduce overall latency.

    -   Disadvantages: Adds more latency to the Windows HLK controller. Windows HLK Studio menu items will be slower to respond and jobs slower to launch.

If you configure your controllers to run on high performance/high resource hardware, they will be able to handle more clients.

>[!NOTE]
>  
Multiple controllers are independent of each other.

 

Windows HLK puts a limit of 150 clients that can connect to a single controller. If you have a large lab that has more than 150 computers intended to be clients, you must allocate multiple controllers. Regardless of the size of your lab, you can allocate multiple controllers, each with any number of clients (up to 150 per controller) connected to a given controller.

>[!NOTE]
>  
Installing Windows HLK Studio does not count toward the limit of 150 clients per controller.

 

The following table describes example scenarios for labs of different sizes.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Number of computers</th>
<th>Minimum number of Windows HLK controllers to allocate</th>
<th>Number of Windows HLK clients to allocate</th>
<th>Configuration</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2 to 10</p></td>
<td><p>1</p></td>
<td><p>1 to 9</p></td>
<td><p>Allocate a single controller that will have 1 to 9 clients connected to it.</p>
<p>The remaining computers all become clients of the controller.</p></td>
</tr>
<tr class="even">
<td><p>11 to 151</p></td>
<td><p>1 or more</p></td>
<td><p>1 to 150</p></td>
<td><p>Allocate at least one controller, and possibly more.</p>
<p>For example, you can allocate one controller that can have up to 150 clients. Or, you can allocate two controllers and distribute the computers as their clients in an arbitrary manner.</p>
<p>The decision about the ratio in which to allocate clients to controllers is completely at your discretion.</p></td>
</tr>
<tr class="odd">
<td><p>152 or more</p></td>
<td><p>2 or more</p></td>
<td><p>150 or more</p></td>
<td><p>You must allocate at least two or more controllers for labs that contain more than 150 clients because this release of Windows HLK supports a maximum of 150 clients per controller.</p></td>
</tr>
</tbody>
</table>

>[!NOTE]
>  
To use Windows HLK to obtain certification, all tests must be performed from a single controller. You cannot combine results from multiple controllers to obtain certification.

 

 

 






