---
title: CREATE INDEX for Paradox
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6472bd69-b931-4bc2-a9bf-f1873ed4cdfe
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# CREATE INDEX for Paradox
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The syntax of the CREATE INDEX statement for the ODBC Paradox driver is:</para>
    <para>
      <legacyBold>CREATE </legacyBold>[<legacyBold>UNIQUE</legacyBold>]<legacyBold> INDEX</legacyBold> <legacyItalic>index-name</legacyItalic> </para>
    <para>
      <legacyBold>ON</legacyBold> <legacyItalic>table-name</legacyItalic> </para>
    <para>
      <legacyBold>(</legacyBold>
      <legacyItalic>column-identifier</legacyItalic> [<legacyBold>ASC</legacyBold>] </para>
    <para>[<legacyBold>,</legacyBold> <legacyItalic>column-identifier</legacyItalic> [<legacyBold>ASC</legacyBold>]...]<legacyBold>)</legacyBold></para>
    <para>The ODBC Paradox driver does not support the <legacyBold>DESC</legacyBold> keyword in the ODBC SQL grammar for the CREATE INDEX statement. The <legacyItalic>table-name</legacyItalic> argument can specify the full path of the table.</para>
    <para>If the keyword <legacyBold>UNIQUE</legacyBold> is specified, the ODBC Paradox driver will create a unique index. The first unique index is created as a primary index. This is a Paradox primary key file named <legacyItalic>table-name</legacyItalic>.PX. Primary indexes are subject to the following restrictions:  </para>
    <list class="bullet">
      <listItem>
        <para>The primary index must be created before any rows are added to the table.</para>
      </listItem>
      <listItem>
        <para>A primary index must be defined upon the first "n" columns in a table.</para>
      </listItem>
      <listItem>
        <para>Only one primary index is allowed per table.</para>
      </listItem>
      <listItem>
        <para>A table cannot be updated by the Paradox driver if a primary index is not defined on the table. (Note that this is not true for an empty table, which can be updated even if a unique index is not defined on the table.)</para>
      </listItem>
      <listItem>
        <para>The <legacyItalic>index-name</legacyItalic> argument for a primary index must be the same as the base name of the table, as required by Paradox.</para>
      </listItem>
    </list>
    <para>If the keyword <legacyBold>UNIQUE</legacyBold> is omitted, the ODBC Paradox driver will create a non-unique index. This consists of two Paradox secondary index files named <legacyItalic>table-name</legacyItalic>.X<legacyItalic>nn</legacyItalic> and <legacyItalic>table-name</legacyItalic>.Y<legacyItalic>nn</legacyItalic>, where <legacyItalic>nn</legacyItalic> is the number of the column in the table. Non-unique indexes are subject to the following restrictions:  </para>
    <list class="bullet">
      <listItem>
        <para>Before a non-unique index can be created for a table, a primary index must exist for that table.</para>
      </listItem>
      <listItem>
        <para>For Paradox 3.<legacyItalic>x</legacyItalic>, the <legacyItalic>index-name</legacyItalic> argument for any index other than a primary index (unique or non-unique) must be the same as the column name. For Paradox 4.<legacyItalic>x</legacyItalic> and 5.<legacyItalic>x</legacyItalic>, the name of such an index can be, but doesn't have to be, the same as the column name.</para>
      </listItem>
      <listItem>
        <para>Only one column can be specified for a non-unique index.</para>
      </listItem>
    </list>
    <para>Columns cannot be added once an index has been defined on a table. If the first column of the argument list of a CREATE TABLE statement creates an index, a second column cannot be included in the argument list.</para>
    <para>For example, to use the sales order number and line number columns as the unique index on the SO_LINES table, use the statement:</para>
    <code>CREATE UNIQUE INDEX SO_LINES
 ON SO_LINES (SONum, LineNum)</code>
    <para>To use the part number column as a non-unique index on the SO_LINES table, use the statement:</para>
    <code>CREATE INDEX PartNum
 ON SO_LINES (PartNum)</code>
    <para>Note that when two CREATE INDEX statements are performed, the first statement will always create a primary index with the same name as the table and the second statement will always create a non-unique index with the same name as the column. These indexes will be named this way even if different names are entered in the CREATE INDEX statements and even if the index is labeled UNIQUE in the second CREATE INDEX statement.</para>
    <alert class="note">
      <para>When you use the Paradox driver without implementing the Borland Database Engine, only read and append statements are allowed.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>