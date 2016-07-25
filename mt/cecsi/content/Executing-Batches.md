---
title: "Executing Batches"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Executing Batches
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Before an application executes a batch of statements, it should first check whether they are supported. To do this, the application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS, and SQL_PARAM_ARRAY_SELECTS options. The first option returns whether row count–generating and result set–generating statements are supported in explicit batches and procedures, while the latter two options return information about the availability of row counts and result sets in parameterized execution.</para>
    <para>Batches of statements are executed through <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>. For example, the following call executes an explicit batch of statements to open a new sales order.</para>
    <code>SQLCHAR *BatchStmt =
   "INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)"
      "VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');"
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 1, 1234, 10);"
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 2, 987, 8);"
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 3, 566, 17);"
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 4, 412, 500)";

SQLExecDirect(hstmt, BatchStmt, SQL_NTS);</code>
    <para>When a batch of result-generating statements is executed, it returns one or more row counts or result sets. For information about how to retrieve these, see <legacyLink xlink:href="a3c32e4b-8fe7-4a33-ae39-ae664001f315">Multiple Results</legacyLink>.</para>
    <para>If a batch of statements includes parameter markers, these are numbered in increasing parameter order as they are in any other statement. For example, the following batch of statements has parameters numbered from 1 through 21; those in the first <legacyBold>INSERT</legacyBold> statement are numbered 1 through 5 and those in the last <legacyBold>INSERT</legacyBold> statement are numbered 18 through 21.</para>
    <code>INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)
   VALUES (?, ?, ?, ?, ?);
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);</code>
    <para>For more information about parameters, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>, later in this section.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>