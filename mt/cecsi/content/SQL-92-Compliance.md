---
title: SQL-92 Compliance
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
translation.priority.ht: 
  - en-gb
---
# SQL-92 Compliance
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ODBC Desktop Database Drivers and the underlying Microsoft Jet engine are not SQL-92 compliant. They support many features that have been defined in SQL-92. Some features supported in the driver are not supported in SQL-92. For more information, see the <legacyItalic>Microsoft Jet Database Engine Programmer's Guide</legacyItalic>. The following are the major differences between the two:  </para>
    <list class="bullet">
      <listItem>
        <para>The SQL used by the Desktop Database Drivers supports more powerful expressions than those specified by SQL-92.</para>
      </listItem>
      <listItem>
        <para>Different rules apply to the BETWEEN predicate.</para>
      </listItem>
      <listItem>
        <para>The SQL used by the Desktop Database Drivers and ANSI SQL supports different keywords.</para>
      </listItem>
    </list>
    <para>The following SQL-92 features are not supported by Microsoft Jet SQL:  </para>
    <list class="bullet">
      <listItem>
        <para>Security statements, such as GRANT and LOCK.</para>
      </listItem>
      <listItem>
        <para>DISTINCT with aggregate function references.</para>
      </listItem>
    </list>
    <para>The following features are enhancements in the SQL used by the Desktop Database Drivers that are not specified by SQL-92:  </para>
    <list class="bullet">
      <listItem>
        <para>The TRANSFORM statement providing support for crosstab queries.</para>
      </listItem>
      <listItem>
        <para>Additional aggregate functions (<legacyBold>StDev</legacyBold> and <legacyBold>VarP</legacyBold>).</para>
      </listItem>
    </list>
    <alert class="note">
      <para>The Desktop Database Drivers support the standard ANSI syntax for % (percent) and _ (underscore), not * (asterisk) and ? (question mark).</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>