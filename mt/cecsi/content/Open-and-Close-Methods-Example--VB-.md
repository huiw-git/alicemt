---
title: "Open and Close Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1311d561-0e86-40f5-8cbc-ad8f13e626d1
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
# Open and Close Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyBold>Open</legacyBold> and <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> methods on both <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> objects that have been opened.</para>
    <code>'BeginOpenVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub OpenX()
    On Error GoTo ErrorHandler

    Dim Cnxn As ADODB.Connection
    Dim rstEmployees As ADODB.Recordset
    Dim strCnxn As String
    Dim strSQLEmployees As String
    Dim varDate As Variant
    
    ' Open connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Set Cnxn = New ADODB.Connection
    Cnxn.Open strCnxn
    
    ' Open employee table
    Set rstEmployees = New ADODB.Recordset
    strSQLEmployees = "employee"
    rstEmployees.Open strSQLEmployees, Cnxn, adOpenKeyset, adLockOptimistic, adCmdTable
    
    ' Assign the first employee record's hire date
    ' to a variable, then change the hire date
    varDate = rstEmployees!hire_date
    Debug.Print "Original data"
    Debug.Print "  Name - Hire Date"
    Debug.Print "  " &amp; rstEmployees!fname &amp; " " &amp; _
        rstEmployees!lname &amp; " - " &amp; rstEmployees!hire_date
    rstEmployees!hire_date = #1/1/1900#
    rstEmployees.Update
    Debug.Print "Changed data"
    Debug.Print "  Name - Hire Date"
    Debug.Print "  " &amp; rstEmployees!fname &amp; " " &amp; _
        rstEmployees!lname &amp; " - " &amp; rstEmployees!hire_date
    
    ' Requery Recordset and reset the hire date
    rstEmployees.Requery
    rstEmployees!hire_date = varDate
    rstEmployees.Update
    Debug.Print "Data after reset"
    Debug.Print "  Name - Hire Date"
    Debug.Print "  " &amp; rstEmployees!fname &amp; " " &amp; _
       rstEmployees!lname &amp; " - " &amp; rstEmployees!hire_date

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
'EndOpenVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close Method</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="663defab-5545-4973-9036-24d5882c9737">Open Method (ADO Connection)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>