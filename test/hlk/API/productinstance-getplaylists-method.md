---
title: GetPlaylists Method
description: GetPlaylists Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 761EAC78-F6D2-49CE-A8A1-5671BA5A2DD0
---

# GetPlaylists Method


Gets the applied playlists for this [ProductInstance](productinstance-class.md).

For **ProductInstance** objects connected to an HLK Controller database, there will be only one Playlist. When connected to a **ProductInstance** from a package, there may be multiple due to merging.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public abstract ReadOnlyCollection<PlaylistInfo> GetPlaylists();`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **ReadOnlyCollection&lt;PlaylistInfo&gt;**, which is a read-only list of playlist info objects.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






