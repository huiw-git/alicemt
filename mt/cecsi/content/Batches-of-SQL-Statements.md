---
title: Batches of SQL Statements
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 766488cc-450c-434c-9c88-467f6c57e17c
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Batches of SQL Statements
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A batch of SQL statements is a group of two or more SQL statements or a single SQL statement that has the same effect as a group of two or more SQL statements. In some implementations, the entire batch statement is executed before any results are available. This is often more efficient than submitting statements separately, because network traffic can often be reduced and the data source can sometimes optimize execution of a batch of SQL statements. In other implementations, calling <legacyBold>SQLMoreResults</legacyBold> triggers the execution of the next statement in the batch. ODBC supports the following types of batches:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Explicit Batches</legacyBold> An <legacyItalic>explicit batch</legacyItalic> is two or more SQL statements separated by semicolons (;). For example, the following batch of SQL statements opens a new sales order. This requires inserting rows into both the Orders and Lines tables. Note that there is no semicolon after the last statement. </para>
        <code>INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)
   VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');
INSERT INTO Lines (OrderID, Line, PartID, Quantity)
   VALUES (2002, 1, 1234, 10);
INSERT INTO Lines (OrderID, Line, PartID, Quantity)
   VALUES (2002, 2, 987, 8);
INSERT INTO Lines (OrderID, Line, PartID, Quantity)
   VALUES (2002, 3, 566, 17);
INSERT INTO Lines (OrderID, Line, PartID, Quantity)
   VALUES (2002, 4, 412, 500)</code>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Procedures</legacyBold> If a procedure contains more than one SQL statement, it is considered to be a batch of SQL statements. For example, the following SQL Server–specific statement creates a procedure that returns a result set containing information about a customer and a result set listing all the open sales orders for that customer: </para>
        <code>CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS
   SELECT * FROM Customers WHERE CustID = @CustomerID
   SELECT OrderID FROM Orders
      WHERE CustID = @CustomerID AND Status = 'OPEN'</code>
        <para>The <legacyBold>CREATE PROCEDURE</legacyBold> statement itself is not a batch of SQL statements. However, the procedure it creates is a batch of SQL statements. No semicolons separate the two <legacyBold>SELECT</legacyBold> statements because the <legacyBold>CREATE PROCEDURE</legacyBold> statement is specific to SQL Server, and SQL Server does not require semicolons to separate multiple statements in a <legacyBold>CREATE PROCEDURE</legacyBold> statement. </para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Arrays of Parameters</legacyBold> Arrays of parameters can be used with a parameterized SQL statement as an effective way to perform bulk operations. For example, arrays of parameters can be used with the following <legacyBold>INSERT</legacyBold> statement to insert multiple rows into the Lines table while executing only a single SQL statement: </para>
        <code>INSERT INTO Lines (OrderID, Line, PartID, Quantity)
   VALUES (?, ?, ?, ?)</code>
        <para>If a data source does not support arrays of parameters, the driver can emulate them by executing the SQL statement once for each set of parameters. For more information, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink> and <legacyLink xlink:href="9b572c5b-1dfe-40af-bebd-051548ab6d90">Arrays of Parameter Values</legacyLink>, later in this section. </para>
      </listItem>
    </list>
    <para>The different types of batches cannot be mixed in an interoperable manner. That is, how an application determines the result of executing an explicit batch that includes procedure calls, an explicit batch that uses arrays of parameters, and a procedure call that uses arrays of parameters is driver-specific.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="2f3475d1-3999-4dd8-aba2-a6e1299c95f8">Result-Generating and Result-Free Statements</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f082c717-4f82-4820-a2fa-ba607d8fd872">Executing Batches</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="6debd41d-9f4c-4f4c-a44b-2993da5306f0">Errors and Batches</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>