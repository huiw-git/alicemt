---
title: SQLFetchScroll (Cursor Library)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4417e57c-31dd-475e-8fe9-eab00a459c80
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLFetchScroll (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLFetchScroll</legacyBold> function in the cursor library. For general information about <legacyBold>SQLFetchScroll</legacyBold>, see <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll Function</legacyLink>.</para>
    <para>The cursor library implements <legacyBold>SQLFetchScroll</legacyBold> by repeatedly calling <legacyBold>SQLFetch</legacyBold> in the driver. It transfers the data it retrieves from the driver to the rowset buffers provided by the application. It also caches the data in memory and disk files. When an application requests a new rowset, the cursor library retrieves it as necessary from the driver (if it has not been previously fetched) or the cache (if it has been previously fetched). Finally, the cursor library maintains the status of the cached data and returns this information to the application in the row status array.</para>
    <para>When the cursor library is used, calls to <legacyBold>SQLFetchScroll</legacyBold> cannot be mixed with calls to either <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLExtendedFetch</legacyBold>.</para>
    <para>When the cursor library is used, calls to <legacyBold>SQLFetchScroll</legacyBold> are supported both for ODBC 2.<legacyItalic>x</legacyItalic> and for ODBC 3.<legacyItalic>x</legacyItalic> drivers.</para>
  </introduction>
  <section>
    <title>Rowset Buffers</title>
    <content>
      <para>The cursor library optimizes the transfer of data from the driver to the rowset buffer provided by the application if:  </para>
      <list class="bullet">
        <listItem>
          <para>The application uses row-wise binding.</para>
        </listItem>
        <listItem>
          <para>There are no unused bytes between fields in the structure the application declares to hold a row of data.</para>
        </listItem>
        <listItem>
          <para>The fields in which <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> returns the length/indicator for a column follows the buffer for that column and precedes the buffer for the next column. These fields are optional.</para>
        </listItem>
      </list>
      <para>When the application requests a new rowset, the cursor library retrieves data from its cache and from the driver as necessary. If the new and old rowsets overlap, the cursor library can optimize its performance by reusing the data from the overlapping sections of the rowset buffers. Therefore, unsaved changes to the rowset buffers are lost unless the new and old rowsets overlap and the changes are in the overlapping sections of the rowset buffers. To save the changes, an application submits a positioned update statement.</para>
      <para>Note that the cursor library always refreshes the rowset buffers with data from the cache when an application calls <legacyBold>SQLFetchScroll</legacyBold> with the <legacyItalic>FetchOrientation</legacyItalic> argument set to SQL_FETCH_RELATIVE and the <legacyItalic>FetchOffset</legacyItalic> argument set to 0.</para>
      <para>The cursor library supports calling <legacyBold>SQLSetStmtAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> of SQL_ATTR_ROW_ARRAY_SIZE to change the rowset size while a cursor is open. The new rowset size will take effect the next time <legacyBold>SQLFetchScroll</legacyBold> is called.</para>
    </content>
  </section>
  <section>
    <title>Result Set Membership</title>
    <content>
      <para>The cursor library retrieves data from the driver only as the application requests it. Depending on the data source and the setting of the SQL_CONCURRENCY statement attribute, this has the following consequences:  </para>
      <list class="bullet">
        <listItem>
          <para>The data retrieved by the cursor library might differ from the data that was available at the time the statement was executed. For example, after the cursor was opened, rows inserted at a point beyond the current cursor position can be retrieved by some drivers.</para>
        </listItem>
        <listItem>
          <para>The data in the result set might be locked by the data source for the cursor library and therefore be unavailable to other users.</para>
        </listItem>
      </list>
      <para>After the cursor library has cached a row of data, it cannot detect changes to that row in the underlying data source (except for positioned updates and deletes operating on the same cursor's cache). This occurs because, for calls to <legacyBold>SQLFetchScroll</legacyBold>, the cursor library never refetches data from the data source. Instead, it refetches data from its cache.</para>
    </content>
  </section>
  <section>
    <title>Scrolling</title>
    <content>
      <para>The cursor library supports the following fetch types in <legacyBold>SQLFetchScroll</legacyBold>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Cursor type</para>
            </TD>
            <TD>
              <para>Fetch types</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Forward-only</para>
            </TD>
            <TD>
              <para>SQL_FETCH_NEXT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Static</para>
            </TD>
            <TD>
              <para>SQL_FETCH_NEXT</para>
              <para>SQL_FETCH_PRIOR</para>
              <para>SQL_FETCH_FIRST</para>
              <para>SQL_FETCH_LAST</para>
              <para>SQL_FETCH_RELATIVE</para>
              <para>SQL_FETCH_ABSOLUTE</para>
              <para>SQL_FETCH_BOOKMARK</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Errors</title>
    <content>
      <para>When <legacyBold>SQLFetchScroll</legacyBold> is called and one of the calls to <legacyBold>SQLFetch</legacyBold> returns SQL_ERROR, the cursor library proceeds as follows. After it completes these steps, the cursor library continues processing.  </para>
      <list class="ordered">
        <listItem>
          <para>Calls <legacyBold>SQLGetDiagRec</legacyBold> to obtain error information from the driver and posts this as a diagnostic record in the Driver Manager.</para>
        </listItem>
        <listItem>
          <para>Sets the SQL_DIAG_ROW_NUMBER field in the diagnostic record to the appropriate value.</para>
        </listItem>
        <listItem>
          <para>Sets the SQL_DIAG_COLUMN_NUMBER field in the diagnostic record to the appropriate value, if applicable; otherwise, it sets it to 0.</para>
        </listItem>
        <listItem>
          <para>Sets the value for the row in error in the row status array to SQL_ROW_ERROR.</para>
        </listItem>
      </list>
      <para>After the cursor library has called <legacyBold>SQLFetch</legacyBold> multiple times in its implementation of <legacyBold>SQLFetchScroll</legacyBold>, any error or warning returned by one of the calls to <legacyBold>SQLFetch</legacyBold> will be in a diagnostic record and can be retrieved by a call to <legacyBold>SQLGetDiagRec</legacyBold>. If the data was truncated when it was fetched, the truncated data will now reside in the cursor library's cache. Subsequent calls to <legacyBold>SQLFetchScroll</legacyBold> to scroll to a row with truncated data will return the truncated data, and no warning will be raised because the data is fetched from the cursor library's cache. To keep track of the length of data returned so that it can determine whether the data returned in a buffer has been truncated, an application should bind the length/indicator buffer.</para>
    </content>
  </section>
  <section>
    <title>Bookmark Operations</title>
    <content>
      <para>The cursor library supports calling <legacyBold>SQLFetchScroll</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> of SQL_FETCH_BOOKMARK. It also supports specifying an offset in the <legacyItalic>FetchOffset</legacyItalic> argument that can be used in the bookmark operation. This is the only bookmark operation the cursor library supports. The cursor library does not support calling <legacyBold>SQLBulkOperations</legacyBold>.</para>
      <para>If the application has set the SQL_ATTR_USE_BOOKMARKS statement attribute and has bound to the bookmark column, the cursor library generates a fixed-length bookmark and returns it to the application. The cursor library creates and maintains the bookmarks that it uses; it does not use bookmarks maintained at the data source. When <legacyBold>SQLFetchScroll</legacyBold> is called to retrieve a block of data that has already been fetched from the data source, it retrieves the data from the cursor library cache. As a result, the bookmark used in a call to <legacyBold>SQLFetchScroll</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> of SQL_FETCH_BOOKMARK must be created and maintained by the cursor library.</para>
    </content>
  </section>
  <section>
    <title>Interaction with Other Functions</title>
    <content>
      <para>An application must call <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> before it prepares or executes any positioned update or delete statements.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>