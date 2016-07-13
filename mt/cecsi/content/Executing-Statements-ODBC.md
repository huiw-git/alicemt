---
title: Executing Statements ODBC
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09063f43-f5f0-4cf0-baa9-12fec8898997
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Executing Statements ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC applications perform almost all database access by executing SQL statements. The general sequence of events is to allocate a statement handle, set any statement attributes, execute the statement, retrieve any results, and free the statement handle.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="4ce3b446-34ab-46dc-96e5-f40ec95c267e">Allocating a Statement Handle</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="4c59cd8e-a713-4095-9065-20d5bdeafe43">Statement Attributes</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e5f0d2ee-0453-4faf-b007-12978dd300a1">Executing a Statement</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution (Polling Method)</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="e509dad9-5263-4a10-9a4e-03b84b66b6b3">Asynchronous Execution (Notification Method)</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="ee18e2f1-2690-4cc1-9e5c-e20244e5d480">Freeing a Statement Handle</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>