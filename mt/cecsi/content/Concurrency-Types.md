---
title: Concurrency Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Concurrency Types
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To solve the problem of reduced concurrency in cursors, ODBC exposes four different types of cursor concurrency:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Read-only</legacyBold> The cursor can read data but cannot update or delete data. This is the default concurrency type. Although the DBMS might lock rows to enforce the Repeatable Read and Serializable isolation levels, it can use read locks instead of write locks. This results in higher concurrency because other transactions can at least read the data.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Locking</legacyBold> The cursor uses the lowest level of locking necessary to make sure it can update or delete rows in the result set. This usually results in very low concurrency levels, especially at the Repeatable Read and Serializable transaction isolation levels.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Optimistic concurrency using row versions</legacyBold> <legacyBold>and</legacyBold> <legacyBold>optimistic concurrency using values</legacyBold> The cursor uses optimistic concurrency: It updates or deletes rows only if they have not changed since they were last read. To detect changes, it compares row versions or values. There is no guarantee that the cursor will be able to update or delete a row, but concurrency is much higher than when locking is used. For more information, see the following section, <legacyLink xlink:href="9d71e09e-bc68-4c1f-9229-ed2a7be7d324">Optimistic Concurrency</legacyLink>.</para>
      </listItem>
    </list>
    <para>An application specifies what type of concurrency it wants the cursor to use with the SQL_ATTR_CONCURRENCY statement attribute. To determine what types are supported, it calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_SCROLL_CONCURRENCY option.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>