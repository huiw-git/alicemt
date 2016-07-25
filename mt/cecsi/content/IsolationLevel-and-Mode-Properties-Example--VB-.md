---
title: "IsolationLevel and Mode Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3382fd41-0aa1-4091-97d3-624403111e07
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
# IsolationLevel and Mode Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> property to open an exclusive connection, and the <legacyLink xlink:href="ea84e4b2-fbf2-4eef-b9ce-796b22e21800">IsolationLevel</legacyLink> property to open a transaction that is conducted in isolation of other transactions.</para>
    <code>'BeginIsolationLevelVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    Dim Cnxn As ADODB.Connection
    Dim rstTitles As ADODB.Recordset
    Dim strCnxn As String
    Dim strSQLTitles As String
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Mode = adModeShareExclusive
    Cnxn.IsolationLevel = adXactIsolated
    Cnxn.Open strCnxn
    
     ' open Titles table
    Set rstTitles = New ADODB.Recordset
    strSQLTitles = "titles"
    rstTitles.Open strSQLTitles, Cnxn, adOpenDynamic, adLockPessimistic, adCmdTable
    
    Cnxn.BeginTrans
    
    ' Display connection mode
    If Cnxn.Mode = adModeShareExclusive Then
        MsgBox "Connection mode is exclusive."
    Else
        MsgBox "Connection mode is not exclusive."
    End If
    
    ' Display isolation level
    If Cnxn.IsolationLevel = adXactIsolated Then
        MsgBox "Transaction is isolated."
    Else
        MsgBox "Transaction is not isolated."
    End If
    
    ' Change the type of psychology titles
    Do Until rstTitles.EOF
        If Trim(rstTitles!Type) = "psychology" Then
            rstTitles!Type = "self_help"
            rstTitles.Update
        End If
        rstTitles.MoveNext
    Loop
    
    ' Print current data in recordset
    rstTitles.Requery
    Do While Not rstTitles.EOF
        Debug.Print rstTitles!Title &amp; " - " &amp; rstTitles!Type
        rstTitles.MoveNext
    Loop

    ' clean up
    rstTitles.Close
    Cnxn.RollbackTrans
    Cnxn.Close
    Set rstTitles = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstTitles Is Nothing Then
        If rstTitles.State = adStateOpen Then rstTitles.Close
    End If
    Set rstTitles = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then
            Cnxn.RollbackTrans
            Cnxn.Close
        End If
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndIsolationLevelVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="ea84e4b2-fbf2-4eef-b9ce-796b22e21800">IsolationLevel Property</link>
<link xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>