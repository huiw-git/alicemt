---
title: "Source Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c83eb01-71c7-4c5d-9778-6270471c8164
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
# Source Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source</legacyLink> property by opening three <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects based on different data sources.</para>
    <code>'BeginSourceVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    Dim Cnxn As ADODB.Connection
    Dim rstTitles As ADODB.Recordset
    Dim rstPublishers As ADODB.Recordset
    Dim rstPublishersDirect As ADODB.Recordset
    Dim rstTitlesPublishers As ADODB.Recordset
    Dim cmdSQL As ADODB.Command
    Dim strCnxn As String
    Dim strSQL As String
    
    ' Open a connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open a recordset based on a command object
    Set cmdSQL = New ADODB.Command
    Set cmdSQL.ActiveConnection = Cnxn
    strSQL = "Select title, type, pubdate FROM Titles ORDER BY title"
    cmdSQL.CommandText = strSQL
    Set rstTitles = cmdSQL.Execute()
    
    ' Open a recordset based on a table
    Set rstPublishers = New ADODB.Recordset
    strSQL = "Publishers"
    rstPublishers.Open strSQL, Cnxn, adOpenStatic, adLockReadOnly, adCmdTable
    'rstPublishers.Open strSQL, Cnxn, , , adCmdTable
     ' the above two lines of code are identical
    
    ' Open a recordset based on a table
    Set rstPublishersDirect = New ADODB.Recordset
    rstPublishersDirect.Open strSQL, strCnxn, , , adCmdTableDirect
    
    ' Open a recordset based on an SQL string.
    Set rstTitlesPublishers = New ADODB.Recordset
    strSQL = "SELECT title_ID AS TitleID, title AS Title, " &amp; _
        "publishers.pub_id AS PubID, pub_name AS PubName " &amp; _
        "FROM publishers INNER JOIN Titles " &amp; _
        "ON publishers.pub_id = Titles.pub_id " &amp; _
        "ORDER BY Title"
    rstTitlesPublishers.Open strSQL, strCnxn, , , adCmdText
    
    ' Use the Source property to display the source of each recordset.
    MsgBox "rstTitles source: " &amp; vbCr &amp; _
        rstTitles.Source &amp; vbCr &amp; vbCr &amp; _
        "rstPublishers source: " &amp; vbCr &amp; _
        rstPublishers.Source &amp; vbCr &amp; vbCr &amp; _
        "rstPublishersDirect source: " &amp; vbCr &amp; _
        rstPublishersDirect.Source &amp; vbCr &amp; vbCr &amp; _
        "rstTitlesPublishers source: " &amp; vbCr &amp; _
        rstTitlesPublishers.Source

    ' clean up
    rstTitles.Close
    rstPublishers.Close
    rstTitlesPublishers.Close
    Cnxn.Close
    Set rstTitles = Nothing
    Set rstPublishers = Nothing
    Set rstTitlesPublishers = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstTitles Is Nothing Then
        If rstTitles.State = adStateOpen Then rstTitles.Close
    End If
    Set rstTitles = Nothing
    
    If Not rstPublishers Is Nothing Then
        If rstPublishers.State = adStateOpen Then rstPublishers.Close
    End If
    Set rstPublishers = Nothing
    
    If Not rstTitlesPublishers Is Nothing Then
        If rstTitlesPublishers.State = adStateOpen Then rstTitlesPublishers.Close
    End If
    Set rstTitlesPublishers = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndSourceVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source Property (ADO Recordset)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>