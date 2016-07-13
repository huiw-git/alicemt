---
title: Using the ODBC Cursor Library
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9653f2f8-ccfc-4220-99ef-601dc0fa641c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using the ODBC Cursor Library
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>To use the ODBC cursor library, an application:  </para>
  </introduction>
  <section>
    <content>
      <list class="ordered">
        <listItem>
          <para>Calls <legacyBold>SQLSetConnectAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> of SQL_ATTR_ODBC_CURSORS to specify how the cursor library should be used with a particular connection. The cursor library can be always used (SQL_CUR_USE_ODBC), used only if driver does not support scrollable cursors (SQL_CUR_USE_IF_NEEDED), or never used (SQL_CUR_USE_DRIVER).</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLDriverConnect</legacyBold>, or <legacyBold>SQLBrowseConnect</legacyBold> to connect to the data source.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLSetStmtAttr</legacyBold> to specify the cursor type (SQL_ATTR_CURSOR_TYPE), concurrency (SQL_ATTR_CONCURRENCY), and rowset size (SQL_ATTR_ROW_ARRAY_SIZE). The cursor library supports forward-only and static cursors. Forward-only cursors must be read-only, while static cursors can be read-only or can use optimistic concurrency control comparing values.</para>
        </listItem>
        <listItem>
          <para>Allocates one or more rowset buffers and calls <legacyBold>SQLBindCol</legacyBold> one or more times to bind these buffers to result set columns.</para>
        </listItem>
        <listItem>
          <para>Generates a result set by executing a <legacyBold>SELECT</legacyBold> statement or a procedure, or by calling a catalog function. If the application will execute positioned update statements, it should execute a <legacyBold>SELECT FOR UPDATE</legacyBold> statement to generate the result set.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> one or more times to scroll through the result set.</para>
        </listItem>
      </list>
      <para>The application can change data values in the rowset buffers. To refresh the rowset buffers with data from the cursor library's cache, an application calls <legacyBold>SQLFetchScroll</legacyBold> with the <legacyItalic>FetchOrientation</legacyItalic> argument set to SQL_FETCH_RELATIVE and the <legacyItalic>FetchOffset</legacyItalic> argument set to 0.</para>
      <para>To retrieve data from an unbound column, the application calls <legacyBold>SQLSetPos</legacyBold> to position the cursor on the desired row. It then calls <legacyBold>SQLGetData</legacyBold> to retrieve the data.</para>
      <para>To determine the number of rows that have been retrieved from the data source, the application calls <legacyBold>SQLRowCount</legacyBold>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>