---
title: "Refresh Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5375fa1-4711-4f7e-9ba4-54c427f71325
caps.latest.revision: 9
manager: sonalm
---
# Refresh Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates using the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method to refresh the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection for a stored procedure <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object.</para>
    <code>'BeginRefreshVB
Public Sub Main()
    On Error GoTo ErrorHandler

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection strings
    
    ' connection and recordset variables
    Dim Cnxn As ADODB.Connection
    Dim cmdByRoyalty As ADODB.Command
    Dim rstByRoyalty As ADODB.Recordset
    Dim rstAuthors As ADODB.Recordset
    Dim strCnxn As String
    Dim strSQLAuthors As String
     ' record variables
    Dim intRoyalty As Integer
    Dim strAuthorID As String
    Dim strRoyalty As String
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
       
    ' Open a command object for a stored procedure
    ' with one parameter
    Set cmdByRoyalty = New ADODB.Command
    Set cmdByRoyalty.ActiveConnection = Cnxn
    cmdByRoyalty.CommandText = "byroyalty"
    cmdByRoyalty.CommandType = adCmdStoredProc
    cmdByRoyalty.Parameters.Refresh
    
    ' Get paramater value, execute the command
    ' and store the results in a recordset
    strRoyalty = InputBox("Enter royalty:")
    If strRoyalty = "" Then
        Err.Raise 1, , "You either didn't enter royalty or canceled the input box. Exit the application"
    End If
    
    intRoyalty = Trim(strRoyalty)
    cmdByRoyalty.Parameters(1) = intRoyalty
    Set rstByRoyalty = cmdByRoyalty.Execute()
       
    ' Open the Authors table to get author names for display
    Set rstAuthors = New ADODB.Recordset
    strSQLAuthors = "Authors"
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenForwardOnly, adLockPessimistic, adCmdTable
    
    ' Print current data in the recordset
    ' and add author names
    Debug.Print "Authors with " &amp; intRoyalty &amp; " percent royalty"
    
    Do Until rstByRoyalty.EOF
        strAuthorID = rstByRoyalty!au_id
        Debug.Print "   " &amp; rstByRoyalty!au_id &amp; ", ";
        rstAuthors.Filter = "au_id = '" &amp; strAuthorID &amp; "'"
        Debug.Print rstAuthors!au_fname &amp; " "; rstAuthors!au_lname
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
'EndRefreshVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
<link xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>