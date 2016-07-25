---
title: "Resync Command Property-Dynamic (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
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
# Resync Command Property-Dynamic (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies a user-supplied command string that the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method issues to refresh the data in the table named in the <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Table</legacyLink> dynamic property.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value which is a command string.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object is the result of a JOIN operation executed on multiple base tables. The rows affected depend on the <legacyItalic>AffectRecords</legacyItalic> parameter of the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method. The standard <legacyBold>Resync</legacyBold> method is executed if the <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Table</legacyLink> and <legacyBold>Resync Command</legacyBold> properties are not set.</para>
      <para>The command string of the <legacyBold>Resync Command</legacyBold> property is a parameterized command or stored procedure that uniquely identifies the row being refreshed, and returns a single row containing the same number and order of columns as the row to be refreshed. The command string contains a parameter for each primary key column in the <legacyBold>Unique Table</legacyBold>; otherwise, a run-time error is returned. The parameters are automatically filled in with primary key values from the row to be refreshed.</para>
      <para>Here are two examples based on SQL:</para>
      <para>1) The <legacyBold>Recordset</legacyBold> is defined by a command:</para>
      <code>SELECT * FROM Customers JOIN Orders ON 
   Customers.CustomerID = Orders.CustomerID
   WHERE city = 'Seattle'
   ORDER BY CustomerID</code>
      <para>The <legacyBold>Resync Command</legacyBold> property is set to:</para>
      <code>"SELECT * FROM 
   (SELECT * FROM Customers JOIN Orders 
   ON Customers.CustomerID = Orders.CustomerID
   city = 'Seattle' ORDER BY CustomerID)
WHERE Orders.OrderID = ?"</code>
      <para>The <legacyBold>Unique Table</legacyBold> is <legacyItalic>Orders</legacyItalic> and its primary key, <legacyItalic>OrderID</legacyItalic>, is parameterized. The sub-select provides a simple way to programmatically ensure that the same number and order of columns are returned as by the original command.</para>
      <para>2) The <legacyBold>Recordset</legacyBold> is defined by a stored procedure:</para>
      <code>CREATE PROC Custorders @CustomerID char(5) AS 
SELECT * FROM Customers JOIN Orders ON 
Customers.CustomerID = Orders.CustomerID 
WHERE Customers.CustomerID = @CustomerID</code>
      <para>The <legacyBold>Resync</legacyBold> method should execute the following stored procedure:</para>
      <code>CREATE PROC CustordersResync @ordid int AS 
SELECT * FROM Customers JOIN Orders ON 
Customers.CustomerID = Orders.CustomerID
WHERE Orders.ordid  = @ordid</code>
      <para>The <legacyBold>Resync Command</legacyBold> property is set to:</para>
      <code>"{call CustordersResync (?)}"</code>
      <para>Once again, the <legacyBold>Unique Table</legacyBold> is <legacyItalic>Orders</legacyItalic> and its primary key, <legacyItalic>OrderID</legacyItalic>, is parameterized.</para>
      <para>
        <legacyBold>Resync Command</legacyBold> is a dynamic property appended to the <legacyBold>Recordset</legacyBold> object <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection when the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property is set to <legacyBold>adUseClient</legacyBold>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>