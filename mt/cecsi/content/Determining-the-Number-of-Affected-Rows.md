---
title: Determining the Number of Affected Rows
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Determining the Number of Affected Rows
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>After an application updates, deletes, or inserts rows, it can call <legacyBold>SQLRowCount</legacyBold> to determine how many rows were affected. <legacyBold>SQLRowCount</legacyBold> returns this value whether or not the rows were updated, deleted, or inserted by executing an <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, or <legacyBold>INSERT</legacyBold> statement, by executing a positioned update or delete statement, or by calling <legacyBold>SQLSetPos</legacyBold>.</para>
    <para>If a batch of SQL statements is executed, the count of affected rows might be a total count for all statements in the batch or individual counts for each statement in the batch. For more information, see <legacyLink xlink:href="766488cc-450c-434c-9c88-467f6c57e17c">Batches of SQL Statements</legacyLink> and <legacyLink xlink:href="a3c32e4b-8fe7-4a33-ae39-ae664001f315">Multiple Results</legacyLink>.</para>
    <para>The number of affected rows is also returned in the SQL_DIAG_ROW_COUNT diagnostic header field in the diagnostic area associated with the statement handle. However, the data in this field is reset after every function call on the same statement handle, whereas the value returned by <legacyBold>SQLRowCount</legacyBold> remains the same until a call to <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLPrepare</legacyBold>, or <legacyBold>SQLSetPos</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>