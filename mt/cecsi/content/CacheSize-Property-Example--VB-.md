---
title: "CacheSize Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a237ffdb-6e5b-47c6-9901-d5cdbe8625f3
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
# CacheSize Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink> property to show the difference in performance for an operation performed with and without a 30-record cache.</para>
    <code>'BeginCacheSizeVB
    
    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    'recordset and connection variables
    Dim rstRoySched As ADODB.Recordset
    Dim strSQLSched As String
    Dim strCnxn As String
     'record variables
    Dim sngStart As Single
    Dim sngEnd As Single
    Dim sngNoCache As Single
    Dim sngCache As Single
    Dim intLoop As Integer
    Dim strTemp As String
    
    ' Open the connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    
    ' Open the RoySched Table
    Set rstRoySched = New ADODB.Recordset
    strSQLSched = "roysched"
    rstRoySched.Open strSQLSched, strCnxn, , , adCmdTable
    
    ' Enumerate the Recordset object twice and
    ' record the elapsed time
    sngStart = Timer

    For intLoop = 1 To 2
        rstRoySched.MoveFirst
    
        If Not rstRoySched.EOF Then
            ' Execute a simple operation for the
            ' performance test
            Do
                strTemp = rstRoySched!title_id
                rstRoySched.MoveNext
            Loop Until rstRoySched.EOF
        End If
    Next intLoop

    sngEnd = Timer
    sngNoCache = sngEnd - sngStart

    ' Cache records in groups of 30 records.
    rstRoySched.MoveFirst
    rstRoySched.CacheSize = 30
    sngStart = Timer
    
    ' Enumerate the Recordset object twice and record
    ' the elapsed time
    For intLoop = 1 To 2
        rstRoySched.MoveFirst
        Do While Not rstRoySched.EOF
            ' Execute a simple operation for the
            ' performance test
            strTemp = rstRoySched!title_id
            rstRoySched.MoveNext
        Loop
    Next intLoop

    sngEnd = Timer
    sngCache = sngEnd - sngStart
    
    ' Display performance results.
    MsgBox "Caching Performance Results:" &amp; vbCr &amp; _
        "   No cache: " &amp; Format(sngNoCache, "##0.000") &amp; " seconds" &amp; vbCr &amp; _
        "   30-record cache: " &amp; Format(sngCache, "##0.000") &amp; " seconds"
   
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
'EndCacheSizeVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>