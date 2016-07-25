---
title: "Block Cursors, Scrollable Cursors, and Backward Compatibility for ODBC 3.x Applications"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82f6cf68-cfde-4417-9788-d6382ca14bf8
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Block Cursors, Scrollable Cursors, and Backward Compatibility for ODBC 3.x Applications
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The existence of both <legacyBold>SQLFetchScroll</legacyBold> and <legacyBold>SQLExtendedFetch</legacyBold> represents the first clear split in ODBC between the Application Programming Interface (API), which is the set of functions the application calls, and the Service Provider Interface (SPI), which is the set of functions the driver implements. This split is required to balance the requirement in ODBC 3.<legacyItalic>x</legacyItalic>, which uses <legacyBold>SQLFetchScroll</legacyBold>, to align with the standards and be compatible with ODBC 2.<legacyItalic>x</legacyItalic>, which uses <legacyBold>SQLExtendedFetch</legacyBold>.</para>
    <para>The ODBC 3<legacyItalic>.x</legacyItalic> API, which is the set of functions the application calls, includes <legacyBold>SQLFetchScroll</legacyBold> and related statement attributes. The ODBC 3<legacyItalic>.x </legacyItalic>SPI, which is the set of functions the driver implements, includes <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLExtendedFetch</legacyBold>, and related statement attributes. Because ODBC does not formally enforce this split between the API and the SPI, it is possible for ODBC 3<legacyItalic>.x</legacyItalic> applications to call <legacyBold>SQLExtendedFetch</legacyBold> and related statement attributes. However, there is no reason for ODBC 3<legacyItalic>.x</legacyItalic> applications to do this. For more information about APIs and SPIs, see the introduction to <legacyLink xlink:href="2604f492-587b-4a51-9876-59a7870b3ef2">ODBC Architecture</legacyLink>.</para>
    <para>For information about how the ODBC 3.<legacyItalic>x</legacyItalic> Driver Manager maps calls to ODBC 2.<legacyItalic>x</legacyItalic> and ODBC 3.<legacyItalic>x</legacyItalic> drivers, and what functions and statement attributes an ODBC 3.<legacyItalic>x</legacyItalic> driver should implement for block and scrollable cursors, see <legacyLink xlink:href="75dcdea6-ff6b-4ac8-aa11-a1f9edbeb8e6">What the Driver Does</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
    <para>The following table summarizes what functions and statement attributes an ODBC 3.<legacyItalic>x</legacyItalic> application should use with block and scrollable cursors. It also lists changes between ODBC 2.<legacyItalic>x</legacyItalic> and ODBC 3.<legacyItalic>x</legacyItalic> in this area that ODBC 3.<legacyItalic>x</legacyItalic> applications should be aware of to be compatible with ODBC 2.<legacyItalic>x</legacyItalic> drivers.</para>
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
            <para>Points to the bookmark to use with <legacyBold>SQLFetchScroll</legacyBold>.</para>
            <para>When an application sets this in an ODBC 2.<legacyItalic>x</legacyItalic> driver, this must point to a fixed-length bookmark.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROW_STATUS_PTR</para>
          </TD>
          <TD>
            <para>Points to the row status array filled by <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, and <legacyBold>SQLSetPos</legacyBold>.</para>
            <para>If an application sets this in an ODBC 2.<legacyItalic>x</legacyItalic> driver and calls <legacyBold>SQLBulkOperation</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD before calling <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLFetch</legacyBold>, or <legacyBold>SQLExtendedFetch</legacyBold>, SQLSTATE HY011 (Attribute cannot be set now) is returned.</para>
            <para>When an application calls <legacyBold>SQLFetch</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver, <legacyBold>SQLFetch</legacyBold> is mapped to <legacyBold>SQLExtendedFetch</legacyBold> and therefore returns values in this array.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROWS_FETCHED_PTR</para>
          </TD>
          <TD>
            <para>Points to the buffer in which <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> return the number of rows fetched.</para>
            <para>When an application calls <legacyBold>SQLFetch</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver, <legacyBold>SQLFetch</legacyBold> is mapped to <legacyBold>SQLExtendedFetch</legacyBold> and therefore returns a value in this buffer.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROW_ARRAY_SIZE</para>
          </TD>
          <TD>
            <para>Sets the rowset size.</para>
            <para>If an application calls <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD in an ODBC 2.<legacyItalic>x</legacyItalic> driver, SQL_ROWSET_SIZE will be used for the call, not SQL_ATTR_ROW_ARRAY_SIZE, because the call is mapped to <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD, which uses SQL_ROWSET_SIZE.</para>
            <para>Calling <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD or <legacyBold>SQLExtendedFetch</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver uses SQL_ROWSET_SIZE.</para>
            <para>Calling <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver uses SQL_ATTR_ROW_ARRAY_SIZE.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLBulkOperations</legacyBold>             </para>
          </TD>
          <TD>
            <para>Performs insert and bookmark operations. When <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD is called in an ODBC 2.<legacyItalic>x</legacyItalic> driver, it is mapped to <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD. The following are implementation details:</para>
            <list class="bullet">
              <listItem>
                <para>When working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, an application must use only the implicitly allocated ARD associated with the <legacyItalic>StatementHandle</legacyItalic>; it cannot allocate another ARD for adding rows, because explicit descriptor operations are not supported in an ODBC 2.<legacyItalic>x</legacyItalic> driver. An application must use <legacyBold>SQLBindCol</legacyBold> to bind to the ARD, not <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>.</para>
              </listItem>
              <listItem>
                <para>When calling an ODBC 3.<legacyItalic>x</legacyItalic> driver, an application can call <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD before calling <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. When calling an ODBC 2.<legacyItalic>x</legacyItalic> driver, an application must call <legacyBold>SQLFetchScroll</legacyBold> before calling <legacyBold>SQLBulkOperations </legacyBold>with an Operation of SQL_ADD.</para>
              </listItem>
            </list>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLFetch</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns the next rowset. The following are implementation details:</para>
            <list class="bullet">
              <listItem>
                <para>When an application calls <legacyBold>SQLFetch</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver, it is mapped to <legacyBold>SQLExtendedFetch</legacyBold>.</para>
              </listItem>
              <listItem>
                <para>When an application calls <legacyBold>SQLFetch</legacyBold> in an ODBC 3.<legacyItalic>x</legacyItalic> driver, it returns the number of rows specified with the SQL_ATTR_ROW_ARRAY_SIZE statement attribute.</para>
              </listItem>
            </list>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLFetchScroll</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns the specified rowset. The following are implementation details:</para>
            <list class="bullet">
              <listItem>
                <para>When an application calls <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver, it returns SQLSTATE 01S01 (Error in row) before each error that applies to a single row. It does this only because the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maps this to <legacyBold>SQLExtendedFetch</legacyBold> and <legacyBold>SQLExtendedFetch</legacyBold> returns this SQLSTATE. When an application calls <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 3.<legacyItalic>x</legacyItalic> driver, it never returns SQLSTATE 01S01 (Error in row).</para>
              </listItem>
              <listItem>
                <para>When an application calls <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver with <legacyItalic>FetchOrientation</legacyItalic> set to SQL_FETCH_BOOKMARK, the <legacyItalic>FetchOffset</legacyItalic> argument must be set to 0. SQLSTATE HYC00 (Optional feature not implemented) is returned if offset-based bookmark fetching is attempted with an ODBC 2.<legacyItalic>x</legacyItalic> driver.</para>
              </listItem>
            </list>
          </TD>
        </tr>
      </tbody>
    </table>
    <alert class="note">
      <para>ODBC 3.<legacyItalic>x</legacyItalic> applications should not use <legacyBold>SQLExtendedFetch</legacyBold> or the SQL_ROWSET_SIZE statement attribute. Instead, they should use <legacyBold>SQLFetchScroll</legacyBold> and the SQL_ATTR_ROW_ARRAY_SIZE statement attribute. ODBC 3.<legacyItalic>x</legacyItalic> applications should not use <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD but should use <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>