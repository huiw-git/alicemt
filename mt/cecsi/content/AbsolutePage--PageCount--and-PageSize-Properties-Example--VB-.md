---
title: "AbsolutePage, PageCount, and PageSize Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5aaada64-5115-4adc-8668-827348f32566
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
# AbsolutePage, PageCount, and PageSize Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <code>'BeginAbsolutePageVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler
  
    'recordset and connection variables
    Dim rstEmployees As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQL As String
        'record variables
    Dim strMessage As String
    Dim intPage As Integer
    Dim intPageCount As Integer
    Dim intRecord As Integer

    'Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open employee recordset
    ' Use client cursor to enable AbsolutePosition property
    Set rstEmployees = New ADODB.Recordset
    strSQL = "employee"
    rstEmployees.Open strSQL, strCnxn, adUseClient, adLockReadOnly, adCmdTable
   
    ' Display names and hire dates, five records at a time
    rstEmployees.PageSize = 5
    intPageCount = rstEmployees.PageCount
    For intPage = 1 To intPageCount
        rstEmployees.AbsolutePage = intPage
        strMessage = ""
        For intRecord = 1 To rstEmployees.PageSize
            strMessage = strMessage &amp; _
                rstEmployees!fname &amp; " " &amp; _
                rstEmployees!lname &amp; " " &amp; _
                rstEmployees!hire_date &amp; vbCr
            rstEmployees.MoveNext
            If rstEmployees.EOF Then Exit For
        Next intRecord
        MsgBox strMessage
    Next intPage
   
    ' clean up
    rstEmployees.Close
    Cnxn.Close
    Set rstEmployees = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstEmployees Is Nothing Then
        If rstEmployees.State = adStateOpen Then rstEmployees.Close
    End If
    Set rstEmployees = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndAbsolutePageVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage Property</link>
<link xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount Property</link>
<link xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>