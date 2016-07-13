---
title: SQLStatistics (Access Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLStatistics (Access Driver)
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
            <para>Column</para>
          </TD>
          <TD>
            <para>Comments</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>TABLE_QUALIFIER</para>
          </TD>
          <TD>
            <para>The path to a database file is returned for Microsoft Access.</para>
            <para>Pattern matching is not supported in the <legacyItalic>szTableQualifier</legacyItalic> argument.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TABLE_OWNER</para>
          </TD>
          <TD>
            <para>NULL is returned in this column, because owner name is not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TABLE_NAME</para>
          </TD>
          <TD>
            <para>Undelimited table name.</para>
            <para>Pattern matching is not supported in the <legacyItalic>szTableName</legacyItalic> argument.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>INDEX_QUALIFIER</para>
          </TD>
          <TD>
            <para>NULL is always returned.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>INDEX_NAME</para>
          </TD>
          <TD>
            <para>Index-dependent.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TYPE</para>
          </TD>
          <TD>
            <para>Only SQL_TABLE_STAT or SQL_INDEX_OTHER will be returned for TYPE.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SEQ_IN_INDEX</para>
          </TD>
          <TD>
            <para>Index-dependent.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>COLUMN_NAME</para>
          </TD>
          <TD>
            <para>Index-dependent.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>COLLATION</para>
          </TD>
          <TD>
            <para>Index-dependent.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CARDINALITY</para>
          </TD>
          <TD>
            <para>Returned for Microsoft Access only.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PAGES</para>
          </TD>
          <TD>
            <para>NULL is always returned.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>Filtering is based on uniqueness (the <legacyItalic>fUnique</legacyItalic> argument). The <legacyItalic>fAccuracy</legacyItalic> parameter is ignored.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>