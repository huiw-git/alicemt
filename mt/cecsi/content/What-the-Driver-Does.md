---
title: What the Driver Does
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75dcdea6-ff6b-4ac8-aa11-a1f9edbeb8e6
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# What the Driver Does
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table summarizes what functions and statement attributes an ODBC 3<legacyItalic>.x</legacyItalic> driver should implement for block and scrollable cursors.</para>
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
            <para>SQL_ATTR_ROW_STATUS_PTR</para>
          </TD>
          <TD>
            <para>Sets the address of the row status array filled by <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold>. This array is also filled by <legacyBold>SQLSetPos</legacyBold> if <legacyBold>SQLSetPos</legacyBold> is called in statement state S6. If <legacyBold>SQLSetPos</legacyBold> is called in state S7, this array is not filled but the array pointed to by the <legacyItalic>RowStatusArray</legacyItalic> argument of <legacyBold>SQLExtendedFetch</legacyBold> is filled. For more information, see <legacyLink xlink:href="3d70e0e3-fe83-4b4d-beac-42c82495a05b">Statement Transitions</legacyLink> in Appendix B: ODBC State Transition Tables.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROWS_FETCHED_PTR</para>
          </TD>
          <TD>
            <para>Sets the address of the buffer in which <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> return the number of rows fetched. If <legacyBold>SQLExtendedFetch</legacyBold> is called, this buffer is not filled but the <legacyItalic>RowCountPtr</legacyItalic> argument points to the number of rows fetched.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROW_ARRAY_SIZE</para>
          </TD>
          <TD>
            <para>Sets the rowset size used by <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROWSET_SIZE</para>
          </TD>
          <TD>
            <para>Sets the rowset size used by <legacyBold>SQLExtendedFetch</legacyBold>. ODBC 3<legacyItalic>.x</legacyItalic> drivers implement this if they want to work with ODBC 2.<legacyItalic>x</legacyItalic> applications that call <legacyBold>SQLExtendedFetch</legacyBold> or <legacyBold>SQLSetPos</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLBulkOperations</legacyBold>             </para>
          </TD>
          <TD>
            <para>If an ODBC 3<legacyItalic>.x</legacyItalic> driver should work with ODBC 2.<legacyItalic>x</legacyItalic> applications that use <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD, the driver must support <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD in addition to <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLExtendedFetch</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns the specified rowset. ODBC 3<legacyItalic>.x</legacyItalic> drivers implement this if they want to work with ODBC 2.<legacyItalic>x</legacyItalic> applications that call <legacyBold>SQLExtendedFetch</legacyBold> or <legacyBold>SQLSetPos</legacyBold>. The following are implementation details:</para>
            <list class="bullet">
              <listItem>
                <para>The driver retrieves the rowset size from the value of the SQL_ROWSET_SIZE statement attribute.</para>
              </listItem>
              <listItem>
                <para>The driver retrieves the address of the row status array from the <legacyItalic>RowStatusArray</legacyItalic> argument, not the SQL_ATTR_ROW_STATUS_PTR statement attribute. The <legacyItalic>RowStatusArray</legacyItalic> argument in a call to <legacyBold>SQLExtendedFetch</legacyBold> must not be a null pointer. (Note that in ODBC 3<legacyItalic>.x</legacyItalic>, the SQL_ATTR_ROW_STATUS_PTR statement attribute can be a null pointer.)</para>
              </listItem>
              <listItem>
                <para>The driver retrieves the address of the rows fetched buffer from the <legacyItalic>RowCountPtr</legacyItalic> argument, not the SQL_ATTR_ROWS_FETCHED_PTR statement attribute. </para>
              </listItem>
              <listItem>
                <para>The driver returns SQLSTATE 01S01 (Error in row) to indicate that an error has occurred while rows were fetched by a call to <legacyBold>SQLExtendedFetch</legacyBold>. An ODBC 3<legacyItalic>.x</legacyItalic> driver should return SQLSTATE 01S01 (Error in row) only when <legacyBold>SQLExtendedFetch</legacyBold> is called, not when <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> is called. To preserve backward compatibility, when SQLSTATE 01S01 (Error in row) is returned by <legacyBold>SQLExtendedFetch</legacyBold>, the Driver Manager does not order status records in the error queue according to the rules stated in the "Sequence of Status Records" section of <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>.</para>
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
                <para>The driver retrieves the rowset size from the value of the SQL_ATTR_ROW_ARRAY_SIZE statement attribute.</para>
              </listItem>
              <listItem>
                <para>The driver retrieves the address of the row status array from the SQL_ATTR_ROW_STATUS_PTR statement attribute.</para>
              </listItem>
              <listItem>
                <para>The driver retrieves the address of the rows fetched buffer from the SQL_ATTR_ROWS_FETCHED_PTR statement attribute.</para>
              </listItem>
              <listItem>
                <para>The application can mix calls between <legacyBold>SQLFetchScroll</legacyBold> and <legacyBold>SQLFetch</legacyBold>.</para>
              </listItem>
              <listItem>
                <para>                   <legacyBold>SQLFetch</legacyBold> returns bookmarks if column 0 is bound.</para>
              </listItem>
              <listItem>
                <para>                   <legacyBold>SQLFetch</legacyBold> can be called to return more than one row. </para>
              </listItem>
              <listItem>
                <para>The driver does not return SQLSTATE 01S01 (Error in row) to indicate that an error has occurred while rows were fetched by a call to <legacyBold>SQLFetch</legacyBold>.</para>
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
                <para>The driver retrieves the rowset size from the SQL_ATTR_ROW_ARRAY_SIZE statement attribute.</para>
              </listItem>
              <listItem>
                <para>The driver retrieves the address of the row status array from the SQL_ATTR_ROW_STATUS_PTR statement attribute.</para>
              </listItem>
              <listItem>
                <para>The driver retrieves the address of the rows fetched buffer from the SQL_ATTR_ROWS_FETCHED_PTR statement attribute.</para>
              </listItem>
              <listItem>
                <para>The application can mix calls between <legacyBold>SQLFetchScroll</legacyBold> and <legacyBold>SQLFetch</legacyBold>. </para>
              </listItem>
              <listItem>
                <para>The driver does not return SQLSTATE 01S01 (Error in row) to indicate that an error has occurred while rows were fetched by a call to <legacyBold>SQLFetchScroll</legacyBold>.</para>
              </listItem>
            </list>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetPos</legacyBold>             </para>
          </TD>
          <TD>
            <para>Performs various positioned operations. The following are implementation details:</para>
            <list class="bullet">
              <listItem>
                <para>This can be called in statement states S6 or S7. For more details, see <legacyLink xlink:href="3d70e0e3-fe83-4b4d-beac-42c82495a05b">Statement Transitions</legacyLink> in Appendix B: ODBC State Transition Tables.</para>
              </listItem>
              <listItem>
                <para>If this is called in statement state S5 or S6, the driver retrieves the rowset size from the SQL_ATTR_ROWS_FETCHED_PTR statement attribute and the address of the row status array from the SQL_ATTR_ROW_STATUS_PTR statement attribute.</para>
              </listItem>
              <listItem>
                <para>If this is called in statement state S7, the driver retrieves the rowset size from the SQL_ROWSET_SIZE statement attribute and the address of the row status array from the <legacyItalic>RowStatusArray</legacyItalic> argument of <legacyBold>SQLExtendedFetch</legacyBold>. </para>
              </listItem>
              <listItem>
                <para>The driver returns SQLSTATE 01S01 (Error in row) only to indicate that an error has occurred while rows were fetched by a call to <legacyBold>SQLSetPos</legacyBold> to perform a bulk operation when the function is called in state S7. To preserve backward compatibility, if SQLSTATE 01S01 (Error in row) is returned by <legacyBold>SQLSetPos</legacyBold>, the Driver Manager does not order status records in the error queue according to the rules stated in the "Sequence of Status Records" section of <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>.</para>
              </listItem>
              <listItem>
                <para>If the driver should work with ODBC 2.<legacyItalic>x</legacyItalic> applications that call <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> argument of SQL_ADD, the driver must support <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> argument of SQL_ADD.</para>
              </listItem>
            </list>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>