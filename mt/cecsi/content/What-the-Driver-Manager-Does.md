---
title: "What the Driver Manager Does"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57f65c38-d9ee-46c8-9051-128224a582c6
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# What the Driver Manager Does
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table summarizes how the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maps calls to ODBC 2.<legacyItalic>x</legacyItalic> and ODBC 3<legacyItalic>.x</legacyItalic> drivers.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Function or</para>
              <para>statement attribute</para>
            </TD>
            <TD>
              <para>Comments</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_ATTR_FETCH_BOOKMARK_PTR</para>
            </TD>
            <TD>
              <para>Points to the bookmark to use with <legacyBold>SQLFetchScroll</legacyBold>. The following are implementation details:</para>
              <list class="bullet">
                <listItem>
                  <para>When an application sets this in an ODBC 2.<legacyItalic>x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager caches it. It dereferences the pointer and passes the value to the ODBC 2.<legacyItalic>x</legacyItalic> driver in the <legacyItalic>FetchOffset</legacyItalic> argument of <legacyBold>SQLExtendedFetch </legacyBold>when<legacyBold> SQLFetchScroll</legacyBold> is later called by the application.</para>
                </listItem>
                <listItem>
                  <para>When an application sets this in an ODBC 3<legacyItalic>.x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager passes the call to the driver.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_STATUS_PTR</para>
            </TD>
            <TD>
              <para>Points to the row status array filled by <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, and <legacyBold>SQLSetPos</legacyBold>. The following are implementation details:</para>
              <list class="bullet">
                <listItem>
                  <para>When an application sets this in an ODBC 2.<legacyItalic>x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager caches its value. It passes this value to the ODBC 2.<legacyItalic>x</legacyItalic> driver in the <legacyItalic>RowStatusArray</legacyItalic> argument of <legacyBold>SQLExtendedFetch </legacyBold>when<legacyBold> SQLFetchScroll </legacyBold>or<legacyBold> SQLFetch </legacyBold>is called.</para>
                </listItem>
                <listItem>
                  <para>When an application sets this in an ODBC 3<legacyItalic>.x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager passes the call to the driver.</para>
                </listItem>
                <listItem>
                  <para>In state S6, if an application sets SQL_ATTR_ROW_STATUS_PTR and then calls <legacyBold>SQLBulkOperations</legacyBold> (with an <legacyItalic>Operation</legacyItalic> of SQL_ADD) or <legacyBold>SQLSetPos</legacyBold> without first calling <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>, SQLSTATE HY011 (Attribute cannot be set now) is returned.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROWS_FETCHED_PTR</para>
            </TD>
            <TD>
              <para>Points to the buffer in which <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> return the number of rows fetched. The following are implementation details:</para>
              <list class="bullet">
                <listItem>
                  <para>When an application sets this in an ODBC 2.<legacyItalic>x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager caches its value. It passes this value to the ODBC 2.<legacyItalic>x</legacyItalic> driver in the <legacyItalic>RowCountPtr</legacyItalic> argument of <legacyBold>SQLExtendedFetch </legacyBold>when<legacyBold> SQLFetch </legacyBold>or<legacyBold> SQLFetchScroll </legacyBold>is called by the application.</para>
                </listItem>
                <listItem>
                  <para>When an application sets this in an ODBC 3<legacyItalic>.x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager passes the call to the driver.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_ARRAY_SIZE</para>
            </TD>
            <TD>
              <para>Sets the rowset size. The following are implementation details:</para>
              <list class="bullet">
                <listItem>
                  <para>When an application sets this in an ODBC 2.<legacyItalic>x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maps it to the SQL_ROWSET_SIZE statement attribute.</para>
                </listItem>
                <listItem>
                  <para>When an application sets this in an ODBC 3<legacyItalic>.x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager passes the call to the driver. </para>
                </listItem>
                <listItem>
                  <para>When an application working with an ODBC 3<legacyItalic>.x</legacyItalic> driver calls <legacyBold>SQLSetScrollOptions</legacyBold>, SQL_ROWSET_SIZE is set to the value in the <legacyItalic>RowsetSize</legacyItalic> argument if the underlying driver does not support <legacyBold>SQLSetScrollOptions</legacyBold>.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ROWSET_SIZE</para>
            </TD>
            <TD>
              <para>Sets the rowset size used by <legacyBold>SQLExtendedFetch </legacyBold>when<legacyBold> SQLExtendedFetch </legacyBold>is called by an ODBC 2<legacyItalic>.x</legacyItalic> application. The following are implementation details:</para>
              <list class="bullet">
                <listItem>
                  <para>When an application sets this, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager passes the call to the driver, regardless of driver version.</para>
                </listItem>
                <listItem>
                  <para>When an application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver calls <legacyBold>SQLSetScrollOptions</legacyBold>, SQL_ROWSET_SIZE is set to the value in the <legacyBold>RowsetSize</legacyBold> argument.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLBulkOperations</legacyBold>
            </para>
            </TD>
            <TD>
              <para>Performs an insert operation, or update, delete, or fetch by bookmark operations. The following are implementation details:</para>
              <list class="bullet">
                <listItem>
                  <para>When an application calls <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD in an ODBC 2.<legacyItalic>x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maps it to <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD.</para>
                </listItem>
                <listItem>
                  <para>When working with an ODBC 2.<legacyItalic>x</legacyItalic> driver that does not support <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager does not map <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD to <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD. This is because <legacyBold>SQLBulkOperations</legacyBold> cannot be called in state S7, which in ODBC 2.<legacyItalic>x</legacyItalic> was the only state in which <legacyBold>SQLSetPos</legacyBold> could be called.</para>
                </listItem>
                <listItem>
                  <para>If the application calls <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD in an ODBC 2.<legacyItalic>x</legacyItalic> driver before calling <legacyBold>SQLFetchScroll</legacyBold>, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager returns an error.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLExtendedFetch</legacyBold>
            </para>
            </TD>
            <TD>
              <para>Returns the specified rowset. Except for the restriction just noted, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager passes calls to <legacyBold>SQLExtendedFetch</legacyBold> to the driver, regardless of the driver version.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLFetch</legacyBold>
            </para>
            </TD>
            <TD>
              <para>Returns the next rowset. The following are implementation details:</para>
              <list class="bullet">
                <listItem>
                  <para>When an application calls <legacyBold>SQLFetch</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maps it to<legacyBold> SQLExtendedFetch</legacyBold>. The <legacyItalic>FetchOrientation</legacyItalic> argument of <legacyBold>SQLExtendedFetch</legacyBold> is set to SQL_FETCH_NEXT. The Driver Manager uses the cached value of the SQL_ATTR_ROW_STATUS_PTR statement attribute for the <legacyItalic>RowStatusArray</legacyItalic> argument and the cached value of the SQL_ATTR_ROWS_FETCHED_PTR statement attribute for the <legacyItalic>RowCountPtr</legacyItalic> argument.</para>
                </listItem>
                <listItem>
                  <para>An ODBC 3<legacyItalic>.x</legacyItalic> application can mix calls to <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver because the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maps <legacyBold>SQLFetch</legacyBold> to <legacyBold>SQLExtendedFetch</legacyBold> when an application calls it in an ODBC 2.<legacyItalic>x</legacyItalic> driver.</para>
                </listItem>
                <listItem>
                  <para>If an ODBC 2.<legacyItalic>x</legacyItalic> driver does not support <legacyBold>SQLExtendedFetch</legacyBold>, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager does not map <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> to <legacyBold>SQLExtendedFetch</legacyBold> when an application calls it in that driver. If the application attempts to set SQL_ATTR_ROW_ARRAY_SIZE to a value greater than 1, SQLSTATE HYC00 (Optional feature not implemented) is returned.</para>
                </listItem>
                <listItem>
                  <para>Except for the restrictions just noted, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager passes calls to <legacyBold>SQLFetch</legacyBold> to the driver, regardless of the driver version.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLFetchScroll</legacyBold>
            </para>
            </TD>
            <TD>
              <para>Returns the specified rowset. The following are implementation details:</para>
              <list class="bullet">
                <listItem>
                  <para>When an application calls <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maps it to <legacyBold>SQLExtendedFetch</legacyBold>. It uses the cached value of the SQL_ATTR_ROW_STATUS_PTR statement attribute for the <legacyItalic>RowStatusArray</legacyItalic> argument and the cached value of the SQL_ATTR_ROWS_FETCHED_PTR statement attribute for the <legacyItalic>RowCountPtr</legacyItalic> argument. If the <legacyItalic>FetchOrientation</legacyItalic> argument in <legacyBold>SQLFetchScroll</legacyBold> is SQL_FETCH_BOOKMARK, it uses the cached value of the SQL_ATTR_FETCH_BOOKMARK_PTR statement attribute for the <legacyItalic>FetchOffset</legacyItalic> argument and returns an error if the <legacyItalic>FetchOffset</legacyItalic> argument of <legacyBold>SQLFetchScroll</legacyBold> is not 0.</para>
                </listItem>
                <listItem>
                  <para>When an application calls this in an ODBC 3<legacyItalic>.x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager passes the call to the driver.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLSetPos</legacyBold>
            </para>
            </TD>
            <TD>
              <para>Performs various positioned operations. The ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager passes calls to <legacyBold>SQLSetPos</legacyBold> to the driver, regardless of the driver version.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLSetScrollOptions</legacyBold>
            </para>
            </TD>
            <TD>
              <para>When the Driver Manager maps <legacyBold>SQLSetScrollOptions</legacyBold> for an application working with an ODBC 3<legacyItalic>.x</legacyItalic> driver that does not support <legacyBold>SQLSetScrollOptions</legacyBold>, the Driver Manager sets the SQL_ROWSET_SIZE statement option, not the SQL_ATTR_ROW_ARRAY_SIZE statement attribute, to the <legacyItalic>RowsetSize</legacyItalic> argument in <legacyBold>SQLSetScrollOption</legacyBold>. As a result, <legacyBold>SQLSetScrollOptions</legacyBold> cannot be used by an application when fetching multiple rows by a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. It can be used only when fetching multiple rows by a call to <legacyBold>SQLExtendedFetch</legacyBold>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>