---
title: SQLTables (Access Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
translation.priority.ht: 
  - en-gb
---
# SQLTables (Access Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Access Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Argument</para>
          </TD>
          <TD>
            <para>Comments</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyItalic>szTableOwner</legacyItalic>             </para>
          </TD>
          <TD>
            <para>The only valid argument for <legacyItalic>szTableOwner</legacyItalic> is NULL because none of the drivers support owner names. With <legacyItalic>szTableOwner</legacyItalic> set to NULL, all tables are returned. NULL is returned in the TABLE_OWNER column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>szTableQualifier</legacyItalic>             </para>
          </TD>
          <TD>
            <para>In the TABLE_QUALIFIER column, <legacyBold>SQLTables</legacyBold> will return the path to a database file. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>SzTableType</legacyItalic>             </para>
          </TD>
          <TD>
            <para>When the Microsoft Access driver is used, "SYSTEM TABLE" is supported for <legacyItalic>szTableType</legacyItalic> for system tables, "SYNONYM" is supported for attached tables, and "VIEW" is supported for row-returning queries.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="60d5068a-7d7c-447c-acc6-f3f2cf73440c">SqlTables</link>
</relatedTopics>
</developerConceptualDocument>