---
title: DatabaseProjectManager Constructor (String, String)
description: DatabaseProjectManager Constructor (String, String)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d6e1ed66-21e8-47c5-87fc-217a6af2fa66
---

# DatabaseProjectManager Constructor (String, String)


This constructor initializes a new instance of the **DatabaseProjectManager** class. You should cast this back to the **ILogoManager** interface, this will prevent issues later when porting to a different implementation of this interface. The DataStore name is the NetBIOS name of the server parameter.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim server As String`

`Dim database As String`

`Dim instance As New DatabaseProjectManager(server, database)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New ( _`

          `server As String _`

          `database As String _`

`)`

**C#**

`public DatabaseProjectManager (`

          `string server`

          `string database`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*server*

     The name of the server to connect to.

*database*

     The name of the database to connect to.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown if *server* is **null** or empty, or if the database connection fails (for example, if the controller is unavailable).

 

 






