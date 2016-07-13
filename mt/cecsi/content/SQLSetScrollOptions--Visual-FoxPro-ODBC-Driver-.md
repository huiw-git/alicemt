---
title: SQLSetScrollOptions (Visual FoxPro ODBC Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetScrollOptions (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Partial </para>
    <para>ODBC API Conformance: Level 2</para>
    <para>Sets options that control the behavior of cursors associated with a statement handle, <legacyItalic>hstmt</legacyItalic>.</para>
    <para>The Visual FoxPro ODBC Driver supports only SQL_CONCUR_READ_ONLY; it does not support the <legacyItalic>fConcurrency</legacyItalic> value SQL_CONCUR_ROWVER. The driver converts SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC, and SQL_CURSOR_KEYSET_DRIVEN to SQL_SCROLL_STATIC with warning ODBC_01S02.</para>
    <para>For more information, see <legacyLink xlink:href="2a825ba7-7942-4c23-bcdb-c80dc12f8c86">SQLSetScrollOptions</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>