---
title: PlaylistManager.GetTestsFromProjectThatMatchPlaylist Method
description: PlaylistManager.GetTestsFromProjectThatMatchPlaylist Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 077455BC-7170-4692-B120-A57EBDFB9C0B
---

# PlaylistManager.GetTestsFromProjectThatMatchPlaylist Method


Retrieves the test from the current [PlaylistManager](playlistmanager-class.md)'s Project that match those in the Playlist.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

` public List<Test> GetTestsFromProjectThatMatchPlaylist (`

          `Playlist playlist`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*playlist*

Contains the list of tests that will be searched for in the Project

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


*List&lt;Test&gt;*

The list of tests from the current [PlaylistManager](playlistmanager-class.md)'s Project that match the tests in the [Playlist](playlist-class.md).

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


For a test to be retrieved from the [PlaylistManager](playlistmanager-class.md)'s Project, the same test must be present in the playlist and that test must have a matching Feature with a [Target](target-class.md) in the PlaylistManager's Project.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






