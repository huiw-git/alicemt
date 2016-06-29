---
title: Driver Tasks
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
translation.priority.ht: 
  - en-gb
---
# Driver Tasks
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specific tasks performed by drivers include:  </para>
    <list class="bullet">
      <listItem>
        <para>Connecting to and disconnecting from the data source.</para>
      </listItem>
      <listItem>
        <para>Checking for function errors not checked by the Driver Manager.</para>
      </listItem>
      <listItem>
        <para>Initiating transactions; this is transparent to the application.</para>
      </listItem>
      <listItem>
        <para>Submitting SQL statements to the data source for execution. The driver must modify ODBC SQL to DBMS-specific SQL; this is often limited to replacing escape clauses defined by ODBC with DBMS-specific SQL.</para>
      </listItem>
      <listItem>
        <para>Sending data to and retrieving data from the data source, including converting data types as specified by the application.</para>
      </listItem>
      <listItem>
        <para>Mapping DBMS-specific errors to ODBC SQLSTATEs.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>