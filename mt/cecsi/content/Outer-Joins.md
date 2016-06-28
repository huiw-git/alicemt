---
title: Outer Joins
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
translation.priority.ht: 
  - en-gb
---
# Outer Joins
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC supports the SQL-92 left, right, and full outer join syntax. The escape sequence for outer joins is</para>
    <para>         <legacyBold>{oj</legacyBold> <legacyItalic>outer-join</legacyItalic><legacyBold>}</legacyBold></para>
    <para>where <legacyItalic>outer-join</legacyItalic> is</para>
    <para>         <legacyItalic>table-reference</legacyItalic> {<legacyBold>LEFT | RIGHT | FULL} OUTER JOIN</legacyBold>      {<legacyItalic>table-reference</legacyItalic> | <legacyItalic>outer-join</legacyItalic>} <legacyBold>ON</legacyBold> <legacyItalic>search-condition</legacyItalic></para>
    <para>         <legacyItalic>table-reference</legacyItalic> specifies a table name, and <legacyItalic>search-condition</legacyItalic> specifies the join condition between the <legacyItalic>table-references</legacyItalic>.</para>
    <para>An outer join request must appear after the <legacyBold>FROM</legacyBold> keyword and before the <legacyBold>WHERE</legacyBold> clause (if one exists). For complete syntax information, see <legacyLink xlink:href="2cfd1525-6677-4d36-9b9e-730496853750">Outer Join Escape Sequence</legacyLink> in Appendix C: SQL Grammar.</para>
    <para>For example, the following SQL statements create the same result set that lists all customers and shows which has open orders. The first statement uses the escape-sequence syntax. The second statement uses the native syntax for Oracle and is not interoperable.</para>
    <code>SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}
   WHERE Orders.Status='OPEN'

SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status
   FROM Customers, Orders
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))</code>
    <para>To determine the types of outer joins that a data source and driver support, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_OJ_CAPABILITIES flag. The types of outer joins that might be supported are left, right, full, or nested outer joins; outer joins in which the column names in the <legacyBold>ON</legacyBold> clause do not have the same order as their respective table names in the <legacyBold>OUTER JOIN </legacyBold>clause; inner joins in conjunction with outer joins; and outer joins using any ODBC comparison operator. If the SQL_OJ_CAPABILITIES information type returns 0, no outer join clause is supported.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>