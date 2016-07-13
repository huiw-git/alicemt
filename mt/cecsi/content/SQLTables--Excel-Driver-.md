---
title: SQLTables (Excel Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLTables (Excel Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Excel Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
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
            <para>
              <legacyItalic>szTableOwner</legacyItalic> </para>
          </TD>
          <TD>
            <para>The only valid argument for <legacyItalic>szTableOwner</legacyItalic> is NULL because none of the drivers support owner names. With <legacyItalic>szTableOwner</legacyItalic> set to NULL, all tables are returned. NULL is returned in the TABLE_OWNER column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyItalic>szTableQualifier</legacyItalic>
            </para>
          </TD>
          <TD>
            <para>When the Microsoft Excel 3.0 or 4.0 driver is used, if you call <legacyBold>SQLTables</legacyBold> with a value for <legacyItalic>szTableQualifier</legacyItalic> that is not the name of an existing table, the driver will create a table with that name.</para>
            <para>In the TABLE_QUALIFIER column, <legacyBold>SQLTables</legacyBold> will return the path to a directory.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyItalic>SzTableType</legacyItalic>
            </para>
          </TD>
          <TD>
            <para>For Microsoft Excel 3.0 or 4.0, "TABLE" is the only table type supported.</para>
            <para>For later versions of Microsoft Excel files, "SYSTEM TABLE" is returned for sheet names (tables with a "$" on the end), and "TABLE" is returned for tables within worksheets.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>