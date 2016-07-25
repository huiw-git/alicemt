---
title: "ConnectionString, ConnectionTimeout, and State Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4de7336a-b5ea-43f1-b750-5fa302b5b756
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
# ConnectionString, ConnectionTimeout, and State Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates different ways of using the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to open a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. It also uses the <legacyLink xlink:href="8904a403-1383-4b4b-b53d-5c01d6f5deac">ConnectionTimeout</legacyLink> property to set a connection timeout period, and the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property to check the state of the connections. The GetState function is required for this procedure to run.</para>
    <alert class="note">
      <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
    </alert>
    <code>'BeginConnectionStringVB

    'To integrate this code replace
    'the database, DSN or Data Source values
    
Public Sub Main()
    On Error GoTo ErrorHandler

    Dim Cnxn1 As ADODB.Connection
    Dim Cnxn2 As ADODB.Connection
    Dim Cnxn3 As ADODB.Connection
    Dim Cnxn4 As ADODB.Connection
    
     ' Open a connection without using a Data Source Name (DSN)
    Set Cnxn1 = New ADODB.Connection
    Cnxn1.ConnectionString = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn1.Open
    MsgBox "Cnxn1 state: " &amp; GetState(Cnxn1.State)
    
     ' Open a connection using a DSN and ODBC tags
     ' It is assumed that you have created DSN 'Pubs' with a user name as
     ' 'MyUserId' and password as 'MyPassword'.
    Set Cnxn2 = New ADODB.Connection
    Cnxn2.ConnectionString = "Data Source='Pubs';" &amp; _
        "User ID='MyUserId';Password='MyPassword';"
    Cnxn2.ConnectionTimeout = 30
    Cnxn2.Open
    MsgBox "Cnxn2 state: " &amp; GetState(Cnxn2.State)
    
     ' Open a connection using a DSN and OLE DB tags
     ' It is assumed that you have created DSN 'Pubs1' with windows authentication.
    Set Cnxn3 = New ADODB.Connection
    Cnxn3.ConnectionString = "Data Source='Pubs1';"
    Cnxn3.Open
    MsgBox "Cnxn2 state: " &amp; GetState(Cnxn3.State)
    
     ' Open a connection using a DSN and individual
     ' arguments instead of a connection string
     ' It is assumed that you have created DSN 'Pubs' with a user name as
     ' 'MyUserId' and password as 'MyPassword'.
    Set Cnxn4 = New ADODB.Connection
    Cnxn4.Open "Pubs", "MyUserId", "MyPassword"
    MsgBox "Cnxn4 state: " &amp; GetState(Cnxn4.State)
       
    ' clean up
    Cnxn1.Close
    Cnxn2.Close
    Cnxn3.Close
    Cnxn4.Close
    Set Cnxn1 = Nothing
    Set Cnxn2 = Nothing
    Set Cnxn3 = Nothing
    Set Cnxn4 = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
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
    
    If Not Cnxn4 Is Nothing Then
        If Cnxn4.State = adStateOpen Then Cnxn4.Close
    End If
    Set Cnxn4 = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub

Public Function GetState(intState As Integer) As String

   Select Case intState
      Case adStateClosed
         GetState = "adStateClosed"
      Case adStateOpen
         GetState = "adStateOpen"
   End Select

End Function
'EndConnectionStringVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString Property</link>
<link xlink:href="8904a403-1383-4b4b-b53d-5c01d6f5deac">ConnectionTimeout Property</link>
<link xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>