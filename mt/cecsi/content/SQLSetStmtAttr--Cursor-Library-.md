---
title: "SQLSetStmtAttr (Cursor Library)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6018a733-c2c8-4047-92ec-92cf85031767
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetStmtAttr (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLSetStmtAttr</legacyBold> function in the cursor library. For general information about <legacyBold>SQLSetStmtAttr</legacyBold>, see <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library supports the following statement attributes with <legacyBold>SQLSetStmtAttr</legacyBold>:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_ATTR_CONCURRENCY</para>
            </TD>
            <TD>
              <para>SQL_ATTR_ROW_BIND_OFFSET_PTR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CURSOR_TYPE</para>
            </TD>
            <TD>
              <para>SQL_ATTR_ROW_BIND_TYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_FETCH_BOOKMARK_PTR</para>
            </TD>
            <TD>
              <para>SQL_ATTR_ROWSET_ARRAY_SIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR</para>
            </TD>
            <TD>
              <para>SQL_ATTR_SIMULATE_CURSOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_BIND_TYPE</para>
            </TD>
            <TD>
              <para>SQL_ATTR_USE_BOOKMARKS</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The cursor library supports only the SQL_CURSOR_FORWARD_ONLY and SQL_CURSOR_STATIC values of the SQL_ATTR_CURSOR_TYPE statement attribute.</para>
      <para>For forward-only cursors, the cursor library supports the SQL_CONCUR_READ_ONLY value of the SQL_ATTR_CONCURRENCY statement attribute. For static cursors, the cursor library supports the SQL_CONCUR_READ_ONLY and SQL_CONCUR_VALUES values of the SQL_ATTR_CONCURRENCY statement attribute.</para>
      <para>The cursor library supports only the SQL_SC_NON_UNIQUE value of the SQL_ATTR_SIMULATE_CURSOR statement attribute.</para>
      <para>Although the ODBC specification supports calls to <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_PARAM_BIND_TYPE or SQL_ATTR_ROW_BIND_TYPE attributes after <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has been called, the cursor library does not. Before it can change the binding type in the cursor library, the application must close the cursor. The cursor library supports changing the SQL_ATTR_ROW_BIND_OFFSET_PTR, SQL_ATTR_PARAM_BIND_OFFSET_PTR, SQL_ATTR_ROWS_FETCHED_PTR, and SQL_ATTR_PARAMS_PROCESSED_PTR statement attributes when a cursor is open.</para>
      <para>An application can call <legacyBold>SQLSetStmtAttr</legacyBold> with an <legacyBold>Attribute</legacyBold> of SQL_ATTR_ROW_ARRAY_SIZE to change the rowset size while a cursor is open. The new rowset size will take effect the next time <legacyBold>SQLFetchScroll</legacyBold> or <legacyBold>SQLFetch</legacyBold> is called.</para>
      <para>The cursor library supports setting the SQL_ATTR_PARAM_BIND_OFFSET_PTR or SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute to enable binding offsets. The binding offset will not be used for calls to <legacyBold>SQLFetch</legacyBold> when the cursor library is used with an ODBC 2.<legacyItalic>x</legacyItalic> driver.</para>
      <para>The cursor library supports setting the SQL_ATTR_USE_BOOKMARKS statement attribute to SQL_UB_VARIABLE.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>