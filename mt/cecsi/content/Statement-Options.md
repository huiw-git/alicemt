---
title: "Statement Options"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd73b769-c8b5-43e0-9f80-b3011b7a6162
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Statement Options
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>These options allow customization of a specific execution statement within an application.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Statement option</para>
          </TD>
          <TD>
            <para>Notes</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_BIND_TYPE</para>
          </TD>
          <TD>
            <para>Cannot exceed 2,147,483,647 bytes or available memory.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CONCURRENCY</para>
          </TD>
          <TD>
            <para>For allowed values, see the <legacyLink xlink:href="db63d610-f86f-4029-9d66-fed616c8a818">Cursor Type and Concurrency Combinations</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CURSOR_TYPE</para>
          </TD>
          <TD>
            <para>The driver does not allow SQL_CURSOR_DYNAMIC. See <legacyLink xlink:href="d9f49520-72d7-4234-8635-260d0ce4199c">SQLSetScrollOptions</legacyLink> for more information. For allowed values, see the <legacyLink xlink:href="db63d610-f86f-4029-9d66-fed616c8a818">Cursor Type and Concurrency Combinations</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_GET_BOOKMARK</para>
          </TD>
          <TD>
            <para>Returns a 32-bit integer value that is the bookmark for the current record number. Get only; cannot Set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_KEYSET_SIZE</para>
          </TD>
          <TD>
            <para>Can be set only to 0.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_ROWS</para>
          </TD>
          <TD>
            <para>The maximum number of rows to return from a result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROW_NUMBER</para>
          </TD>
          <TD>
            <para>Returns a 32-bit integer specifying the position of the current row within the result set. Get only; cannot Set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROWSET_SIZE</para>
          </TD>
          <TD>
            <para>Cannot exceed 4,294,967,296 rows; however, you must have enough virtual memory in your computer to handle your request. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_USE_BOOKMARKS</para>
          </TD>
          <TD>
            <para>Supports setting SQL_USE_BOOKMARKS to SQL_UB_ON and exposes fixed-length bookmarks.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>