---
title: SQLTables (Text File Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f47fd1a4-5bd8-4b2e-8ae3-e595e49f4f95
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLTables (Text File Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Text File Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
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
            <para>In the TABLE_QUALIFIER column, <legacyBold>SQLTables</legacyBold> will return the path to a directory.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>SzTableType</legacyItalic>             </para>
          </TD>
          <TD>
            <para>"TABLE" is the only table type supported.</para>
            <para>When the Text driver is used, the list of files returned by <legacyBold>SQLTables</legacyBold> is determined by the file extensions in the <legacyBold>Extensions List</legacyBold> box in the <legacyBold>ODBC Text Setup</legacyBold> dialog box.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>