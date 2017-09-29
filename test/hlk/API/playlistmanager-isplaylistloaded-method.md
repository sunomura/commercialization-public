---
title: IsPlaylistLoaded Method
description: IsPlaylistLoaded Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1DAD0D03-EDEE-4F41-9429-258B5866D8FE
---

# IsPlaylistLoaded Method


\[Some information relates to pre-released product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.\]

Returns whether this **PlaylistManager**'s [Project](project-class.md) has a playlist applied.

It is recommended to call this method before calling [LoadPlaylist(string)](playlistmanager-loadplaylist-method--string-.md) or [UnloadPlaylist](playlistmanager-unloadplaylist-method.md).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public bool IsPlaylistLoaded()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


**true** if a playlist has been loaded. Otherwise, **false**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






