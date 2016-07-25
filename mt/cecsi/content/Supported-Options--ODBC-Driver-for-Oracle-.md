---
title: "Supported Options (ODBC Driver for Oracle)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: feefe0fd-5679-4c42-aa9e-e52b83f02544
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Supported Options (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The ODBC Driver for Oracle supports the following options for the SQLGetConnectOption( ) and SQLSetConnectOption( ) Level 1 functions:  </para>
    <list class="bullet">
      <listItem>
        <para>SQL_ACCESS_MODE (<legacyLink xlink:href="98cced6f-41b8-43c1-a3cd-f4ea1615c0af">SQLGetConnectOption</legacyLink>( ) only)</para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">SQL_AUTOCOMMIT</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">SQL_ODBC_CURSORS</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">SQL_OPT_TRACEFILE</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">SQL_OPT_TRACE</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">SQL_TRANSLATE_DLL</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">SQL_TRANSLATE_OPTION</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">SQL_TXN_ISOLATION</legacyLink>
        </para>
      </listItem>
    </list>
    <para>The ODBC Driver for Oracle supports the following options for the SQLGetStmtOption( ) and SQLSetStmtOption( ) Level 1 functions:</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="cd73b769-c8b5-43e0-9f80-b3011b7a6162">SQL_BIND_TYPE</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="cd73b769-c8b5-43e0-9f80-b3011b7a6162">SQL_CONCURRENCY</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="cd73b769-c8b5-43e0-9f80-b3011b7a6162">SQL_CURSOR_TYPE</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="cd73b769-c8b5-43e0-9f80-b3011b7a6162">SQL_KEYSET_SIZE</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="cd73b769-c8b5-43e0-9f80-b3011b7a6162">SQL_MAX_ROWS</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="cd73b769-c8b5-43e0-9f80-b3011b7a6162">SQL_ROWSET_SIZE</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>