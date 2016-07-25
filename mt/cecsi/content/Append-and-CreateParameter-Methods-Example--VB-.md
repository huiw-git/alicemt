---
title: "Append and CreateParameter Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46908cbd-434f-43e7-a794-ed0be0e0c0a7
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
# Append and CreateParameter Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append</legacyLink> and <legacyLink xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter</legacyLink> methods to execute a stored procedure with an input parameter.</para>
    <code>'BeginAppendVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
    
Public Sub Main()
    On Error GoTo ErrorHandler

    'recordset, command and connection variables
    Dim Cnxn As ADODB.Connection
    Dim cmdByRoyalty As ADODB.Command
    Dim prmByRoyalty As ADODB.Parameter
    Dim rstByRoyalty As ADODB.Recordset
    Dim rstAuthors As ADODB.Recordset
    Dim strCnxn As String
    Dim strSQLAuthors As String
    Dim strSQLByRoyalty As String
     'record variables
    Dim intRoyalty As Integer
    Dim strAuthorID As String
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
       
    ' Open command object with one parameter
    Set cmdByRoyalty = New ADODB.Command
    cmdByRoyalty.CommandText = "byroyalty"
    cmdByRoyalty.CommandType = adCmdStoredProc
   
    ' Get parameter value and append parameter
    intRoyalty = Trim(InputBox("Enter royalty:"))
    Set prmByRoyalty = cmdByRoyalty.CreateParameter("percentage", adInteger, adParamInput)
    cmdByRoyalty.Parameters.Append prmByRoyalty
    prmByRoyalty.Value = intRoyalty
    
    ' Create recordset by executing the command
    Set cmdByRoyalty.ActiveConnection = Cnxn
    Set rstByRoyalty = cmdByRoyalty.Execute
    
    ' Open the Authors Table to get author names for display
    ' and set cursor client-side
    Set rstAuthors = New ADODB.Recordset
    strSQLAuthors = "Authors"
    rstAuthors.Open strSQLAuthors, Cnxn, adUseClient, adLockOptimistic, adCmdTable
    
    ' Print recordset adding author names from Authors table
    Debug.Print "Authors with " &amp; intRoyalty &amp; " percent royalty"
    
    Do Until rstByRoyalty.EOF
        strAuthorID = rstByRoyalty!au_id
        Debug.Print "   " &amp; rstByRoyalty!au_id &amp; ", ";
        rstAuthors.Filter = "au_id = '" &amp; strAuthorID &amp; "'"
        Debug.Print rstAuthors!au_fname &amp; " " &amp; rstAuthors!au_lname
        rstByRoyalty.MoveNext
    Loop

    ' clean up
    rstByRoyalty.Close
    rstAuthors.Close
    Cnxn.Close
    Set rstByRoyalty = Nothing
    Set rstAuthors = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstByRoyalty Is Nothing Then
        If rstByRoyalty.State = adStateOpen Then rstByRoyalty.Close
    End If
    Set rstByRoyalty = Nothing
    
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
'EndAppendVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method</link>
<link xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter Method</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>