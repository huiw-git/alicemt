---
title: "Prepared Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3a3db2d-7f73-4288-ad08-5468f251d610
caps.latest.revision: 9
manager: sonalm
---
# Prepared Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="11ca8825-765e-4bb4-a6ce-3f6564ad8755">Prepared</legacyLink> property by opening two <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> objects — one prepared and one not prepared.</para>
    <code>'BeginPreparedVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    Dim Cnxn As ADODB.Connection
    Dim cmd1 As ADODB.Command
    Dim cmd2 As ADODB.Command
    
    Dim strCnxn As String
    Dim strCmd As String
    Dim sngStart As Single
    Dim sngEnd As Single
    Dim sngNotPrepared As Single
    Dim sngPrepared As Single
    Dim intLoop As Integer
    
    ' Open a connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Set Cnxn = New ADODB.Connection
    Cnxn.Open strCnxn
    
    ' Create two command objects for the same
    ' command - one prepared and one not prepared
    strCmd = "SELECT title, type FROM Titles ORDER BY type"
    
    Set cmd1 = New ADODB.Command
    Set cmd1.ActiveConnection = Cnxn
    cmd1.CommandText = strCmd
       
    Set cmd2 = New ADODB.Command
    Set cmd2.ActiveConnection = Cnxn
    cmd2.CommandText = strCmd
    cmd2.Prepared = True
    
    ' Set a timer, then execute the unprepared
    ' command 20 times
    sngStart = Timer
    For intLoop = 1 To 20
        cmd1.Execute
    Next intLoop
    sngEnd = Timer
    sngNotPrepared = sngEnd - sngStart
    
    ' Reset the timer, then execute the prepared
    ' command 20 times
    sngStart = Timer
    For intLoop = 1 To 20
        cmd2.Execute
    Next intLoop
    sngEnd = Timer
    sngPrepared = sngEnd - sngStart
    
    ' Display performance results
    MsgBox "Performance Results:" &amp; vbCr &amp; _
        "   Not Prepared: " &amp; Format(sngNotPrepared, _
        "##0.000") &amp; " seconds" &amp; vbCr &amp; _
        "   Prepared: " &amp; Format(sngPrepared, _
        "##0.000") &amp; " seconds"
 
    ' clean up
    Cnxn.Close
    Set Cnxn = Nothing
    Set cmd1 = Nothing
    Set cmd2 = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    Set cmd1 = Nothing
    Set cmd2 = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndPreparedVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="11ca8825-765e-4bb4-a6ce-3f6564ad8755">Prepared Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>