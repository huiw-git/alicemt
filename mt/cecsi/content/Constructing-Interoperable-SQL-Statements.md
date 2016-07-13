---
title: Constructing Interoperable SQL Statements
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dee6f7e2-bcc4-4c74-8c7c-12aeda8a90eb
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Constructing Interoperable SQL Statements
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>As mentioned in the previous sections, interoperable applications should use the ODBC SQL grammar. Beyond using this grammar, however, a number of additional problems are faced by interoperable applications. For example, what does an application do if it wants to use a feature, such as outer joins, that is not supported by all data sources?</para>
    <para>At this point, the application writer must make some decisions about which language features are required and which are optional. In most cases, if a particular driver does not support a feature required by the application, the application simply refuses to run with that driver. However, if the feature is optional, the application can work around the feature. For example, it might disable those parts of the interface that allow the user to use the feature.</para>
    <para>To determine which features are supported, applications start by calling <legacyBold>SQLGetInfo</legacyBold> with the SQL_SQL_CONFORMANCE option. The SQL conformance level gives the application a broad view of which SQL is supported. To refine this view, the application calls <legacyBold>SQLGetInfo</legacyBold> with any of a number of other options. For a complete list of these options, see the <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> function description. Finally, <legacyBold>SQLGetTypeInfo</legacyBold> returns information about the data types supported by the data source. The following sections list a number of possible factors that applications should watch for when constructing interoperable SQL statements.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="84f7ef61-1ef1-46f3-9678-b087aa8e8e34">Catalog and Schema Usage</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="5bc5f64b-c75a-43d2-8745-102ec7a49000">Catalog Position</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="729ba55f-743b-4a04-8c39-ac0a9914211d">Quoted Identifiers</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ee8a31aa-389d-4dd1-bfa9-547f6b50bc70">Identifier Case</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="5913abfa-d280-43e4-a2f1-05a924388bf9">Escape Sequences</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="29f468f2-f557-4a92-b31d-569c63cc6272">Literal Prefixes and Suffixes</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="cda56f2b-6eec-4cbc-8dbb-36d8fa9f9216">Parameter Markers in Procedure Calls</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="96ac9859-5976-4b06-ae1f-2fec3231e266">DDL Statements</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>