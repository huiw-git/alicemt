---
title: "ActiveCommand Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23b06499-62df-4f46-88eb-6da392f9b456
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
# ActiveCommand Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand</legacyLink> property.</para>
    <para>A subroutine is given a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object whose <legacyBold>ActiveCommand</legacyBold> property is used to display the command text and parameter that created the <legacyBold>Recordset</legacyBold>.</para>
    <code>'BeginActiveCommandVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

        'recordset and connection variables
    Dim cmd As ADODB.Command
    Dim rst As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
        'record variables
    Dim strPrompt As String
    Dim strName As String
    
    Set Cnxn = New ADODB.Connection
    Set cmd = New ADODB.Command
    
    strPrompt = "Enter an author's name (e.g., Ringer): "
    strName = Trim(InputBox(strPrompt, "ActiveCommandX Example"))
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
        
        'create SQL command string
    cmd.CommandText = "SELECT * FROM Authors WHERE au_lname = ?"
    cmd.Parameters.Append cmd.CreateParameter("LastName", adChar, adParamInput, 20, strName)
    
    Cnxn.Open strCnxn
    cmd.ActiveConnection = Cnxn
    
        'create the recordset by executing command string
    Set rst = cmd.Execute(, , adCmdText)
        'see the results
    Call ActiveCommandXprint(rst)
  
    ' clean up
    Cnxn.Close
    Set rst = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rst Is Nothing Then
        If rst.State = adStateOpen Then rst.Close
    End If
    Set rst = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndActiveCommandVB</code>
    <para>The <legacyBold>ActiveCommandXprint</legacyBold> routine is given only a <legacyBold>Recordset</legacyBold> object, yet it must print the command text and parameter that created the <legacyBold>Recordset</legacyBold>. This can be done because the <legacyBold>Recordset</legacyBold> object's <legacyBold>ActiveCommand</legacyBold> property yields the associated <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object.</para>
    <para>The <legacyBold>Command</legacyBold> object's <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> property yields the parameterized command that created the <legacyBold>Recordset</legacyBold>. The <legacyBold>Command</legacyBold> object's <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection yields the value that was substituted for the command's parameter placeholder ("<legacyBold>?</legacyBold>").</para>
    <para>Finally, an error message or the author's name and ID are printed.</para>
    <code>'BeginActiveCommandPrintVB
Public Sub ActiveCommandXprint(rstp As ADODB.Recordset)

    Dim strName As String
    
    strName = rstp.ActiveCommand.Parameters.Item("LastName").Value
    
    Debug.Print "Command text = '"; rstp.ActiveCommand.CommandText; "'"
    Debug.Print "Parameter = '"; strName; "'"
    
    If rstp.BOF = True Then
       Debug.Print "Name = '"; strName; "', not found."
    Else
       Debug.Print "Name = '"; rstp!au_fname; " "; rstp!au_lname; _
             "', author ID = '"; rstp!au_id; "'"
    End If

    rstp.Close
    Set rstp = Nothing
End Sub
'EndActiveCommandPrintVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand Property</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>