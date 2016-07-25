---
title: "Save and Open Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddccdf58-9c57-4c9b-8b7f-0cf193f955fb
caps.latest.revision: 11
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
# Save and Open Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>These three examples demonstrate how the <legacyLink xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save</legacyLink> and <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> methods can be used together.</para>
    <para>Assume that you are going on a business trip and want to take along a table from a database. Before you go, you access the data as a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and save it in a transportable form. When you arrive at your destination, you access the <legacyBold>Recordset</legacyBold> as a local, disconnected <legacyBold>Recordset</legacyBold>. You make changes to the <legacyBold>Recordset</legacyBold>, and then save it again. Finally, when you return home, you connect to the database again and update it with the changes you made on the road.</para>
    <para>First, access and save the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table.</para>
    <code>'BeginSaveVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
    
Public Sub Main()
    On Error GoTo ErrorHandler

    'recordset and connection variables
    Dim rstAuthors As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLAuthors As String
     
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    Set rstAuthors = New ADODB.Recordset
    strSQLAuthors = "SELECT au_id, au_lname, au_fname, city, phone FROM Authors"
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenDynamic, adLockOptimistic, adCmdText
     
    'For sake of illustration, save the Recordset to a diskette in XML format
    rstAuthors.Save "c:\Pubs.xml", adPersistXML

    ' clean up
    rstAuthors.Close
    Cnxn.Close
    Set rstAuthors = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    'clean up
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
'EndSaveVB</code>
    <para>At this point, you have arrived at your destination. You will access the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table as a local, disconnected <legacyBold>Recordset</legacyBold>. You must have the <legacyBold>MSPersist</legacyBold> provider on the computer that you are using to access the saved file, a:\Pubs.xml.</para>
    <code>Attribute VB_Name = "Save"</code>
    <para>Finally, you return home. Now update the database with your changes.</para>
    <code>Attribute VB_Name = "Save"</code>
  </introduction>
  <relatedTopics>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="a9b287f5-04b0-4514-8143-f67879ca9842">Recordset Persistence</link>
<link xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>