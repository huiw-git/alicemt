---
title: "OriginalValue and UnderlyingValue Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1750804b-d7ef-47d6-8d73-1f51fa1cbe4a
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
# OriginalValue and UnderlyingValue Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue</legacyLink> and <legacyLink xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue</legacyLink> properties by displaying a message if a record's underlying data has changed during a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> batch update.</para>
    <code>'BeginOriginalValueVB
Public Sub Main()
    On Error GoTo ErrorHandler

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

    Dim Cnxn As ADODB.Connection
    Dim rstTitles As ADODB.Recordset
    Dim fldType As ADODB.Field
    Dim strCnxn As String
    Dim strSQLTitles As String
    
    ' Open connection.
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open recordset for batch update
    ' using object refs to set properties
    Set rstTitles = New ADODB.Recordset
    Set rstTitles.ActiveConnection = Cnxn
    rstTitles.CursorType = adOpenKeyset
    rstTitles.LockType = adLockBatchOptimistic
    strSQLTitles = "titles"
    rstTitles.Open strSQLTitles
    
    ' Set field object variable for Type field
    Set fldType = rstTitles!Type
    
    ' Change the type of psychology titles
    Do Until rstTitles.EOF
        If Trim(fldType) = "psychology" Then
            fldType = "self_help"
        End If
        rstTitles.MoveNext
    Loop
    
    ' Similate a change by another user by updating
    ' data using a command string
    Cnxn.Execute "UPDATE Titles SET type = 'sociology' " &amp; _
       "WHERE type = 'psychology'"
    
    'Check for changes
    rstTitles.MoveFirst
    Do Until rstTitles.EOF
        If fldType.OriginalValue &lt;&gt; fldType.UnderlyingValue Then
            MsgBox "Data has changed!" &amp; vbCr &amp; vbCr &amp; _
                "  Title ID: " &amp; rstTitles!title_id &amp; vbCr &amp; _
                "  Current value: " &amp; fldType &amp; vbCr &amp; _
                "  Original value: " &amp; _
                fldType.OriginalValue &amp; vbCr &amp; _
                "  Underlying value: " &amp; _
                fldType.UnderlyingValue &amp; vbCr
        End If
    rstTitles.MoveNext
    Loop
    
    ' Cancel the update because this is a demonstration
    rstTitles.CancelBatch
    
    ' Restore original values
    Cnxn.Execute "UPDATE Titles SET type = 'psychology' " &amp; _
        "WHERE type = 'sociology'"
   
    ' clean up
    rstTitles.Close
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
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndOriginalValueVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>