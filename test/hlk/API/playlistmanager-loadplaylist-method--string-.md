---
title: PlaylistManager.LoadPlaylist Method (string)
description: PlaylistManager.LoadPlaylist Method (string)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: C55EDC43-C257-4F16-8FB0-40F943ABA05F
---

# PlaylistManager.LoadPlaylist Method (string)


Loads the tests from a Playlist into this [PlaylistManager](playlistmanager-class.md)'s [Project](project-class.md).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public List<Guid> LoadPlaylist (`

          `string playlistPath`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*playlistPath*

Full path to Playlist file. The path does not have to be cleaned/validated before passing to this method.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


*List&lt;Guid&gt;*

Guids for tests that could not be added because they could not be found.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






