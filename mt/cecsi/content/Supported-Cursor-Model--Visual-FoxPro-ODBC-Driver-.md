---
title: Supported Cursor Model (Visual FoxPro ODBC Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Supported Cursor Model (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Visual FoxPro ODBC Driver supports both <legacyItalic>block</legacyItalic> (<legacyItalic>rowset</legacyItalic>) and <legacyItalic>static</legacyItalic> cursors. Static cursors are supported for any driver that conforms to Level 1 ODBC compliance. The driver does not support dynamic, keyset-driven, or mixed (keyset and dynamic) cursors.</para>
    <para>Your application can call <legacyLink xlink:href="76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36">SQLSetStmtOption</legacyLink> with a SQL_CURSOR_TYPE option of SQL_CURSOR_FORWARD_ONLY (block cursor) or SQL_CURSOR_STATIC (static cursor).</para>
    <alert class="note">
      <para>If you call <legacyBold>SQLSetStmtOption</legacyBold> with a SQL_CURSOR_TYPE option other than SQL_CURSOR_FORWARD_ONLY or SQL_CURSOR_STATIC, the function returns SQL_SUCCESS_WITH_INFO with a SQLSTATE of 01S02 (Option value changed). The driver sets all unsupported cursor modes to SQL_CURSOR_STATIC.</para>
    </alert>
    <para>For more information about cursor types and about <legacyBold>SQLSetStmtOption</legacyBold>, see the <legacyLink xlink:href="b33c3c43-ae66-44a3-be17-9cd82624dd96">ODBC Programmer's Reference</legacyLink>.</para>
  </introduction>
  <section>
    <title>block cursor</title>
    <content>
      <para>A forward-scrolling, read-only result set returned to the client, who is responsible for maintaining storage for the data.</para>
    </content>
  </section>
  <section>
    <title>static cursor</title>
    <content>
      <para>A snapshot of a data set defined by the query. Static cursors do not reflect real-time changes of the underlying data by other users. The cursor's memory buffer is maintained by the ODBC cursor library, which allows forward and backward scrolling.</para>
    </content>
  </section>
  <section>
    <title>rowset</title>
    <content>
      <para>Blocks of data stored in a cursor, representing rows retrieved from a data source.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>