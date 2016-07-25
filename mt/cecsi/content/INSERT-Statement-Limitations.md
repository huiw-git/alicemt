---
title: "INSERT Statement Limitations"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dea05698-527a-41ab-8729-bbed85556185
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# INSERT Statement Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Inserted data is truncated on the right without warning if it is too long to fit into the column.</para>
    <para>Attempting to insert a value that is out of the range of a column's data type causes a NULL to be inserted into the column.</para>
    <para>When a dBASE, Microsoft Excel, Paradox, or Textdriver is used, inserting a zero-length string into a column actually inserts a NULL instead.</para>
    <para>When the Microsoft Excel driver is used, if an empty string is inserted into a column, the empty string is converted to a NULL; a searched SELECT statement that is executed with an empty string in the WHERE clause will not succeed on that column.</para>
    <para>A table is not updatable by the Paradox driver under two conditions:  </para>
    <list class="bullet">
      <listItem>
        <para>When a unique index is not defined on the table. This is not true for an empty table, which can be updated with a single row even if a unique index is not defined on the table. If a single row is inserted in an empty table that does not have a unique index, an application cannot create a unique index or insert additional data after the single row has been inserted. </para>
      </listItem>
      <listItem>
        <para>If the Borland Database Engine is not implemented, only read and append statements are allowed on the Paradox table.</para>
      </listItem>
    </list>
    <para>When the Text driver is used, NULL values are represented by a blank-padded string in fixed-length files, but are represented by no spaces in delimited files. For example, in the following row containing three fields, the second field is a NULL value:</para>
    <code> "Smith:,, 123</code>
    <para>When the Text driver is used, all column values can be padded with leading spaces. The length of any row must be less than or equal to 65,543 bytes.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>