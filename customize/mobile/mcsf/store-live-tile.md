---
title: Store live tile
description: The Store tile, when medium-sized, becomes a live tile.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 37a4827d-190c-40f1-acf7-9523af758b8c
ms.author: alhopper
ms.date: 05/02/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# Store live tile


The Store tile, when medium-sized, becomes a live tile. It shows both the Microsoft Store logo and the name. The Microsoft Store live tile cycles through apps that the user will see in the Store and lets the user discover apps outside of the Store. By default, the Store live tile is on and out-of-the-box, the live tile is only updated over Wi-Fi until the user enters the Store for the first time. After the user enters the Store, the OS will start using cellular data to update the Store live tile in the background.

Microsoft recommends that partners keep the default Store live tile behavior. However, partners may change the default behavior to turn off the Store live tile and to prevent the OS from using cellular data to update the Store live tile in the background.

Regardless of the default Store live tile settings, users have the option of changing the defaults by choosing the **Live Tile** settings in the Microsoft Store **Settings** screen.



<a href="" id="constraints---imagetimeonly"></a>**Constraints:** ImageTimeOnly  

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample or use the sample StoreLiveTile.xml file.

    ```
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="StoreLiveTile"  
                         Description="Use to configure the Store tile in the Start screen."  
                         Owner=""  
                         OwnerType="OEM"> 
      
      <Static>  

        <Settings Path="StoreMoOemGroup">  
          <Setting Name="OemMoCustomizedIsLiveTileEnabled" Value="" /> 
          <Setting Name="OemMoLiveTileOptInToCellularAfterStoreLaunch" Value="" /> 
       </Settings>  

      </Static>

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  To set the default value for **Live Tile** **Show products on tile** option in the Microsoft Store **Settings** screen, set `OemMoCustomizedIsLiveTileEnabled` to one of the following values:

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Value</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>0 or 'Disabled'</p></td>
    <td><p>Disables the live tile feature for the Store tile. The <strong>Show products on tile</strong> option is Off.</p></td>
    </tr>
    <tr class="even">
    <td><p>1 or 'Enabled'</p></td>
    <td><p>Enables the live tile feature for the Store tile. The <strong>Show products on tile</strong> option is On.</p>
    <p>This is the default OS value.</p></td>
    </tr>
    </tbody>
    </table>

     

4.  To set the default value for **Live Tile** **Only update the tile when I'm on Wi-Fi** option in the Microsoft Store **Settings** screen, set `OemMoLiveTileOptInToCellularAfterStoreLaunch` to one of the following values:

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Value</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>0 or 'Disabled'</p></td>
    <td><p>Prevents the OS from using cellular data to update the Store live tile after the user enters the Store for the first time. The <strong>Only update the tile when I'm on Wi-Fi</strong> option is On.</p>
    <p>Although the feature does not use a lot of data, partners may want to disable live tile updates over cellular data to meet certain market requirements.</p></td>
    </tr>
    <tr class="even">
    <td><p>1 or 'Enabled'</p></td>
    <td><p>Allows the OS to use cellular data to update the Store live tile in the background after the user enters the Store for the first time. The <strong>Only update the tile when I'm on Wi-Fi</strong> option is Off.</p>
    <p>This is the default OS value.</p></td>
    </tr>
    </tbody>
    </table>

     

<a href="" id="testing-steps-"></a>**Testing steps:**  
1.  Flash a build containing this customization to a phone.

2.  Verify that the Store live tile is medium-sized and pinned to the Start screen.

3.  Go to the **Settings** screen in the Microsoft Store app, and check the default values for the following **Live Tile** options: **Show products on tile** and **Only update the tile when I'm on Wi-Fi**. Confirm that they match the default values that you set.

 

 






