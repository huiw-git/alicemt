---
title: "Named Commands"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a0ec8f9-5ba3-4f9f-b80d-2073aa049586
caps.latest.revision: 13
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
# Named Commands
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyLink xlink:href="0b81af6f-b9ae-4f7c-b59b-b5bdd775036f">Creating and Executing a Simple Command</legacyLink> shows one way to execute a command. There is another way: you can make it a named command, and then call this named command directly on the <legacyBold>Connection</legacyBold> object (assigned to the <legacyBold>ActiveConnection</legacyBold> property of the <legacyBold>Command</legacyBold> object). Naming a command means assigning a name to the <legacyBold>Name</legacyBold> property of a <legacyBold>Command</legacyBold> object. For example,</para>
    <code>objCmd.Name = "GetCustomers"
objCmd.ActiveConnection = objConn
objConn.GetCustomers objRs</code>
    <para>The named command acts as if it were a "custom method" on the <legacyBold>Connection</legacyBold> object. The result of the command is returned as an out parameter of this "custom method". </para>
    <para>The following example illustrates this feature. </para>
    <code>'BeginNamedCmd
    On Error GoTo ErrHandler:
    
    Dim objConn As New ADODB.Connection
    Dim objCmd As New ADODB.Command
    Dim objRs As New ADODB.Recordset
    
    ' Connect to the data source.
    Set objConn = GetNewConnection
    
    objCmd.CommandText = "SELECT CustomerID, CompanyName FROM Customers"
    objCmd.CommandType = adCmdText
    
    'Name the command.
    objCmd.Name = "GetCustomers"
    
    objCmd.ActiveConnection = objConn
    
    ' Execute using Command.Name from the Connection.
    objConn.GetCustomers objRs
    
    ' Display.
    Do While Not objRs.EOF
        Debug.Print objRs(0) &amp; vbTab &amp; objRs(1)
        objRs.MoveNext
    Loop
    
    'clean up
    objRs.Close
    objConn.Close
    Set objRs = Nothing
    Set objConn = Nothing
    Set objCmd = Nothing
    Exit Sub
    
ErrHandler:
    'clean up
    If objRs.State = adStateOpen Then
        objRs.Close
    End If
    
    If objConn.State = adStateOpen Then
        objConn.Close
    End If
    
    Set objRs = Nothing
    Set objConn = Nothing
    Set objCmd = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
'EndNamedCmd</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object (ADO)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>