---
title: Errors and Batches
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
translation.priority.ht: 
  - en-gb
---
# Errors and Batches
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an error occurs while executing a batch of SQL statements, one of the following four outcomes are possible. (Each possible outcome is data source–specific and might even depend on the statements included in the batch.)  </para>
    <list class="bullet">
      <listItem>
        <para>No statements in the batch are executed.</para>
      </listItem>
      <listItem>
        <para>No statements in the batch are executed and the transaction is rolled back.</para>
      </listItem>
      <listItem>
        <para>All of the statements before the error statement are executed.</para>
      </listItem>
      <listItem>
        <para>All of the statements except the error statement are executed.</para>
      </listItem>
    </list>
    <para>In the first two cases, <legacyBold>SQLExecute</legacyBold> and <legacyBold>SQLExecDirect</legacyBold> return SQL_ERROR. In the latter two cases, they may return SQL_SUCCESS_WITH_INFO or SQL_SUCCESS, depending on the implementation. In all cases, further error information can be retrieved with <legacyBold>SQLGetDiagField</legacyBold>, <legacyBold>SQLGetDiagRec</legacyBold>, or <legacyBold>SQLError</legacyBold>. However, the nature and depth of this information is data source–specific. Furthermore, this information is unlikely to exactly identify the statement in error.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>