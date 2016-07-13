---
title: SQLColAttributes (Paradox Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bbeef024-d470-4d28-b61b-26997ef41007
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLColAttributes (Paradox Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Paradox Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Attribute</para>
          </TD>
          <TD>
            <para>Comments</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_COLUMN_DISPLAY_SIZE</para>
          </TD>
          <TD>
            <para>For LONGVARBINARY data, SQL_COLUMN_DISPLAY_SIZE is the maximum length of the column, not the maximum length of the column times 2.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_OWNER_NAME</para>
          </TD>
          <TD>
            <para>An empty string ("") is returned in this column because owner name is not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_QUALIFIER_NAME</para>
          </TD>
          <TD>
            <para>The path to a directory is returned.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_COLUMN_SEARCHABLE</para>
          </TD>
          <TD>
            <para>LONGVARBINARY and LONGVARCHAR columns are reported as SQL_UNSEARCHABLE.</para>
            <para>Fixed-length and variable-length binary and character data types are searchable, even though LONGVARBINARY and LONGVARCHAR are not.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <alert class="note">
      <para>The above is not a complete list of the attributes returned by <legacyBold>SQLColAttributes</legacyBold>.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>