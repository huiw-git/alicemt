---
title: "ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dade4531-0bcc-4a52-8f86-b110ba2a3f9d
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
# ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink>, <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink>, <legacyLink xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout</legacyLink>, <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink>, <legacyLink xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size</legacyLink>, and <legacyLink xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction</legacyLink> properties to execute a stored procedure.</para>
    <code>'BeginActiveConnectionVB

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

    ' Define a command object for a stored procedure
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    Set cmdByRoyalty = New ADODB.Command
    Set cmdByRoyalty.ActiveConnection = Cnxn
    ' Set the criteria
    strSQLByRoyalty = "byroyalty"
    cmdByRoyalty.CommandText = strSQLByRoyalty
    cmdByRoyalty.CommandType = adCmdStoredProc
    cmdByRoyalty.CommandTimeout = 15
       
    ' Define the stored procedure's input parameter
    intRoyalty = Trim(InputBox("Enter royalty:"))
    Set prmByRoyalty = New ADODB.Parameter
    prmByRoyalty.Type = adInteger
    prmByRoyalty.Size = 3
    prmByRoyalty.Direction = adParamInput
    prmByRoyalty.Value = intRoyalty
    
    cmdByRoyalty.Parameters.Append prmByRoyalty
    
    ' Create a recordset by executing the command.
    Set rstByRoyalty = cmdByRoyalty.Execute()
      
    ' Open the Authors Table to get author names for display
    Set rstAuthors = New ADODB.Recordset
    strSQLAuthors = "Authors"
    
    'rstAuthors.Open strSQLAuthors, strCnxn, , , adCmdTable
    rstAuthors.Open strSQLAuthors, strCnxn, adOpenForwardOnly, adLockReadOnly, adCmdTable
    'the above two lines of code are identical as the default values for
    'CursorType and LockType arguments match those shown
    
    ' Print the recordset and add author names from Table
    Debug.Print "Authors with " &amp; intRoyalty &amp; _
       " percent royalty"
      
    Do Until rstByRoyalty.EOF
        strAuthorID = rstByRoyalty!au_id
        Debug.Print , rstByRoyalty!au_id &amp; ", ";
        rstAuthors.Filter = "au_id = '" &amp; strAuthorID &amp; "'"
        Debug.Print rstAuthors!au_fname &amp; " " &amp; _
            rstAuthors!au_lname
        rstByRoyalty.MoveNext
    Loop

    ' clean up
    rstAuthors.Close
    rstByRoyalty.Close
    Cnxn.Close
    Set rstAuthors = Nothing
    Set rstByRoyalty = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstAuthors Is Nothing Then
        If rstAuthors.State = adStateOpen Then rstAuthors.Close
    End If
    Set rstAuthors = Nothing
    
    If Not rstByRoyalty Is Nothing Then
        If rstByRoyalty.State = adStateOpen Then rstByRoyalty.Close
    End If
    Set rstByRoyalty = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndActiveConnectionVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand Property</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property</link>
<link xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout Property</link>
<link xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType Property</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction Property</link>
<link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>