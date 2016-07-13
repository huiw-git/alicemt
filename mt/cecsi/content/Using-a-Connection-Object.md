---
title: Using a Connection Object
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b34f971-5699-43e7-9b15-137d334fa66e
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
# Using a Connection Object
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Before opening a <legacyBold>Connection</legacyBold> object, you must define certain information about the data source and type of connection. Most of this information is held by the <legacyItalic>ConnectionString</legacyItalic> parameter of the <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open method</legacyLink> on the <legacyBold>Connection</legacyBold> object, or by the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString property</legacyLink> on the <legacyBold>Connection</legacyBold> object. A connection string consists of a list of argument/value pairs separated by semi-colons, with the values enclosed within single quotes. For example:</para>
    <code>Dim sConn As String
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" &amp; _
             "Initial Catalog='Northwind';Integrated Security='SSPI';"</code>
    <alert class="note">
      <para>You can also specify an ODBC Data Source Name (DSN) or a Data Link (UDL) file in a connection string. For more information about DSNs, see <legacyLink xlink:href="67cc4945-4850-4eb4-8da6-b835ddaeca4c">Managing Data Sources</legacyLink> in the ODBC Programmer's Reference. For more information about UDLs, see <legacyLink xlink:href="95c180ea-bd4f-4dca-b95a-576afd135bbc">Data Link API Overview</legacyLink> in the OLE DB Programmer's Reference.</para>
    </alert>
    <para>Typically, you establish a connection by calling the <legacyBold>Connection.Open</legacyBold> method with an appropriate a <legacyItalic>connection string</legacyItalic> as its parameter. An example is shown in the following Visual Basic code snippet:</para>
    <code>Dim oConn As ADODB.Connection
Dim oRs As ADODB.Recordset
Dim sConn As String
Dim sSQL as String



' Open a connection.
Set oConn = New ADODB.Connection
.Open 

' Make a query over the connection.
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " &amp; _
             "FROM Products"
Set oRs = New ADODB.Recordset
oRs.Open sSQL, , adOpenStatic, adLockBatchOptimistic, adCmdText
                      
MsgBox oRs.RecordCount
        
' Close the connection.
oConn.Close
Set oConn = Nothing
    </code>
    <para>Here <legacyBold>oRs.Open</legacyBold> takes a <legacyBold>Connection</legacyBold> object (<legacyItalic>oConn</legacyItalic>) variable as the value of its <legacyItalic>ActiveConnection</legacyItalic> parameter. Also, the <legacyBold>Connection.CursorLocation</legacyBold> property assumes the default value of <legacyBold>adUseServer</legacyBold>. Contrast this to the <legacyLink xlink:href="de4bcd56-dac2-45e6-95ab-9fd7f25878fc">HelloData</legacyLink> example in the preceding section. The following instruction would result in run-time errors. </para>
    <code>oRs.MarshalOptions = adMarshalModifiedOnly
' Disconnect the Recordset.
Set oRs.ActiveConnection = Nothing</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>