---
title: "NextRecordset Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b14806da-80d9-4da4-bb87-f558b36a6ac0
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
# NextRecordset Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink> method to view the data in a recordset that uses a compound command statement made up of three separate <legacyBold>SELECT</legacyBold> statements.</para>
    <code>'BeginNextRecordsetVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    ' connection and recordset variables
    Dim rstCompound As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim SQLCompound As String
    
    Dim intCount As Integer
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open compound recordset
    Set rstCompound = New ADODB.Recordset
    SQLCompound = "SELECT * FROM Authors; " &amp; _
        "SELECT * FROM stores; " &amp; _
        "SELECT * FROM jobs"
    rstCompound.Open SQLCompound, Cnxn, adOpenStatic, adLockReadOnly, adCmdText
    
    ' Display results from each SELECT statement
    intCount = 1
    Do Until rstCompound Is Nothing
        Debug.Print "Contents of recordset #" &amp; intCount
        
        Do Until rstCompound.EOF
            Debug.Print , rstCompound.Fields(0), rstCompound.Fields(1)
            rstCompound.MoveNext
        Loop
        
        Set rstCompound = rstCompound.NextRecordset
        intCount = intCount + 1
    Loop
   
    ' clean up
    Cnxn.Close
    Set rstCompound = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstCompound Is Nothing Then
        If rstCompound.State = adStateOpen Then rstCompound.Close
    End If
    Set rstCompound = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndNextRecordsetVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>