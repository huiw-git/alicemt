---
title: "Calling a Stored Procedure as a Method on a Connection object"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35ffdb79-a931-4271-a3bb-0cd804cf173e
caps.latest.revision: 12
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
# Calling a Stored Procedure as a Method on a Connection object
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can call a stored procedure as if it were a native method on the associated open <legacyBold>Connection</legacyBold> object. This is similar to calling a named command on the <legacyBold>Connection</legacyBold> object. </para>
    <para>The following Visual Basic code example calls a stored procedure in the Northwind sample database, called CustOrdersOrders, which is listed here again for your convenience.</para>
    <code>CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS
SELECT OrderID, OrderDate, RequiredDate, ShippedDate
FROM Orders
WHERE CustomerID = @CustomerID
ORDER BY OrderID</code>
    <para>The following code example demonstrates how to call a stored procedure as if it were a native method on an associated open <legacyBold>Connection</legacyBold> object.</para>
    <code>    Const DS = "MySQLServer"
    Const DB = "Northwind"
    Const DP = "SQLOLEDB"
    
    Dim objConn As New ADODB.Connection
    Dim objRs As New ADODB.Recordset
    Dim objComm As New ADODB.Command
    
    ConnectionString = "Provider=" &amp; DP &amp; _
                       ";Data Source=" &amp; DS &amp; _
                       ";Initial Catalog=" &amp; DB &amp; _
                       ";Integrated Security=SSPI;"
    
    ' Connect to the data source.
    objConn.Open ConnectionString
    
    ' Set a stored procedure

    Set objComm.ActiveConnection = objConn

    ' Execute the stored procedure on
    ' the active connection object...
    '    "ALFKI" is the required input parameter,
    '    objRs is the resultant output variable.

    
    ' Display the result.
    Debug.Print "Results returned from sp_CustOrdersOrders for ALFKI: "
    Do While Not objRs.EOF
        Debug.Print vbTab &amp; objRs(0) &amp; vbTab &amp; objRs(1) &amp; vbTab &amp; _
                    objRs(2) &amp; vbTab &amp; objRs(3)
        objRs.MoveNext
     Loop
    
    'Clean up.
    objRs.Close
    objConn.Close
    Set objRs = Nothing
    Set objConn = Nothing
    Set objComm = Nothing</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object (ADO)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>