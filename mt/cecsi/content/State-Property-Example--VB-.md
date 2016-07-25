---
title: "State Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9da6db50-d9bb-47e1-ae8b-be3c9b88cf9a
caps.latest.revision: 10
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
# State Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property to display a message while asynchronous connections are opening and asynchronous commands are executing.</para>
    <code>'BeginStateVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    Dim Cnxn1 As ADODB.Connection
    Dim Cnxn2 As ADODB.Connection
    Dim cmdChange As ADODB.Command
    Dim cmdRestore As ADODB.Command
    Dim strCnxn As String
    Dim strSQL As String
    
    ' Open two asynchronous connections, displaying
    ' a message while connecting
    Set Cnxn1 = New ADODB.Connection
    Set Cnxn2 = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
       
    Cnxn1.Open strCnxn, , , adAsyncConnect
    Do Until Cnxn1.State &lt;&gt; adStateConnecting
       Debug.Print "Opening first connection...."
    Loop
    
    Cnxn2.Open strCnxn, , , adAsyncConnect
    Do Until Cnxn2.State &lt;&gt; adStateConnecting
       Debug.Print "Opening second connection...."
    Loop
    
    ' Create two command objects
    Set cmdChange = New ADODB.Command
    cmdChange.ActiveConnection = Cnxn1
    strSQL = "UPDATE Titles SET type = 'self_help' WHERE type = 'psychology'"
    cmdChange.CommandText = strSQL
    
    Set cmdRestore = New ADODB.Command
    cmdRestore.ActiveConnection = Cnxn2
    strSQL = "UPDATE Titles SET type = 'psychology' WHERE type = 'self_help'"
    cmdRestore.CommandText = strSQL
    
    ' Executing the commands, displaying a message
    ' while they are executing
    cmdChange.Execute , , adAsyncExecute
    Do Until cmdChange.State &lt;&gt; adStateExecuting
       Debug.Print "Change command executing...."
    Loop
    
    cmdRestore.Execute , , adAsyncExecute
    Do Until cmdRestore.State &lt;&gt; adStateExecuting
       Debug.Print "Restore command executing...."
    Loop

    ' clean up
    Cnxn1.Close
    Cnxn2.Close
    Set Cnxn1 = Nothing
    Set Cnxn2 = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not Cnxn1 Is Nothing Then
        If Cnxn1.State = adStateOpen Then Cnxn1.Close
    End If
    Set Cnxn1 = Nothing
    
    If Not Cnxn2 Is Nothing Then
        If Cnxn2.State = adStateOpen Then Cnxn2.Close
    End If
    Set Cnxn2 = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndStateVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>