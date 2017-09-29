---
title: PlaylistManager.GetTestsInProjectNotInPlaylist Method
description: PlaylistManager.GetTestsInProjectNotInPlaylist Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0D1CE135-ED26-46D2-A8FA-BE80BEC56916
---

# PlaylistManager.GetTestsInProjectNotInPlaylist Method

>[!WARNING]
>  This method is being deprecated.

 

Finds the tests that are in the [PlaylistManager](playlistmanager-class.md)'s Project but not in the given Playlist.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

` public List<Test> GetTestsInProjectNotInPlaylist (`

          `string playlistPath`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*playlistPath*

Path to the playlist file.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


*List&lt;Test&gt;*

List of tests in the[PlaylistManager](playlistmanager-class.md)'s Project but not the Playlist.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






