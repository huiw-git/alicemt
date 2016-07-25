---
title: "Update and CancelUpdate Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 55bedd08-7440-4da4-b854-4ac9ef2fdedb
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
# Update and CancelUpdate Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method in conjunction with the <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> method.</para>
    <code>'BeginUpdateVB
Public Sub Main()
    On Error GoTo ErrorHandler

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

    ' recordset and connection variables
    Dim rstEmployees As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLEmployees As String
     ' buffer variables
    Dim strOldFirst As String
    Dim strOldLast As String
    Dim strMessage As String
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
     
    ' Open recordset to enable changes
    Set rstEmployees = New ADODB.Recordset
    strSQLEmployees = "SELECT fname, lname FROM Employee ORDER BY lname"
    rstEmployees.Open strSQLEmployees, Cnxn, adOpenKeyset, adLockOptimistic, adCmdText
    
    ' Store original data
    strOldFirst = rstEmployees!fname
    strOldLast = rstEmployees!lname
    ' Change data in edit buffer
    rstEmployees!fname = "Linda"
    rstEmployees!lname = "Kobara"
    
    ' Show contents of buffer and get user input
    strMessage = "Edit in progress:" &amp; vbCr &amp; _
        "  Original data = " &amp; strOldFirst &amp; " " &amp; _
        strOldLast &amp; vbCr &amp; "  Data in buffer = " &amp; _
        rstEmployees!fname &amp; " " &amp; rstEmployees!lname &amp; vbCr &amp; vbCr &amp; _
        "Use Update to replace the original data with " &amp; _
        "the buffered data in the Recordset?"
    
    If MsgBox(strMessage, vbYesNo) = vbYes Then
        rstEmployees.Update
    Else
        rstEmployees.CancelUpdate
    End If
    
    ' show the resulting data
    MsgBox "Data in recordset = " &amp; rstEmployees!fname &amp; " " &amp; _
       rstEmployees!lname
    
    ' restore original data because this is a demonstration
    If Not (strOldFirst = rstEmployees!fname And _
           strOldLast = rstEmployees!lname) Then
        rstEmployees!fname = strOldFirst
        rstEmployees!lname = strOldLast
        rstEmployees.Update
    End If
   
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
' EndUpdateVB</code>
    <para>This example demonstrates the <legacyBold>Update</legacyBold> method in conjunction with the <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> method.</para>
    <code>Attribute VB_Name = "Update"</code>
  </introduction>
  <relatedTopics>
<link xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>