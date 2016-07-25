---
title: "Status Property Example (Recordset) (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e37b4d46-380d-4615-b4bb-e1a7b0851771
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
# Status Property Example (Recordset) (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property to display which records have been modified in a batch operation before a batch update has occurred.</para>
    <code>'BeginStatusRecordsetVB
Public Sub Main()
    On Error GoTo ErrorHandler

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

    ' connection and recordset variables
    Dim rstTitles As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLTitles As String
    
     ' open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
     ' open recordset for batch update
    Set rstTitles = New ADODB.Recordset
    strSQLTitles = "Titles"
    rstTitles.Open strSQLTitles, Cnxn, adOpenKeyset, adLockBatchOptimistic, adCmdTable
    
    ' change the type of psychology titles
    Do Until rstTitles.EOF
        If Trim(rstTitles!Type) = "psychology" Then rstTitles!Type = "self_help"
        rstTitles.MoveNext
    Loop
    
    ' display Title ID and status
    rstTitles.MoveFirst
    Do Until rstTitles.EOF
        If rstTitles.Status = adRecModified Then
            Debug.Print rstTitles!title_id &amp; " - Modified"
        Else
            Debug.Print rstTitles!title_id
        End If
    rstTitles.MoveNext
    Loop
   
    ' clean up
    rstTitles.Close
    Cnxn.Close
    Set rstTitles = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstTitles Is Nothing Then
        If rstTitles.State = adStateOpen Then
            ' Cancel the update because this is a demonstration
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
'EndStatusRecordsetVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status Property (ADO Recordset)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>