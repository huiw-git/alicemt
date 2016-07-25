---
title: "Editing Data"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef514f85-c446-4f05-824e-c9313b2ffae1
caps.latest.revision: 15
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
# Editing Data
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>We have explained how use ADO to connect to a data source, execute a command, get the results in a <legacyBold>Recordset</legacyBold> object, and navigate within the <legacyBold>Recordset</legacyBold>. This section focuses on the next fundamental ADO operation: editing data.</para>
    <para>This section continues to use the sample <legacyBold>Recordset</legacyBold> introduced in <legacyLink xlink:href="de1d74af-89b6-4f3f-a8c9-07c3e2b3c9a5">Examining Data</legacyLink>, with one important change. The following code is used to open the <legacyBold>Recordset</legacyBold>: </para>
    <code>'BeginEditIntro
    Dim strSQL As String
    Dim objRs1 As ADODB.Recordset
    
    strSQL = "SELECT * FROM Shippers"
    
    Set objRs1 = New ADODB.Recordset
    
    objRs1.Open strSQL, GetNewConnection, adOpenStatic, _
                adLockBatchOptimistic, adCmdText
    
    ' Disconnect the Recordset from the Connection object.
    Set objRs1.ActiveConnection = Nothing
'EndEditIntro</code>
    <para>The important change to the code involves setting the <legacyBold>CursorLocation</legacyBold> property of the <legacyBold>Connection</legacyBold> object equal to <legacyBold>adUseClient</legacyBold> in the <legacyItalic>GetNewConnection</legacyItalic> function (shown in the next example), which indicates the use of a client cursor. For more information about the differences between client-side and server-side cursors, see <legacyLink xlink:href="c1b7d7e6-1707-4ce2-863f-0c6dea967df6">Understanding Cursors and Locks</legacyLink>.</para>
    <para>The <legacyBold>CursorLocation</legacyBold> property's <legacyBold>adUseClient</legacyBold> setting moves the location of the cursor from the data source (the SQL Server, in this case) to the location of the client code (the desktop workstation). This setting forces ADO to invoke the Client Cursor Engine for OLE DB on the client in order to create and manage the cursor.</para>
    <para>You might also have noticed that the <legacyBold>LockType</legacyBold> parameter of the <legacyBold>Open</legacyBold> method changed to <legacyBold>adLockBatchOptimistic</legacyBold>. This opens the cursor in batch mode. (The provider caches multiple changes and writes them to the underlying data source only when you call the <legacyBold>UpdateBatch</legacyBold> method.) Changes that were made to the <legacyBold>Recordset</legacyBold> will not be updated in the database until the <legacyBold>UpdateBatch</legacyBold> method is called.</para>
    <para>Finally, the code in this section uses a modified version of the GetNewConnection function. This version of the function now returns a client-side cursor. The function looks like this:</para>
    <code>'BeginNewConnection
Public Function GetNewConnection() As ADODB.Connection
    On Error GoTo ErrHandler:
    
    Dim objConn As New ADODB.Connection
    Dim strConnStr As String
    
    strConnStr = "Provider='SQLOLEDB';Initial Catalog='Northwind';" &amp; _
                 "Data Source='MySqlServer';Integrated Security='SSPI';"
             
    objConn.ConnectionString = strConnStr
    objConn.CursorLocation = adUseClient
    objConn.Open
    
    Set GetNewConnection = objConn
    
    Exit Function
    
ErrHandler:
    Set objConn = Nothing
    Set GetNewConnection = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Function
'EndNewConnection</code>
    <para>This section contains the following topics.</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="17ce1263-5897-452a-9ea5-c7f96b33df65">Editing Existing Records</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="dd34669e-6f06-403b-9241-1c85c82aecc2">Adding Records</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="65090cba-6d46-4775-8d61-f6838e7752a6">Determining What is Supported</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="bfed5cfa-7f57-463b-9da2-0c612a079d30">Deleting Records Using the Delete Method</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="8b528b23-063d-45ea-8dea-6a90d4060b20">Alternatives: Using SQL Statements</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>