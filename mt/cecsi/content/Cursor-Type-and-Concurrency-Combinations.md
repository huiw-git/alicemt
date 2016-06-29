---
title: Cursor Type and Concurrency Combinations
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
translation.priority.ht: 
  - en-gb
---
# Cursor Type and Concurrency Combinations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>Cursor types control the functionality of the cursor provided to the user. Concurrency options control the updatability and locking behavior of a result set.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Cursor type</para>
          </TD>
          <TD>
            <para>Concurrency (allowed values)</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_CURSOR_FORWARD_ONLY</para>
          </TD>
          <TD>
            <para>SQL_CONCUR_READ_ONLY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CURSOR_STATIC</para>
          </TD>
          <TD>
            <para>SQL_CONCUR_READ_ONLY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CURSOR_KEYSET_DRIVEN<superscript>[1]</superscript></para>
          </TD>
          <TD>
            <para>SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<superscript>[2]</superscript> SQL_CONCUR_VALUES</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>
      <superscript>[1]</superscript>   See <legacyLink xlink:href="59d86fed-387c-4719-9550-36343e74da44">Limitations of Using Keyset-Driven Cursors</legacyLink>.</para>
    <para>
      <superscript>[2]</superscript>   SQL_CONCUR_LOCK is supported only when the SQL_AUTOCOMMIT connection option is set to SQL_AUTOCOMMIT_OFF.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">Connect Options</link>
</relatedTopics>
</developerConceptualDocument>