---
title: PlaylistManager.DeserializePlaylist Method
description: PlaylistManager.DeserializePlaylist Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 62FA2592-8FE7-4743-B4B6-013243B23CAA
---

# PlaylistManager.DeserializePlaylist Method


Deserializes a playlist file into a [Playlist](playlist-class.md) object.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public static Playlist DeserializePlaylist (`

          `string playlistImportPath`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*playlistImportPath*

     Full path to the playlist file

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


*Playlist*

When the given Playlist file cannot be found a **System.IO.FileNotFoundException** is returned. When the given path is empty or has invalid characters, a **System.ArgumentException** is returned. When the given Playlist file does not conform to the schema, a [PlaylistException](playlistexception-class.md) is returned.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






