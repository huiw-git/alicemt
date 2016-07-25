---
title: "Sort Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc2fd40b-65d6-4023-90a3-90c9a88ef6cf
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
# Sort Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object's <legacyLink xlink:href="3683ffa0-6f93-4906-9533-ef6942f24f39">Sort</legacyLink> property to reorder the rows of a <legacyBold>Recordset</legacyBold> derived from the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table of the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database. A secondary utility routine prints each row.</para>
    <code>'BeginSortVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler
    
     ' connection and recordset variables
    Dim Cnxn As New ADODB.Connection
    Dim rstAuthors As New ADODB.Recordset
    Dim strCnxn As String
    Dim strSQLAuthors As String
        
    Dim strTitle As String
        
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' open client-side recordset to enable sort method
    Set rstAuthors = New ADODB.Recordset
    rstAuthors.CursorLocation = adUseClient
    strSQLAuthors = "SELECT * FROM Authors"
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenStatic, adLockReadOnly, adCmdText
    
     ' sort the recordset last name ascending
    rstAuthors.Sort = "au_lname ASC, au_fname ASC"
     ' show output
    Debug.Print "Last Name Ascending:"
    Debug.Print "First Name  Last Name" &amp; vbCr
    
    rstAuthors.MoveFirst
    Do Until rstAuthors.EOF
        Debug.Print rstAuthors!au_fname &amp; " " &amp; rstAuthors!au_lname
        rstAuthors.MoveNext
    Loop
    
     ' sort the recordset last name descending
    rstAuthors.Sort = "au_lname DESC, au_fname ASC"
     ' show output
    Debug.Print "Last Name Descending"
    Debug.Print "First Name  Last Name" &amp; vbCr
    
    Do Until rstAuthors.EOF
        Debug.Print rstAuthors!au_fname &amp; " " &amp; rstAuthors!au_lname
        rstAuthors.MoveNext
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
'EndSortVB</code>
    <para>This is the secondary utility routine that prints the given title, and the contents of the specified <legacyBold>Recordset</legacyBold>.</para>
    <code>Attribute VB_Name = "Sort"</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="3683ffa0-6f93-4906-9533-ef6942f24f39">Sort Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>