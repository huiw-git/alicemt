---
title: "Delete Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c80e71b-9e3f-4d05-ab2a-9e78798dad88
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
# Delete Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink> method to remove a specified record from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
    <code>'BeginDeleteVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    Dim rstRoySched As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLRoySched As String
    
    Dim strMsg As String
    Dim strTitleID As String
    Dim intLoRange As Integer
    Dim intHiRange As Integer
    Dim intRoyalty As Integer
    
     ' open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' open RoySched table with cursor client-side
    Set rstRoySched = New ADODB.Recordset
    rstRoySched.CursorLocation = adUseClient
    rstRoySched.CursorType = adOpenStatic
    rstRoySched.LockType = adLockBatchOptimistic
    rstRoySched.Open "SELECT * FROM roysched WHERE royalty = 20", strCnxn, , , adCmdText
    
    ' Prompt for a record to delete
    strMsg = "Before delete there are " &amp; rstRoySched.RecordCount &amp; _
       " titles with 20 percent royalty:" &amp; vbCr &amp; vbCr
    
    Do While Not rstRoySched.EOF
       strMsg = strMsg &amp; rstRoySched!title_id &amp; vbCr
       rstRoySched.MoveNext
    Loop
    
    strMsg = strMsg &amp; vbCr &amp; vbCr &amp; "Enter the ID of a record to delete:"
    strTitleID = UCase(InputBox(strMsg))
    
    If strTitleID = "" Then
        Err.Raise 1, , "You didn't enter any value for the record ID."
    End If
    
    ' Move to the record and save data so it can be restored
    rstRoySched.Filter = "title_id = '" &amp; strTitleID &amp; "'"
    
    If rstRoySched.RecordCount &lt; 1 Then
        Err.Raise 1, , "There is no record for the record ID you entered."
    End If
    
    intLoRange = rstRoySched!lorange
    intHiRange = rstRoySched!hirange
    intRoyalty = rstRoySched!royalty
    
    ' Delete the record
    rstRoySched.Delete
    rstRoySched.UpdateBatch
    
    ' Show the results
    rstRoySched.Filter = adFilterNone
    rstRoySched.Requery
    strMsg = ""
    strMsg = "After delete there are " &amp; rstRoySched.RecordCount &amp; _
       " titles with 20 percent royalty:" &amp; vbCr &amp; vbCr
    Do While Not rstRoySched.EOF
        strMsg = strMsg &amp; rstRoySched!title_id &amp; vbCr
        rstRoySched.MoveNext
    Loop
    MsgBox strMsg
    
    ' Restore the data because this is a demonstration
    rstRoySched.AddNew
    rstRoySched!title_id = strTitleID
    rstRoySched!lorange = intLoRange
    rstRoySched!hirange = intHiRange
    rstRoySched!royalty = intRoyalty
    rstRoySched.UpdateBatch

    ' clean up
    rstRoySched.Close
    Set rstRoySched = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstRoySched Is Nothing Then
        If rstRoySched.State = adStateOpen Then rstRoySched.Close
    End If
    Set rstRoySched = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndDeleteVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete Method (ADO Recordset)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>