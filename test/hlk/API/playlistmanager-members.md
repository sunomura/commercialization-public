---
title: PlaylistManager Members
description: PlaylistManager Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: A6208465-2B62-4059-BFDD-977F4F8D0B9A
---

# PlaylistManager Members


The following tables list the members exposed by the [PlaylistManager Class](playlistmanager-class.md).

## <span id="Public_Constructor"></span><span id="public_constructor"></span><span id="PUBLIC_CONSTRUCTOR"></span>Public Constructor


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[PlaylistManager](playlistmanager-constructor.md)</p></td>
<td><p>Initializes a new instance of the [PlaylistManager Class](playlistmanager-class.md).)</p></td>
</tr>
</tbody>
</table>

 

## <span id="Public_Methods"></span><span id="public_methods"></span><span id="PUBLIC_METHODS"></span>Public Methods


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[CreatePlaylist](playlistmanager-createplaylist-method.md)</p></td>
<td><p>Creates a Playlist file from this [PlaylistManager](playlistmanager-class.md)'s Project instance.</p></td>
</tr>
<tr class="even">
<td><p>[DeserializePlaylist](playlistmanager-deserializeplaylist-method.md)</p></td>
<td><p>Deserializes a playlist file into a [Playlist](playlist-class.md) object.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[GetMissingTests](playlistmanager-getmissingtests-method.md)</p></td>
<td><p>Uses the given [Playlist](playlist-class.md) to find tests for each [Target](target-class.md) in the current [PlaylistManager](playlistmanager-class.md)'s Project that should be present but are not.</p>
<div class="alert">
<strong>Warning</strong>  This method is being deprecated.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>[GetTestsFromProjectThatMatchPlaylist](playlistmanager-gettestsfromprojectthatmatchplaylist-method.md)</p></td>
<td><p>Retrieves the test from the current [PlaylistManager](playlistmanager-class.md)'s Project that match those in the Playlist.</p></td>
</tr>
<tr class="odd">
<td><p>[GetTestsInProjectNotInPlaylist](playlistmanager-gettestsinprojectnotinplaylist-method.md)</p></td>
<td><p>Finds the tests that are in the [PlaylistManager](playlistmanager-class.md)'s Project but not in the given Playlist.</p>
<div class="alert">
<strong>Warning</strong>  This method is being deprecated.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>[IsPlaylistLoaded](playlistmanager-isplaylistloaded-method.md)</p></td>
<td><p>Returns whether this <strong>PlaylistManager</strong>'s [Project](project-class.md) has a playlist applied.</p></td>
</tr>
<tr class="even">
<td><p>[LoadPlaylist](playlistmanager-loadplaylist-method.md)</p></td>
<td><p>Loads the tests from a Playlist into this [PlaylistManager](playlistmanager-class.md)'s [Project](project-class.md).</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToString</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p>[UnloadPlaylist](playlistmanager-unloadplaylist-method.md)</p></td>
<td><p>Unloads the current playlist from this [Project](project-class.md).</p></td>
</tr>
</tbody>
</table>

 

## <span id="Protected_Methods"></span><span id="protected_methods"></span><span id="PROTECTED_METHODS"></span>Protected Methods


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Finalize</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p><strong>MemberwiseClone</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
</tbody>
</table>

 

 

 






