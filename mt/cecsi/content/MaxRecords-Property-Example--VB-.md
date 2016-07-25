---
title: "MaxRecords Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 630a3be4-7a87-41cf-997e-8bb50d89db1e
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
# MaxRecords Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords</legacyLink> property to open a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> containing the 10 most expensive titles in the <legacyBold><legacyItalic>Titles</legacyItalic></legacyBold> table.</para>
    <code>'BeginMaxRecordsVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    Dim rstTitles As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLTitles As String
    
    ' Open a connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open recordset containing the 10 most expensive
    ' titles in the Titles table
    Set rstTitles = New ADODB.Recordset
    rstTitles.MaxRecords = 10
    
    strSQLTitles = "SELECT Title, Price FROM Titles ORDER BY Price DESC"
    rstTitles.Open strSQLTitles, strCnxn, adOpenStatic, adLockReadOnly, adCmdText
    
    ' Display the contents of the recordset
    Debug.Print "Top Ten Titles by Price:"
    
    Do Until rstTitles.EOF
        Debug.Print "  " &amp; rstTitles!Title &amp; " - " &amp; rstTitles!Price
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
'EndMaxRecordsVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>