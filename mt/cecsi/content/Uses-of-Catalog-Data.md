---
title: "Uses of Catalog Data"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5915d0c-eec3-4382-850e-bd863763c99a
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Uses of Catalog Data
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications use catalog data in a variety of ways. Here are some common uses:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Constructing SQL statements at run time.</legacyBold> Vertical applications, such as an order entry application, contain hard-coded SQL statements. The tables and columns that are used by the application are fixed ahead of time, as are the statements that access these tables. For example, an order entry application usually contains a single, parameterized <legacyBold>INSERT</legacyBold> statement for adding new orders to the system. </para>
        <para>Generic applications, such as a spreadsheet program that uses ODBC to retrieve data, often construct SQL statements at run time based on input from the user. Such an application could require the user to type the names of the tables and columns to use. However, it would be easier for the user if the application displayed lists of tables and columns from which the user could make selections. To build these lists, the application would call the <legacyBold>SQLTables</legacyBold> and <legacyBold>SQLColumns</legacyBold> catalog functions. </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Constructing SQL statements during development.</legacyBold> Application development environments typically allow the programmer to create database queries while developing a program. The queries are then hard-coded in the application being built. </para>
        <para>Such environments could also use <legacyBold>SQLTables</legacyBold> and <legacyBold>SQLColumns</legacyBold> to create lists from which the programmer could make selections. These environments might also use <legacyBold>SQLPrimaryKeys</legacyBold> and <legacyBold>SQLForeignKeys</legacyBold> to automatically determine and show relationships between selected tables, and use <legacyBold>SQLStatistics</legacyBold> to determine and highlight indexed fields so the programmer can create efficient queries. </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Constructing cursors.</legacyBold> An application, driver, or middleware that provides a scrollable cursor engine could use <legacyBold>SQLSpecialColumns</legacyBold> to determine which column or columns uniquely identify a row. The program could build a <legacyItalic>keyset</legacyItalic> containing the values of these columns for each row that has been fetched. When the application scrolls back to the row, it would then use these values to fetch the most recent data for the row. For more information about scrollable cursors and keysets, see <legacyLink xlink:href="2c8a5f50-9b37-452f-8160-05f42bc4d97e">Scrollable Cursors</legacyLink>.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>