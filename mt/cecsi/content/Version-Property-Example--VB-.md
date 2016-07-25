---
title: "Version Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 708efd50-2905-4168-b7e4-91b2e9b23539
caps.latest.revision: 10
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
# Version Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="db4cb894-9bd9-422d-a58a-cef6941a5784">Version</legacyLink> property of a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object to display the current ADO version. It also uses several dynamic properties to show:  </para>
    <list class="bullet">
      <listItem>
        <para>the current DBMS name and version.</para>
      </listItem>
      <listItem>
        <para>OLE DB version.</para>
      </listItem>
      <listItem>
        <para>             provider name and version.</para>
      </listItem>
      <listItem>
        <para>             ODBC version.</para>
      </listItem>
      <listItem>
        <para>ODBC driver name and version.</para>
      </listItem>
    </list>
    <code>'BeginVersionVB
Public Sub Main()
    On Error GoTo ErrorHandler

    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strVersionInfo As String
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    strVersionInfo = "ADO Version: " &amp; Cnxn.Version &amp; vbCr
    strVersionInfo = strVersionInfo &amp; "DBMS Name: " &amp; Cnxn.Properties("DBMS Name") &amp; vbCr
    strVersionInfo = strVersionInfo &amp; "DBMS Version: " &amp; Cnxn.Properties("DBMS Version") &amp; vbCr
    strVersionInfo = strVersionInfo &amp; "OLE DB Version: " &amp; Cnxn.Properties("OLE DB Version") &amp; vbCr
    strVersionInfo = strVersionInfo &amp; "Provider Name: " &amp; Cnxn.Properties("Provider Name") &amp; vbCr
    strVersionInfo = strVersionInfo &amp; "Provider Version: " &amp; Cnxn.Properties("Provider Version") &amp; vbCr
    
    MsgBox strVersionInfo

    ' clean up
    Cnxn.Close
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndVersionVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="db4cb894-9bd9-422d-a58a-cef6941a5784">Version Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>