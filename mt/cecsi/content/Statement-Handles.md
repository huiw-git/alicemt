---
title: Statement Handles
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65d6d78b-a8c8-489a-9dad-f8d127a44882
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Statement Handles
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>statement</legacyItalic> is most easily thought of as an SQL statement, such as <legacyBold>SELECT * FROM Employee</legacyBold>. However, a statement is more than just an SQL statement — it consists of all of the information associated with that SQL statement, such as any result sets created by the statement and parameters used in the execution of the statement. A statement does not even need to have an application-defined SQL statement. For example, when a catalog function such as <legacyBold>SQLTables</legacyBold> is executed on a statement, it executes a predefined SQL statement that returns a list of table names.</para>
    <para>Each statement is identified by a statement handle. A statement is associated with a single connection, and there can be multiple statements on that connection. Some drivers limit the number of active statements they support; the SQL_MAX_CONCURRENT_ACTIVITIES option in <legacyBold>SQLGetInfo</legacyBold> specifies how many active statements a driver supports on a single connection. A statement is defined to be <legacyItalic>active</legacyItalic> if it has results pending, where results are either a result set or the count of rows affected by an <legacyBold>INSERT</legacyBold>, <legacyBold>UPDATE</legacyBold>, or <legacyBold>DELETE</legacyBold> statement, or data is being sent with multiple calls to <legacyBold>SQLPutData</legacyBold>.</para>
    <para>Within a piece of code that implements ODBC (the Driver Manager or a driver), the statement handle identifies a structure that contains statement information, such as:  </para>
    <list class="bullet">
      <listItem>
        <para>The statement's state</para>
      </listItem>
      <listItem>
        <para>The current statement-level diagnostics</para>
      </listItem>
      <listItem>
        <para>The addresses of the application variables bound to the statement's parameters and result set columns</para>
      </listItem>
      <listItem>
        <para>The current settings of each statement attribute</para>
      </listItem>
    </list>
    <para>Statement handles are used in most ODBC functions. Notably, they are used in the functions to bind parameters and result set columns (<legacyBold>SQLBindParameter</legacyBold> and <legacyBold>SQLBindCol</legacyBold>), prepare and execute statements (<legacyBold>SQLPrepare</legacyBold>, <legacyBold>SQLExecute</legacyBold>, and <legacyBold>SQLExecDirect</legacyBold>), retrieve metadata (<legacyBold>SQLColAttribute</legacyBold> and <legacyBold>SQLDescribeCol</legacyBold>), fetch results (<legacyBold>SQLFetch</legacyBold>), and retrieve diagnostics (<legacyBold>SQLGetDiagField</legacyBold> and <legacyBold>SQLGetDiagRec</legacyBold>). They are also used in catalog functions (<legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLTables</legacyBold>, and so on) and a number of other functions.</para>
    <para>Statement handles are allocated with <legacyBold>SQLAllocHandle</legacyBold> and freed with <legacyBold>SQLFreeHandle</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>