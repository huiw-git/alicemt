---
title: New Features
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8fcdd00-6cb3-4871-9489-6018b3d0d65f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# New Features
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following new functionality has been introduced in ODBC 3.<legacyItalic>x</legacyItalic>. An ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2<legacyItalic>.x</legacyItalic> driver will not be able to use this functionality. The ODBC 3.<legacyItalic>x</legacyItalic> Driver Manager does not map these features when working with an ODBC 2<legacyItalic>.x </legacyItalic>driver.  </para>
    <list class="bullet">
      <listItem>
        <para>Functions that take a descriptor handle as an argument: <legacyBold>SQLSetDescField</legacyBold>, <legacyBold>SQLGetDescField</legacyBold>, <legacyBold>SQLSetDescRec</legacyBold>, <legacyBold>SQLGetDescRec</legacyBold>, and <legacyBold>SQLCopyDesc</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>The functions <legacyBold>SQLSetEnvAttr</legacyBold> and <legacyBold>SQLGetEnvAttr</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>The use of <legacyBold>SQLAllocHandle</legacyBold> to allocate a descriptor handle. (The use of <legacyBold>SQLAllocHandle</legacyBold> to allocate environment, connection, and statement handles is duplicated, not new, functionality.)</para>
      </listItem>
      <listItem>
        <para>The use of <legacyBold>SQLGetConnectAttr</legacyBold> to get the SQL_ATTR_AUTO_IPD connection attributes. (The use of <legacyBold>SQLSetConnectAttr</legacyBold> to set, and <legacyBold>SQLGetConnectAttr</legacyBold> to get, other connection attributes is duplicated, not new, functionality.)</para>
      </listItem>
      <listItem>
        <para>The use of <legacyBold>SQLSetStmtAttr</legacyBold> to set, and <legacyBold>SQLGetStmtAttr</legacyBold> to get, the following statement attributes. (The use of <legacyBold>SQLSetStmtAttr</legacyBold> to set, and <legacyBold>SQLGetStmtAttr</legacyBold> to get, other statement attributes is duplicated, not new, functionality.) </para>
        <para>SQL_ATTR_APP_ROW_DESC</para>
        <para>SQL_ATTR_APP_PARAM_DESC</para>
        <para>SQL_ATTR_ENABLE_AUTO_IPD</para>
        <para>SQL_ATTR_FETCH_BOOKMARK_PTR</para>
        <para>SQL_ATTR_BIND_OFFSET</para>
        <para>SQL_ATTR_METADATA_ID</para>
        <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR</para>
        <para>SQL_ATTR_PARAM_BIND_TYPE</para>
        <para>SQL_ATTR_PARAM_OPERATION_PTR</para>
        <para>SQL_DESC_PARAM_STATUS_PTR</para>
        <para>SQL_ATTR_PARAMS_PROCESSED_PTR</para>
        <para>SQL_ATTR_PARAMSET_SIZE</para>
        <para>SQL_ATTR_ROW_BIND_OFFSET_PTR</para>
        <para>SQL_ATTR_ROW_OPERATION_PTR</para>
        <para>SQL_ATTR_ROW_ARRAY_SIZE </para>
      </listItem>
      <listItem>
        <para>The use of <legacyBold>SQLGetStmtAttr</legacyBold> to get the following statement attributes. (The use of <legacyBold>SQLGetStmtAttr</legacyBold> to get other statement attributes is duplicated functionality, not new functionality.) </para>
        <para>SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC </para>
      </listItem>
      <listItem>
        <para>Use of the interval C data type, the interval SQL data types, the BIGINT C data types, and the SQL_C_NUMERIC data structure.</para>
      </listItem>
      <listItem>
        <para>Row-wise binding of parameters.</para>
      </listItem>
      <listItem>
        <para>Offset-based bookmark fetches, such as calling <legacyBold>SQLFetchScroll</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> argument of SQL_FETCH_BOOKMARK and specifying an offset other than 0.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLFetch</legacyBold> returning the row status array, number of rows fetched, fetching multiple rows, intermixing calls with <legacyBold>SQLFetchScroll</legacyBold>, and intermixing calls with <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>. For more information, see the next section, <legacyLink xlink:href="82f6cf68-cfde-4417-9788-d6382ca14bf8">Block Cursors, Scrollable Cursors, and Backward Compatibility for ODBC 3.x Applications</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>Named parameters.</para>
      </listItem>
      <listItem>
        <para>Any of the ODBC 3.<legacyItalic>x</legacyItalic>–specific <legacyBold>SQLGetInfo</legacyBold> options. (If an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver calls the SQL_XXX_CURSOR_ATTRIBUTES1 information types, which have replaced several ODBC 2.<legacyItalic>x</legacyItalic> information types, some of the information might be reliable, but some might be unreliable. For more information, see <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink>.)</para>
      </listItem>
      <listItem>
        <para>Bind offsets.</para>
      </listItem>
      <listItem>
        <para>Updating, refreshing, and deleting by bookmarks (through a call to <legacyBold>SQLBulkOperations</legacyBold>).</para>
      </listItem>
      <listItem>
        <para>Calling <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> in the S5 state.</para>
      </listItem>
      <listItem>
        <para>The ROW_NUMBER and COLUMN_NUMBER fields in the diagnostic record (which have to be retrieved by the replacement functions <legacyBold>SQLGetDiagField</legacyBold> or <legacyBold>SQLGetDiagRec</legacyBold>).</para>
      </listItem>
      <listItem>
        <para>Approximate row counts.</para>
      </listItem>
      <listItem>
        <para>Warning information (SQL_ROW_SUCCESS_WITH_INFO from <legacyBold>SQLFetchScroll</legacyBold>).</para>
      </listItem>
      <listItem>
        <para>Variable-length bookmarks.</para>
      </listItem>
      <listItem>
        <para>Extended error information for arrays of parameters.</para>
      </listItem>
      <listItem>
        <para>All of the new columns in the result sets returned by the catalog functions.</para>
      </listItem>
      <listItem>
        <para>Use of <legacyBold>SQLDescribeCol</legacyBold> and <legacyBold>SQLColAttribute</legacyBold> on column 0.</para>
      </listItem>
      <listItem>
        <para>Use of any ODBC 3.<legacyItalic>x</legacyItalic>–specific column attributes in a call to <legacyBold>SQLColAttribute</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Use of multiple environment handles.</para>
      </listItem>
    </list>
    <para>This section contains the following topic.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="82f6cf68-cfde-4417-9788-d6382ca14bf8">Block Cursors, Scrollable Cursors, and Backward Compatibility for ODBC 3.x Applications</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>