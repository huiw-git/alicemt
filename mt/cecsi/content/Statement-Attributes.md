---
title: Statement Attributes
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Statement Attributes
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Statement attributes are characteristics of the statement. For example, whether to use bookmarks and what kind of cursor to use with the statement's result set are statement attributes.</para>
    <para>Statement attributes are set with <legacyBold>SQLSetStmtAttr</legacyBold> and their current settings retrieved with <legacyBold>SQLGetStmtAttr</legacyBold>. There is no requirement that an application set any statement attributes; all statement attributes have defaults, some of which are driver-specific.</para>
    <para>When a statement attribute can be set depends on the attribute itself. The SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, and SQL_ATTR_USE_BOOKMARKS statement attributes must be set before the statement is executed. The SQL_ATTR_ASYNC_ENABLE and SQL_ATTR_NOSCAN statement attributes can be set at any time but are not applied until the statement is used again. SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, and SQL_ATTR_QUERY_TIMEOUT statement attributes can be set at any time, but it is driver-specific whether they are applied before the statement is used again. The remaining statement attributes can be set at any time.</para>
    <alert class="note">
      <para>The ability to set statement attributes at the connection level by calling <legacyBold>SQLSetConnectAttr</legacyBold> has been deprecated in ODBC 3.<legacyItalic>x</legacyItalic>. ODBC 3.<legacyItalic>x</legacyItalic> applications should never set statement attributes at the connection level. ODBC 3.<legacyItalic>x</legacyItalic> drivers need only support this functionality if they should work with ODBC 2.<legacyItalic>x</legacyItalic> applications. For more information, see <legacyLink xlink:href="a1b325cf-0c42-41c1-b141-b5a4fee7e708">SQLSetConnectOption Mapping</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
      <para>An exception to this is the SQL_ATTR_METADATA_ID and SQL_ATTR_ASYNC_ENABLE attributes, which are both connection attributes and statement attributes and can be set either at the connection level or the statement level.</para>
      <para>None of the statement attributes introduced in ODBC 3.<legacyItalic>x</legacyItalic> (except for SQL_ATTR_METADATA_ID) can be set at the connection level.</para>
    </alert>
    <para>For more information, see the <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink> function description.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>