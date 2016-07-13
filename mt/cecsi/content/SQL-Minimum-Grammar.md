---
title: SQL Minimum Grammar
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f36d785-104f-4fec-93be-f201203bc7c7
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL Minimum Grammar
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This section describes the minimum SQL syntax that an ODBC driver must support. The syntax described in this section is a subset of the Entry level syntax of SQL-92. </para>
    <para>An application can use any of the syntax in this section and be assured that any ODBC-compliant driver will support that syntax. To determine whether additional features of SQL-92 not in this section are supported, the application should call <legacyBold>SQLGetInfo</legacyBold> with the SQL_SQL_CONFORMANCE information type. Even if the driver does not conform to any SQL-92 conformance level, an application can still use the syntax described in this section. If a driver conforms to an SQL-92 level, on the other hand, it supports all syntax included in that level. This includes the syntax in this section because the minimum grammar described here is a pure subset of the lowest SQL-92 conformance level. Once the application knows the SQL-92 level supported, it can determine whether a higher-level feature is supported (if any) by calling <legacyBold>SQLGetInfo</legacyBold> with the individual information type corresponding to that feature. </para>
    <para>Drivers that work only with read-only data sources might not support those parts of the grammar included in this section that deal with changing data. An application can determine if a data source is read-only by calling <legacyBold>SQLGetInfo</legacyBold> with the SQL_DATA_SOURCE_READ_ONLY information type.</para>
  </introduction>
  <section>
    <title>Statement</title>
    <content>
      <para>
        <legacyItalic>create-table-statement</legacyItalic> ::= </para>
      <para>     CREATE TABLE <legacyItalic>base-table-name</legacyItalic> </para>
      <para>     (<legacyItalic>column-identifier data-type</legacyItalic> [<legacyItalic>,column-identifier data-type</legacyItalic>]...)</para>
      <alert class="important">
        <para>As a <legacyItalic>data-type</legacyItalic> in a <legacyItalic>create-table-statement</legacyItalic>, applications must use a data type from the TYPE_NAME column of the result set returned by <legacyBold>SQLGetTypeInfo</legacyBold>.</para>
      </alert>
      <para>
        <legacyItalic>delete-statement-searched</legacyItalic> ::= </para>
      <para>     DELETE FROM <legacyItalic>table-name</legacyItalic> [WHERE <legacyItalic>search-condition</legacyItalic>]</para>
      <para>
        <legacyItalic>drop-table-statement</legacyItalic> ::= </para>
      <para>     DROP TABLE <legacyItalic>base-table-name</legacyItalic></para>
      <para>
        <legacyItalic>insert-statement</legacyItalic> ::= </para>
      <para>     INSERT INTO <legacyItalic>table-name</legacyItalic> [( <legacyItalic>column-identifier</legacyItalic> [, <legacyItalic>column-identifier</legacyItalic>]...)]      VALUES (<legacyItalic>insert-value</legacyItalic>[, <legacyItalic>insert-value</legacyItalic>]... )</para>
      <para>
        <legacyItalic>select-statement</legacyItalic> ::= </para>
      <para>     SELECT [ALL | DISTINCT] <legacyItalic>select-list</legacyItalic> </para>
      <para>     FROM <legacyItalic>table-reference-list</legacyItalic> </para>
      <para>     [WHERE <legacyItalic>search-condition</legacyItalic>] </para>
      <para>     [<legacyItalic>order-by-clause</legacyItalic>]</para>
      <para>
        <legacyItalic>statement</legacyItalic> ::= <legacyItalic>create-table-statement</legacyItalic> </para>
      <para>     | <legacyItalic>delete-statement-searched</legacyItalic> </para>
      <para>     | <legacyItalic>drop-table-statement</legacyItalic> </para>
      <para>     | <legacyItalic>insert-statement</legacyItalic> </para>
      <para>     | <legacyItalic>select-statement</legacyItalic> </para>
      <para>     | <legacyItalic>update-statement-searched</legacyItalic></para>
      <para>
        <legacyItalic>update-statement-searched</legacyItalic> </para>
      <para>     UPDATE <legacyItalic>table-name</legacyItalic> </para>
      <para>     SET <legacyItalic>column-identifier</legacyItalic> = {<legacyItalic>expression</legacyItalic> | NULL } </para>
      <para>          [, <legacyItalic>column-identifier</legacyItalic> = {<legacyItalic>expression</legacyItalic> | NULL}]... </para>
      <para>     [WHERE <legacyItalic>search-condition</legacyItalic>]</para>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="85777525-1555-4731-8309-63a464c6b43a">Elements Used in SQL Statements</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="782b4490-372b-4366-aad7-a486fb8a07c8">Data Type Support</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="fd7e99d8-d26a-408c-9733-6ffccde99f75">Parameter Data Types</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="07213d04-cd31-45fd-a8c8-2e16e09eeaf4">Parameter Markers</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>