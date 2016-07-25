---
title: "BeginTrans, CommitTrans, and RollbackTrans Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa7de324-cd71-4bd0-8043-24229f4a785e
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
# BeginTrans, CommitTrans, and RollbackTrans Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example changes the book type of all psychology books in the <legacyBold><legacyItalic>Titles</legacyItalic></legacyBold> table of the database. After the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">BeginTrans</legacyLink> method starts a transaction that isolates all the changes made to the <legacyBold><legacyItalic>Titles</legacyItalic></legacyBold> table, the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">CommitTrans</legacyLink> method saves the changes. You can use the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">RollbackTrans</legacyLink> method to undo changes that you saved using the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method.</para>
    <code>'BeginBeginTransVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
    
Public Sub Main()
    On Error GoTo ErrorHandler

    'recordset and connection variables
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim rstTitles As ADODB.Recordset
    Dim strSQLTitles As String
    'record variables
    Dim strTitle As String
    Dim strMessage As String
    
    ' Open connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Set Cnxn = New ADODB.Connection
    Cnxn.Open strCnxn
    
    ' Open recordset dynamic to allow for changes
    Set rstTitles = New ADODB.Recordset
    strSQLTitles = "Titles"
    rstTitles.Open strSQLTitles, Cnxn, adOpenDynamic, adLockPessimistic, adCmdTable
    
    Cnxn.BeginTrans
    
    ' Loop through recordset and prompt user
    ' to change the type for a specified title
    
    rstTitles.MoveFirst
    
    Do Until rstTitles.EOF
        If Trim(rstTitles!Type) = "psychology" Then
            strTitle = rstTitles!Title
            strMessage = "Title: " &amp; strTitle &amp; vbCr &amp; _
            "Change type to self help?"

            ' If yes, change type for the specified title
            If MsgBox(strMessage, vbYesNo) = vbYes Then
                rstTitles!Type = "self_help"
                rstTitles.Update
            End If
        End If
    rstTitles.MoveNext
    Loop

    ' Prompt user to commit all changes made
    If MsgBox("Save all changes?", vbYesNo) = vbYes Then
        Cnxn.CommitTrans
    Else
        Cnxn.RollbackTrans
    End If

    ' Print recordset
    rstTitles.Requery
    rstTitles.MoveFirst
    Do While Not rstTitles.EOF
        Debug.Print rstTitles!Title &amp; " - " &amp; rstTitles!Type
        rstTitles.MoveNext
    Loop

    ' Restore original data as this is a demo
    rstTitles.MoveFirst
    
    Do Until rstTitles.EOF
        If Trim(rstTitles!Type) = "self_help" Then
            rstTitles!Type = "psychology"
            rstTitles.Update
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


'EndBeginTransVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">BeginTrans, CommitTrans, and RollbackTrans Methods</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>