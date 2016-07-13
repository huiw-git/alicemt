---
title: Result-Generating and Result-Free Statements
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2f3475d1-3999-4dd8-aba2-a6e1299c95f8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Result-Generating and Result-Free Statements
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>SQL statements can be loosely divided into the following five categories:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Result Set-Generating Statements</legacyBold> These are SQL statements that generate a result set. For example, a <legacyBold>SELECT</legacyBold> statement.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Row Count-Generating Statements</legacyBold> These are SQL statements that generate a count of affected rows. For example, an <legacyBold>UPDATE</legacyBold> or <legacyBold>DELETE</legacyBold> statement.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Data Definition Language (DDL) Statements</legacyBold> These are SQL statements that modify the structure of the database. For example, <legacyBold>CREATE TABLE</legacyBold> or <legacyBold>DROP INDEX</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Context-Changing Statements</legacyBold> These are SQL statements that change the context of a database. For example, the <legacyBold>USE</legacyBold> and <legacyBold>SET</legacyBold> statements in SQL Server.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Administrative Statements</legacyBold> These are SQL statements used for administrative purposes in a database. For example, <legacyBold>GRANT</legacyBold> and <legacyBold>REVOKE</legacyBold>.</para>
      </listItem>
    </list>
    <para>SQL statements in the first two categories are collectively known as <legacyItalic>result-generating statements</legacyItalic>. SQL statements in the latter three categories are collectively known as <legacyItalic>result-free statements</legacyItalic>. ODBC defines the semantics of batches that include only result-generating statements. These semantics vary widely and are therefore data source–specific. For example, the SQL Server driver does not support dropping an object and then referring to or re-creating the same object in the same batch. Therefore, the term <legacyItalic>batch</legacyItalic> as used in this manual refers only to batches of result-generating statements.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>