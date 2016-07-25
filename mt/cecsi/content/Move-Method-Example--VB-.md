---
title: "Move Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 55eb797a-0205-40d2-a797-55b216d1d3bb
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
# Move Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink> method to position the record pointer based on user input.</para>
    <code>'BeginMoveVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    ' connection and recordset variables
    Dim rstAuthors As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLAuthors As String
     ' record variables
    Dim varBookmark As Variant
    Dim strCommand As String
    Dim lngMove As Long
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open recordset from Authors table
    Set rstAuthors = New ADODB.Recordset
    rstAuthors.CursorLocation = adUseClient
    ' Use client cursor to allow use of AbsolutePosition property
    strSQLAuthors = "SELECT au_id, au_fname, au_lname, city, state FROM Authors ORDER BY au_lname"
    rstAuthors.Open strSQLAuthors, strCnxn, adOpenStatic, adLockOptimistic, adCmdText
       
    rstAuthors.MoveFirst

    Do
        ' Display information about current record and
        ' ask how many records to move
        
        strCommand = InputBox( _
            "Record " &amp; rstAuthors.AbsolutePosition &amp; _
            " of " &amp; rstAuthors.RecordCount &amp; vbCr &amp; _
            "Author: " &amp; rstAuthors!au_fname &amp; _
            " " &amp; rstAuthors!au_lname &amp; vbCr &amp; _
            "Location: " &amp; rstAuthors!city &amp; _
            ", " &amp; rstAuthors!State &amp; vbCr &amp; vbCr &amp; _
            "Enter number of records to Move " &amp; _
            "(positive or negative).")
        
          ' this is for exiting the loop
        'lngMove = CLng(strCommand)
        
        lngMove = CLng(Val(strCommand))
        If lngMove = 0 Then
            MsgBox "You either entered a non-number or canceled the input box. Exit the application."
            Exit Do
        End If
        
        ' Store bookmark in case the Move goes too far
        ' forward or backward
        varBookmark = rstAuthors.Bookmark
        
        ' Move method requires parameter of data type Long
        rstAuthors.Move lngMove
        
        ' Trap for BOF or EOF
        If rstAuthors.BOF Then
            MsgBox "Too far backward! Returning to current record."
            rstAuthors.Bookmark = varBookmark
        End If
        If rstAuthors.EOF Then
            MsgBox "Too far forward!  Returning to current record."
            rstAuthors.Bookmark = varBookmark
        End If
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
'EndMoveVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>