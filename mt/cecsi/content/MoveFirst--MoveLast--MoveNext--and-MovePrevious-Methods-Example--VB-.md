---
title: "MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31d3b083-c677-423e-8d26-a212eaeea281
caps.latest.revision: 11
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
# MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveLast</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveNext</legacyLink>, and <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MovePrevious</legacyLink> methods to move the record pointer of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> based on the supplied command. The MoveAny procedure is required for this procedure to run.</para>
    <code>'BeginMoveFirstVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    ' connection and recordset variables
    Dim rstAuthors As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLAuthors
     ' record variables
    Dim strMessage As String
    Dim intCommand As Integer
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open recordset from Authors table
    Set rstAuthors = New ADODB.Recordset
    rstAuthors.CursorLocation = adUseClient
    ' Use client cursor to enable AbsolutePosition property
    strSQLAuthors = "Authors"
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenStatic, adLockReadOnly, adCmdTable
    
    ' Show current record information and get user's method choice
    Do
        strMessage = "Name: " &amp; rstAuthors!au_fname &amp; " " &amp; _
            rstAuthors!au_lname &amp; vbCr &amp; "Record " &amp; _
            rstAuthors.AbsolutePosition &amp; " of " &amp; _
            rstAuthors.RecordCount &amp; vbCr &amp; vbCr &amp; _
            "[1 - MoveFirst, 2 - MoveLast, " &amp; vbCr &amp; _
            "3 - MoveNext, 4 - MovePrevious]"
        intCommand = Val(Left(InputBox(strMessage), 1))
        
         ' for exiting the loop
        If intCommand &lt; 1 Or intCommand &gt; 4 Then
            MsgBox "You either entered a non-number or canceled the input box. Exit the application."
            Exit Do
        End If
        
        ' Use specified method while trapping for BOF and EOF
        Select Case intCommand
            Case 1
                rstAuthors.MoveFirst
            Case 2
                rstAuthors.MoveLast
            Case 3
                rstAuthors.MoveNext
                If rstAuthors.EOF Then
                    MsgBox "Already at end of recordset!"
                    rstAuthors.MoveLast
                End If
            Case 4
                rstAuthors.MovePrevious
                If rstAuthors.BOF Then
                    MsgBox "Already at beginning of recordset!"
                    rstAuthors.MoveFirst
                End If
        End Select
    Loop

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
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub

'EndMoveFirstVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>