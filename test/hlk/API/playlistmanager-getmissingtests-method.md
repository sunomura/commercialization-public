---
title: PlaylistManager.GetMissingTests Method
description: PlaylistManager.GetMissingTests Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: F0AB802F-02E9-4E19-8723-401570E44358
---

# PlaylistManager.GetMissingTests Method

>[!WARNING]
>  This method is being deprecated.

 

Uses the given [Playlist](playlist-class.md) to find tests for each [Target](target-class.md) in the current [PlaylistManager](playlistmanager-class.md)'s Project that should be present but are not.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public Dictionary<Target, List<PlaylistTest>> GetMissingTests (`

          `Playlist playlist`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*playlist*

 The [Playlist](playlist-class.md) for which missing tests will be found.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


*Dictionary&lt;Target, List&lt;PlaylistTest&gt;&gt;*

A dictionary containing a list of missing tests for each [Target](target-class.md) in the [PlaylistManager](playlistmanager-class.md)'s Project.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


Tests are determined to be missing if they have features that match the features of a Target, but the Test itself does not exist for the Target. This functionality should only be used in conjunction with official Playlist files for the Compat program.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






