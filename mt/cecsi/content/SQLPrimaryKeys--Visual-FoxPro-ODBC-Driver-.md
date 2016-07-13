---
title: SQLPrimaryKeys (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLPrimaryKeys (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Level 2</para>
    <para>Returns the column names that comprise the primary key for a table. The Visual FoxPro ODBC Driver implementation of <legacyBold>SQLPrimaryKeys</legacyBold> behaves as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>Ignores the <legacyItalic>szTableOwner</legacyItalic> and <legacyItalic>cbTableOwner</legacyItalic> arguments.</para>
      </listItem>
      <listItem>
        <para>Works only for data sources that are <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">databases</legacyLink>. The driver returns the error "Driver does not support this function" if the data source is a directory of <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">free tables</legacyLink>.</para>
      </listItem>
    </list>
    <para>For more information, see <legacyLink xlink:href="3f809b09-3c1b-415e-80c5-a603e8e25d5b">SQLPrimaryKeys</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>