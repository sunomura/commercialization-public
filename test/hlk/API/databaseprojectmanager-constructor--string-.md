---
title: DatabaseProjectManager Constructor (String)
description: DatabaseProjectManager Constructor (String)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b1b1351c-bfd2-46ff-a1b4-c832099aee5e
---

# DatabaseProjectManager Constructor (String)


This constructor initializes a new instance of the **DatabaseProjectManager** class. You should cast this back to the **ILogoManager** interface, this will prevent issues later when porting to a different implementation of this interface. The DataStore name is the NetBIOS name of the server parameter.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection (in Microsoft.Windows.Kits.Hardware.ObjectModel.DBConnection)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim server As String`

`Dim instance As New DatabaseProjectManager(server)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New ( _`

          `server As String _`

`)`

**C#**

`public DatabaseProjectManager (`

          `string server`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*server*

     The name of the server to connect to.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


An exception is thrown if *server* is **null** or empty, or if the database connection fails (for example, if the controller is unavailable).

 

 






