---
title: "UpdateBatch and CancelBatch Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 41625f6f-e12d-4d8d-9f60-0729ce64c31e
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
# UpdateBatch and CancelBatch Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method in conjunction with the <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> method.</para>
    <code>'BeginUpdateBatchVB
Public Sub Main()
    On Error GoTo ErrorHandler

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

    'connection and recordset variables
    Dim rstTitles As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLTitles As String
     'record variables
    Dim strTitle As String
    Dim strMessage As String
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
     ' open recordset for batch uodate
    Set rstTitles = New ADODB.Recordset
    strSQLTitles = "titles"
    rstTitles.Open strSQLTitles, Cnxn, adOpenKeyset, adLockBatchOptimistic, adCmdTable
    
    rstTitles.MoveFirst
    ' Loop through recordset and ask user if she wants
    ' to change the type for a specified title.
    Do Until rstTitles.EOF
        If Trim(rstTitles!Type) = "psychology" Then
            strTitle = rstTitles!Title
            strMessage = "Title: " &amp; strTitle &amp; vbCr &amp; _
               "Change type to self help?"
            
            If MsgBox(strMessage, vbYesNo) = vbYes Then
                rstTitles!Type = "self_help"
            End If
        End If
    
        rstTitles.MoveNext
    Loop
    
    ' Ask the user if she wants to commit to all the
    ' changes made above.
    If MsgBox("Save all changes?", vbYesNo) = vbYes Then
        rstTitles.UpdateBatch
    Else
        rstTitles.CancelBatch
    End If
    
    ' Print current data in recordset.
    rstTitles.Requery
    rstTitles.MoveFirst
    Do While Not rstTitles.EOF
        Debug.Print rstTitles!Title &amp; " - " &amp; rstTitles!Type
        rstTitles.MoveNext
    Loop
    
    ' Restore original values because this is a demonstration.
    rstTitles.MoveFirst
    Do Until rstTitles.EOF
        If Trim(rstTitles!Type) = "self_help" Then
            rstTitles!Type = "psychology"
        End If
        rstTitles.MoveNext
    Loop
    rstTitles.UpdateBatch

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
'EndUpdateBatchVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch Method</link>
<link xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>