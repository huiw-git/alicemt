---
title: "Resync Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab95315c-fe15-458c-9e0c-937ae5596592
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
# Resync Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates using the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method to refresh data in a static recordset.</para>
    <code>'BeginResyncVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection strings
    
Public Sub Main()
    On Error GoTo ErrorHandler

    'connection and recordset variables
    Dim Cnxn As ADODB.Connection
    Dim rstTitles As ADODB.Recordset
    Dim strCnxn As String
    Dim strSQLTitles As String
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open recordset using object refs to set properties
    ' that allow for updates to the database
    Set rstTitles = New ADODB.Recordset
    Set rstTitles.ActiveConnection = Cnxn
    rstTitles.CursorType = adOpenKeyset
    rstTitles.LockType = adLockOptimistic
    
    strSQLTitles = "titles"
    rstTitles.Open strSQLTitles
    
    'rstTitles.Open strSQLTitles, Cnxn, adOpenKeyset, adLockPessimistic, adCmdTable
    'the above line of code passes the same refs as the object refs listed above
    
    ' Change the type of the first title in the recordset
    rstTitles!Type = "database"
    
    ' Display the results of the change
    MsgBox "Before resync: " &amp; vbCr &amp; vbCr &amp; _
        "Title - " &amp; rstTitles!Title &amp; vbCr &amp; _
        "Type - " &amp; rstTitles!Type
    
    ' Resync with database and redisplay results
    rstTitles.Resync
    MsgBox "After resync: " &amp; vbCr &amp; vbCr &amp; _
        "Title - " &amp; rstTitles!Title &amp; vbCr &amp; _
        "Type - " &amp; rstTitles!Type

    ' clean up
    rstTitles.CancelBatch
    rstTitles.Close
    Cnxn.Close
    Set rstTitles = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstTitles Is Nothing Then
        If rstTitles.State = adStateOpen Then
            rstTitles.CancelBatch
            rstTitles.Close
        End If
    End If
    Set rstTitles = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndResyncVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>