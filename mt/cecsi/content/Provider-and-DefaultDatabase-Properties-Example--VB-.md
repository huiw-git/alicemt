---
title: "Provider and DefaultDatabase Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 677e1dbe-bcf6-4028-a62c-e99b1c88bf7b
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
# Provider and DefaultDatabase Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property by opening three <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> objects using different providers. It also uses the <legacyLink xlink:href="41e8a8dd-e69c-4a09-8736-93502e01961c">DefaultDatabase</legacyLink> property to set the default database for the Microsoft ODBC Provider.</para>
    <alert class="note">
      <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
    </alert>
    <code>'BeginProviderVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection strings

Public Sub Main()
    On Error GoTo ErrorHandler

    Dim Cnxn1 As ADODB.Connection
    Dim Cnxn2 As ADODB.Connection
    Dim Cnxn3 As ADODB.Connection
    Dim strCnxn As String
    
    ' Open a connection using the Microsoft ODBC provider
    Set Cnxn1 = New ADODB.Connection
    Cnxn1.ConnectionString = "driver={SQL Server};server='MySqlServer';" &amp; _
        "user id='MyUserID';password='MyPassword';"
    Cnxn1.Open strCnxn
    Cnxn1.DefaultDatabase = "Pubs"
   
    ' Display the provider
    MsgBox "Cnxn1 provider: " &amp; Cnxn1.Provider
    
    ' Open a connection using the Microsoft Jet provider
    Set Cnxn2 = New ADODB.Connection
    Cnxn2.Provider = "Microsoft.Jet.OLEDB.4.0"
    Cnxn2.Open "Northwind.mdb", _
        "MyUserID", "MyPassword"

    ' Display the provider.
    MsgBox "Cnxn2 provider: " &amp; Cnxn2.Provider
    
    ' Open a connection using the Microsoft SQL Server provider
    Set Cnxn3 = New ADODB.Connection
    Cnxn3.Provider = "sqloledb"
    Cnxn3.Open "Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    
    ' Display the provider
    MsgBox "Cnxn3 provider: " &amp; Cnxn3.Provider

    ' clean up
    Cnxn1.Close
    Cnxn2.Close
    Cnxn3.Close
    Set Cnxn1 = Nothing
    Set Cnxn2 = Nothing
    Set Cnxn3 = Nothing
    Exit Sub
    
ErrorHandler:
    If Not Cnxn1 Is Nothing Then
        If Cnxn1.State = adStateOpen Then Cnxn1.Close
    End If
    Set Cnxn1 = Nothing
    
    If Not Cnxn2 Is Nothing Then
        If Cnxn2.State = adStateOpen Then Cnxn2.Close
    End If
    Set Cnxn2 = Nothing
    
    If Not Cnxn3 Is Nothing Then
        If Cnxn3.State = adStateOpen Then Cnxn3.Close
    End If
    Set Cnxn3 = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
'EndProviderVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="41e8a8dd-e69c-4a09-8736-93502e01961c">DefaultDatabase Property</link>
<link xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>