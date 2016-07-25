---
title: "GetString Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14c96d71-46a8-4782-b474-80ce348e8bff
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
# GetString Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="92452940-b2a7-456e-94fc-3780c71da33c">GetString</legacyLink> method.</para>
    <para>Assume you are debugging a data access problem and want a quick, simple way of printing the current contents of a small <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
    <code>'BeginGetStringVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

     ' connection variables
    Dim Cnxn As ADODB.Connection
    Dim rstAuthors As ADODB.Recordset
    Dim strCnxn As String
    Dim strSQLAuthors As String
    Dim varOutput As Variant
    
     ' specific variables
    Dim strPrompt As String
    Dim strState As String
    
     ' open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
     ' get user input
    strPrompt = "Enter a state (CA, IN, KS, MD, MI, OR, TN, UT): "
    strState = Trim(InputBox(strPrompt, "GetString Example"))
     
     ' open recordset
    Set rstAuthors = New ADODB.Recordset
    strSQLAuthors = "SELECT au_fname, au_lname, address, city FROM Authors " &amp; _
                "WHERE state = '" &amp; strState &amp; "'"
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenStatic, adLockReadOnly, adCmdText
    
    If Not rstAuthors.EOF Then
    ' Use all defaults: get all rows, TAB as column delimiter,
    ' CARRIAGE RETURN as row delimiter, EMPTY-string as null delimiter
       varOutput = rstAuthors.GetString(adClipString)
        ' print output
       Debug.Print "State = '" &amp; strState &amp; "'"
       Debug.Print "Name             Address             City" &amp; vbCr
       Debug.Print varOutput
    Else
       Debug.Print "No rows found for state = '" &amp; strState &amp; "'" &amp; vbCr
    End If
    
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
'EndGetStringVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="92452940-b2a7-456e-94fc-3780c71da33c">GetString Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>