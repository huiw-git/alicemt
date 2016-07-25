---
title: "StayInSync Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b682bcc3-04b3-42b0-86f4-c17e0cd29baf
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
# StayInSync Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how the <legacyLink xlink:href="502d69b5-dc9a-455d-b115-a03bd39a552b">StayInSync</legacyLink> property facilitates accessing rows in a hierarchical <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
    <para>The outer loop displays each author's first and last name, state, and identification. The appended <legacyBold>Recordset </legacyBold>for each row is retrieved from the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection and automatically assigned to <legacyBold>rstTitleAuthor</legacyBold> by the <legacyBold>StayInSync</legacyBold> property whenever the parent <legacyBold>Recordset</legacyBold> moves to a new row. The inner loop displays four fields from each row in the appended recordset.</para>
    <code>'BeginStayInSyncVB
Public Sub Main()
    On Error GoTo ErrorHandler

    Dim Cnxn As ADODB.Connection
    Dim rst As ADODB.Recordset
    Dim rstTitleAuthor As New ADODB.Recordset
    Dim strCnxn As String

    ' Open the connection with Data Shape attributes
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider=MSDataShape;Data Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Create a recordset
    Set rst = New ADODB.Recordset
    rst.StayInSync = True
    rst.Open "SHAPE {select * from Authors} " &amp; _
                   "APPEND ( { select * from titleauthor} AS chapTitleAuthor " &amp; _
                   "RELATE au_id TO au_id) ", Cnxn, , , adCmdText
    
    Set rstTitleAuthor = rst("chapTitleAuthor").Value
    Do Until rst.EOF
        Debug.Print rst!au_fname &amp; " " &amp; rst!au_lname &amp; " " &amp; _
                   rst!State &amp; " " &amp; rst!au_id
       
        Do Until rstTitleAuthor.EOF
            Debug.Print rstTitleAuthor(0) &amp; " " &amp; rstTitleAuthor(1) &amp; " " &amp; _
                   rstTitleAuthor(2) &amp; " " &amp; rstTitleAuthor(3)
            rstTitleAuthor.MoveNext
        Loop
       
        rst.MoveNext
    Loop

    ' Clean up
    rst.Close
    Cnxn.Close
    Set rst = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' Clean up
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
'EndStayInSyncVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="502d69b5-dc9a-455d-b115-a03bd39a552b">StayInSync Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>