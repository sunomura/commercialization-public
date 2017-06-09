---
title: IEHardenAdmin
description: IEHardenAdmin
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: df9c52da-5493-4e79-b68c-c4f8de2d999a
ms.prod: W10
ms.mktglfcycl: deploy
ms.sitesec: msdn
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# IEHardenAdmin


`IEHardenAdmin` specifies whether Internet Explorer Enhanced Security Configuration (ESC) is enabled for all administrators on the computer. When Internet Explorer ESC is enabled, it reduces the exposure of your server to potential security attacks from Web pages that do not belong to the Local Intranet zone or the Trusted Sites zone.

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>true</strong></p></td>
<td><p>Specifies that ESC is enabled for all administrators on the computer. This is the default setting.</p></td>
</tr>
<tr class="even">
<td><p><strong>false</strong></p></td>
<td><p>Specifies that ESC is not enabled for all administrators on the computer.</p></td>
</tr>
</tbody>
</table>

 

## Valid Passes


specialize

## Parent Hierarchy


[Microsoft-Windows-IE-ESC](microsoft-windows-ie-esc.md) | **IEHardenAdmin**

## Applies To


For a list of the supported Windows editions and architectures that this component supports, see [Microsoft-Windows-IE-ESC](microsoft-windows-ie-esc.md).

## XML Example


The following XML output specifies that ESC is enabled for all administrators on the computer.

``` syntax
<IEHardenAdmin>true</IEHardenAdmin>
```

## Related topics


[LocalIntranetSites](microsoft-windows-ie-internetexplorer-localintranetsites.md)

[TrustedSites](microsoft-windows-ie-internetexplorer-trustedsites.md)

[Microsoft-Windows-IE-ESC](microsoft-windows-ie-esc.md)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_unattend\p_unattend%5D:%20IEHardenAdmin%20%20RELEASE:%20%2810/3/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




