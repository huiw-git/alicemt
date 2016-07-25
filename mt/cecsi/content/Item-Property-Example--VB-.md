---
title: "Item Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4476603-691b-4081-8797-a3d0b331dce5
caps.latest.revision: 9
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Item Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property accesses members of a collection. The example opens the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table of the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database with a parameterized command.</para>
    <para>The parameter in the command issued against the database is accessed from the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object's <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection by index and name. The fields of the returned <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> are then accessed from that object's <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection by index and name.</para>
    <code>'BeginItemVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    Dim Cnxn As ADODB.Connection
    Dim rstAuthors As ADODB.Recordset
    Dim cmd As ADODB.Command
    Dim prm As ADODB.Parameter
    Dim fld As ADODB.Field
    Dim strCnxn As String
    
    Dim ix As Integer
    Dim limit As Long
    Dim Column(0 To 8) As Variant
    
    Set Cnxn = New ADODB.Connection
    Set rstAuthors = New ADODB.Recordset
    Set cmd = New ADODB.Command
    
    'Set the array with the Authors table field (column) names
    Column(0) = "au_id"
    Column(1) = "au_lname"
    Column(2) = "au_fname"
    Column(3) = "phone"
    Column(4) = "address"
    Column(5) = "city"
    Column(6) = "state"
    Column(7) = "zip"
    Column(8) = "contract"
    
    cmd.CommandText = "SELECT * FROM Authors WHERE state = ?"
    Set prm = cmd.CreateParameter("ItemXparm", adChar, adParamInput, 2, "CA")
    cmd.Parameters.Append prm
     ' set connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    cmd.ActiveConnection = Cnxn
     ' open recordset
    rstAuthors.Open cmd, , adOpenStatic, adLockReadOnly
    'Connection and CommandType are omitted because
    'a Command object is provided
    
    Debug.Print "The Parameters collection accessed by index..."
    Set prm = cmd.Parameters.Item(0)
    Debug.Print "Parameter name = '"; prm.Name; "', value = '"; prm.Value; "'"
    Debug.Print
    
    Debug.Print "The Parameters collection accessed by name..."
    Set prm = cmd.Parameters.Item("ItemXparm")
    Debug.Print "Parameter name = '"; prm.Name; "', value = '"; prm.Value; "'"
    Debug.Print
    
    Debug.Print "The Fields collection accessed by index..."
    
    rstAuthors.MoveFirst
    limit = rstAuthors.Fields.Count - 1
    For ix = 0 To limit
       Set fld = rstAuthors.Fields.Item(ix)
       Debug.Print "Field "; ix; ": Name = '"; fld.Name; _
                   "', Value = '"; fld.Value; "'"
    Next ix
    
    Debug.Print
    
    Debug.Print "The Fields collection accessed by name..."
    
    rstAuthors.MoveFirst
    For ix = 0 To 8
       Set fld = rstAuthors.Fields.Item(Column(ix))
       Debug.Print "Field name = '"; fld.Name; "', Value = '"; fld.Value; "'"
    Next ix
    
    ' clean up
    rstAuthors.Close
    Cnxn.Close
    Set rstAuthors = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstAuthors Is Nothing Then
        If rstAuthors.State = adStateOpen Then rstAuthors.Close
    End If
    Set rstAuthors = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    Set cmd = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
'EndItemVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item Property</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>