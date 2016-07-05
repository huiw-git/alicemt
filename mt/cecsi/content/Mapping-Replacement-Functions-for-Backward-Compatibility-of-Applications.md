---
title: Mapping Replacement Functions for Backward Compatibility of Applications
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5e6d9da-76ef-42cb-b3f5-f640857df732
translation.priority.ht: 
  - en-gb
---
# Mapping Replacement Functions for Backward Compatibility of Applications
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An ODBC 3<legacyItalic>.x</legacyItalic> application working through the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager will work against an ODBC 2.<legacyItalic>x</legacyItalic> driver as long as no new features are used. Both duplicated functionality and behavioral changes do, however, affect the way that the ODBC 3.<legacyItalic>x</legacyItalic> application works on an ODBC 2.<legacyItalic>x</legacyItalic> driver. When working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, the Driver Manager maps the following ODBC 3.<legacyItalic>x</legacyItalic> functions, which have replaced one or more ODBC 2.<legacyItalic>x</legacyItalic> functions, into the corresponding ODBC 2.<legacyItalic>x</legacyItalic> functions.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ODBC 3.<legacyItalic>x</legacyItalic> function</para>
          </TD>
          <TD>
            <para>ODBC 2.<legacyItalic>x</legacyItalic> function</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>             <legacyBold>SQLAllocHandle</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLAllocEnv</legacyBold>, <legacyBold>SQLAllocConnect</legacyBold>, or <legacyBold>SQLAllocStmt</legacyBold></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLBulkOperations</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLSetPos</legacyBold>           </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLColAttribute</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLColAttributes</legacyBold>           </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLEndTran</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLTransact</legacyBold>           </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLFetch</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLExtendedFetch</legacyBold>           </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLFetchScroll</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLExtendedFetch</legacyBold>           </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLFreeHandle</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLFreeEnv</legacyBold>, <legacyBold>SQLFreeConnect</legacyBold>, or <legacyBold>SQLFreeStmt</legacyBold></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLGetConnectAttr</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLGetConnectOption</legacyBold>           </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLGetDiagRec</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLError</legacyBold>           </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLGetStmtAttr</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLGetStmtOption</legacyBold>[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLSetConnectAttr</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLSetConnectOption</legacyBold>           </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyBold>SQLSetStmtAttr</legacyBold>           </para>
          </TD>
          <TD>
            <para>             <legacyBold>SQLSetStmtOption</legacyBold>[1]</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   Other actions might also be taken, depending on the attribute being requested.</para>
  </introduction>
  <section>
    <title>SQLAllocHandle</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLAllocEnv</legacyBold>, <legacyBold>SQLAllocConnect</legacyBold>, or <legacyBold>SQLAllocStmt</legacyBold>, as appropriate. The following call to <legacyBold>SQLAllocHandle</legacyBold>:</para>
      <code>SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);</code>
      <para>will result in the Driver Manager performing the following (conceptual, no error checking) mapping:</para>
      <code>switch (HandleType) {
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")
}</code>
    </content>
  </section>
  <section>
    <title>SQLBulkOperations</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLSetPos</legacyBold>. The following call to <legacyBold>SQLBulkOperations</legacyBold>:</para>
      <code>SQLBulkOperations(hstmt, Operation);</code>
      <para>will result in the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>If the Operation argument is SQL_ADD, the Driver Manager calls <legacyBold>SQLSetPos</legacyBold> as follows: </para>
          <code>SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);</code>
        </listItem>
        <listItem>
          <para>If the Operation argument is not SQL_ADD, the driver returns SQLSTATE HY092 (Invalid attribute/option identifier).</para>
        </listItem>
        <listItem>
          <para>If the application attempts to change the SQL_ATTR_ROW_STATUS_PTR between calls to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> and <legacyBold>SQLBulkOperations</legacyBold>, the Driver Manager will return SQLSTATE HY011 (Attribute cannot be set now).</para>
        </listItem>
        <listItem>
          <para>If the Operation argument is SQL_ADD, the application must call <legacyBold>SQLBindCol</legacyBold> to bind the data to be inserted. It cannot call <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold> to bind the data to be inserted.</para>
        </listItem>
        <listItem>
          <para>If the Operation argument is SQL_ADD and the number of rows to be inserted is not the same as the current rowset size, <legacyBold>SQLSetStmtAttr</legacyBold> must be called to set the SQL_ATTR_ROW_ARRAY_SIZE statement attribute to the number of rows to be inserted before calling <legacyBold>SQLBulkOperations</legacyBold>. To revert back to the previous rowset size, the application must set the SQL_ATTR_ROW_ARRAY_SIZE statement attribute before <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> is called.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>SQLColAttribute</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLColAttributes</legacyBold>. The following call to <legacyBold>SQLColAttribute</legacyBold>:</para>
      <code>SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);</code>
      <para>will result in the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>If <legacyItalic>FieldIdentifier</legacyItalic> is one of the following: </para>
          <para>SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX, or SQL_DESC_LOCAL_TYPE_NAME  </para>
          <para>the Driver Manager returns SQL_ERROR with SQLSTATE HY091 (Invalid descriptor field identifier). No further rules of this section apply. </para>
        </listItem>
        <listItem>
          <para>The Driver Manager maps SQL_COLUMN_COUNT, SQL_COLUMN_NAME, or SQL_COLUMN_NULLABLE to SQL_DESC_COUNT, SQL_DESC_NAME, or SQL_DESC_NULLABLE, respectively. (An ODBC 2<legacyItalic>.x</legacyItalic> driver need only support SQL_COLUMN_COUNT, SQL_COLUMN_NAME, and SQL_COLUMN_NULLABLE, not SQL_DESC_COUNT, SQL_DESC_NAME, and SQL_DESC_NULLABLE.) The call to SQLColAttribute is mapped to: </para>
          <code>SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);</code>
        </listItem>
        <listItem>
          <para>All other <legacyItalic>FieldIdentifier</legacyItalic> values are passed through to the driver, with <legacyBold>SQLColAttribute</legacyBold> mapped to <legacyBold>SQLColAttributes</legacyBold> as shown previously.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>BufferLength</legacyItalic> is less than 0, the Driver Manager returns SQL_ERROR with SQLSTATE HY090 (Invalid string or buffer length). No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>FieldIdentifier</legacyItalic> is SQL_DESC_CONCISE_TYPE and the returned type is a concise datetime data type, the Driver Manager maps the return values for date, time, and timestamp codes.</para>
        </listItem>
        <listItem>
          <para>The Driver Manager performs necessary checks to see whether SQLSTATE HY010 (Function sequence error) needs to be raised. If so, the Driver Manager returns SQL_ERROR and SQLSTATE HY010 (Function sequence error). No further rules of this section apply.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>SQLEndTran</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLTransact</legacyBold>. The following call to <legacyBold>SQLEndTran</legacyBold>:</para>
      <code>SQLEndTran(HandleType, Handle, CompletionType);</code>
      <para>will result in the Driver Manager performing the following (conceptual, no error checking) mapping:</para>
      <code>switch (HandleType) {
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")
}</code>
    </content>
  </section>
  <section>
    <title>SQLFetch</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLExtendedFetch</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> argument of SQL_FETCH_NEXT. The following call to <legacyBold>SQLFetch</legacyBold>:</para>
      <code>SQLFetch (StatementHandle);</code>
      <para>will result in the Driver Manager calling <legacyBold>SQLExtendedFetch</legacyBold>, as follows:</para>
      <code>rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &amp;RowCount, RowStatusArray);</code>
      <para>In this call, the <legacyItalic>pcRow</legacyItalic> argument is set to the value that the application sets the SQL_ATTR_ROWS_FETCHED_PTR statement attribute to through a call to <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
      <alert class="note">
        <para>When the application calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_ROW_STATUS_PTR to point to a status array, the Driver Manager caches the pointer. <legacyItalic>RowStatusArray</legacyItalic> can be equal to a null pointer.</para>
      </alert>
      <para>If the driver does not support <legacyBold>SQLExtendedFetch</legacyBold> and the cursor library is loaded, the Driver Manager uses the cursor library's <legacyBold>SQLExtendedFetch</legacyBold> to map <legacyBold>SQLFetch</legacyBold> to <legacyBold>SQLExtendedFetch</legacyBold>. If the driver does not support <legacyBold>SQLExtendedFetch</legacyBold> and the cursor library is not loaded, the Driver Manager passes the call to <legacyBold>SQLFetch</legacyBold> through to the driver. If the application calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_ROW_STATUS_PTR, the Driver Manager ensures that the array is populated. If the application calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_ROWS_FETCHED_PTR, the Driver Manager sets this field to 1.</para>
    </content>
  </section>
  <section>
    <title>SQLFetchScroll</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLExtendedFetch</legacyBold>. The following call to <legacyBold>SQLFetchScroll</legacyBold>:</para>
      <code>SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);</code>
      <para>will result in the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>When the application calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_ROW_STATUS_PTR (which sets the SQL_DESC_ARRAY_STATUS_PTR field in the IRD) to point to a status array, the Driver Manager caches this pointer. Let this pointer be <legacyItalic>RowStatusArray</legacyItalic>; otherwise, let <legacyItalic>RowStatusArray</legacyItalic> be equal to a null pointer. If the <legacyItalic>RowStatusArray</legacyItalic> argument is set to a null pointer, the Driver Manager generates a row-status array.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>FetchOrientation</legacyItalic> is not one of SQL_FETCH_NEXT, SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST, or SQL_FETCH_BOOKMARK, the Driver Manager returns with SQL_ERROR and SQLSTATE HY106 (Fetch type out of range). No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>Case:</para>
        </listItem>
      </list>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>FetchOrientation</legacyItalic> is equal to SQL_FETCH_BOOKMARK, then: </para>
          <list class="bullet">
            <listItem>
              <para>If <legacyBold>SQLSetStmtAttr</legacyBold> was called earlier to set the value of SQL_ATTR_FETCH_BOOKMARK_PTR, then let <legacyItalic>Bmk</legacyItalic> be the value obtained by dereferencing the pointer SQL_DESC_FETCH_BOOKMARK_PTR.</para>
            </listItem>
            <listItem>
              <para>Otherwise, return SQL_ERROR with SQLSTATE HY111 (Invalid bookmark value). No further rules of this section apply.</para>
            </listItem>
          </list>
          <para>The Driver Manager now calls <legacyBold>SQLExtendedFetch</legacyBold>, as follows:  </para>
          <code>rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);</code>
        </listItem>
        <listItem>
          <para>Otherwise, the Driver Manager calls <legacyBold>SQLExtendedFetch</legacyBold>, as follows: </para>
          <code>rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);</code>
          <para>In these calls, the <legacyItalic>pcRow</legacyItalic> argument is set to the value that the application sets the SQL_ATTR_ROWS_FETCHED_PTR statement attribute to through a call to <legacyBold>SQLSetStmtAttr</legacyBold>. </para>
        </listItem>
        <listItem>
          <para>SQL_ATTR_ROW_ARRAY_SIZE is mapped to SQL_ROWSET_SIZE.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>rc</legacyItalic> is equal to SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, and if <legacyItalic>FetchOrientation</legacyItalic> is equal to SQL_FETCH_BOOKMARK and <legacyItalic>FetchOffset</legacyItalic> is not equal to 0, then the Driver Manager posts a warning, SQLSTATE 01S10 (Attempt to fetch by a bookmark offset, offset value ignored), and returns SQL_SUCCESS_WITH_INFO.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>SQLFreeHandle</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLFreeEnv</legacyBold>, <legacyBold>SQLFreeConnect</legacyBold>, or <legacyBold>SQLFreeStmt</legacyBold> as appropriate. The following call to <legacyBold>SQLFreeHandle</legacyBold>:</para>
      <code>SQLFreeHandle(HandleType, Handle);</code>
      <para>will result in the Driver Manager performing the following (conceptual, no error checking) mapping:</para>
      <code>switch (HandleType) {
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")
}</code>
    </content>
  </section>
  <section>
    <title>SQLGetConnectAttr</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLGetConnectOption</legacyBold>. The following call to <legacyBold>SQLGetConnectAttr</legacyBold>:</para>
      <code>SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);</code>
      <para>will result in the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is not a driver-defined connection or statement attribute and is not an attribute defined in ODBC 2.<legacyItalic>x</legacyItalic>, the Driver Manager returns SQL_ERROR with SQLSTATE HY092 (Invalid attribute/option identifier). No further rules in this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is equal to SQL_ATTR_AUTO_IPD or SQL_ATTR_METADATA_ID, the Driver Manager returns SQL_ERROR with SQLSTATE HY092 (Invalid attribute/option identifier).</para>
        </listItem>
        <listItem>
          <para>The Driver Manager performs necessary checks to see if SQLSTATE 08003 (Connection not open) or SQLSTATE HY010 (Function sequence error) needs to be raised. If so, the Driver Manager returns SQL_ERROR and posts the appropriate error message. No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>The Driver Manager calls <legacyBold>SQLGetConnectOption</legacyBold> as follows: </para>
          <code>SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);</code>
          <para>Note that the <legacyItalic>BufferLength</legacyItalic> and <legacyItalic>StringLengthPtr</legacyItalic> are ignored. </para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>SQLGetData</title>
    <content>
      <para>When an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2<legacyItalic>.x</legacyItalic> driver calls <legacyBold>SQLGetData</legacyBold> with the <legacyItalic>ColumnNumber</legacyItalic> argument equal to 0, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maps this to a call to <legacyBold>SQLGetStmtOption</legacyBold> with the <legacyItalic>Option</legacyItalic> attribute set to SQL_GET_BOOKMARK.</para>
    </content>
  </section>
  <section>
    <title>SQLGetStmtAttr</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLGetStmtOption</legacyBold>. The following call to <legacyBold>SQLGetStmtAttr</legacyBold>:</para>
      <code>SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);</code>
      <para>will result in the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is not a driver-defined connection or statement attribute and is not an attribute defined in ODBC 2.<legacyItalic>x</legacyItalic>, the Driver Manager returns SQL_ERROR with SQLSTATE HY092 (Invalid attribute/option identifier). No further rules in this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is one of the following: </para>
          <para>SQL_ATTR_APP_ROW_DESC</para>
          <para>SQL_ATTR_APP_PARAM_DESC</para>
          <para>SQL_ATTR_AUTO_IPD</para>
          <para>SQL_ATTR_ROW_BIND_TYPE</para>
          <para>SQL_ATTR_IMP_ROW_DESC</para>
          <para>SQL_ATTR_IMP_PARAM_DESC</para>
          <para>SQL_ATTR_METADATA_ID</para>
          <para>SQL_ATTR_PARAM_BIND_TYPE</para>
          <para>SQL_ATTR_PREDICATE_PTR</para>
          <para>SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR</para>
          <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR</para>
          <para>SQL_ATTR_ROW_BIND_OFFSET_PTR</para>
          <para>SQL_ATTR_ROW_OPERATION_PTR</para>
          <para>SQL_ATTR_PARAM_OPERATION_PTR  </para>
          <para>the Driver Manager returns SQL_ERROR with SQLSTATE HY092 (Invalid attribute/option identifier). No further rules of this section apply. </para>
        </listItem>
        <listItem>
          <para>The Driver Manager performs necessary checks to see whether SQLSTATE HY010 (Function sequence error) needs to be raised. If so, the Driver Manager returns SQL_ERROR and SQLSTATE HY010 (Function sequence error). No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is equal to SQL_ATTR_ROWS_FETCHED_PTR, the Driver Manager returns a pointer to the internal Driver Manager variable <legacyItalic>cRow</legacyItalic>, which it has used or will use in a call to <legacyBold>SQLExtendedFetch</legacyBold>. No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is equal to SQL_DESC_FETCH_BOOKMARK_PTR, the Driver Manager returns the appropriate pointer that it had cached during a call to <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is equal to SQL_ATTR_ROW_STATUS_PTR, the Driver Manager returns the appropriate pointer that it had cached during a call to <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>The Driver Manager calls <legacyBold>SQLGetStmtOption</legacyBold> as follows: </para>
          <code>SQLGetStmtOption (hstmt, fOption, pvParam);</code>
          <para>where <legacyItalic>hstmt</legacyItalic>, <legacyItalic>fOption</legacyItalic>, and <legacyItalic>pvParam</legacyItalic> will be set to the values of <legacyItalic>StatementHandle</legacyItalic>, <legacyItalic>Attribute</legacyItalic>, and <legacyItalic>ValuePtr</legacyItalic>, respectively. The <legacyItalic>BufferLength</legacyItalic> and <legacyItalic>StringLengthPtr</legacyItalic> are ignored. </para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>SQLSetConnectAttr</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLSetConnectOption</legacyBold>. The following call to <legacyBold>SQLSetConnectAttr</legacyBold>:</para>
      <code>SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);</code>
      <para>will result in the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is not a driver-defined connection or statement attribute and is not an attribute defined in ODBC 2.<legacyItalic>x</legacyItalic>, the Driver Manager returns SQL_ERROR with SQLSTATE HY092 (Invalid attribute/option identifier). No further rules in this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is equal to SQL_ATTR_AUTO_IPD, the Driver Manager returns SQL_ERROR with SQLSTATE HY092 (Invalid attribute/option identifier).</para>
        </listItem>
        <listItem>
          <para>The Driver Manager performs necessary checks to see whether SQLSTATE 08003 (Connection not open) or SQLSTATE HY010 (Function sequence error) need to be raised. If one of these errors needs to be raised, the Driver Manager returns SQL_ERROR and posts the appropriate error message. No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>The Driver Manager calls <legacyBold>SQLSetConnectOption</legacyBold> as follows: </para>
          <code>SQLSetConnectOption (hdbc, fOption, vParam);</code>
          <para>where <legacyItalic>hdbc</legacyItalic>, <legacyItalic>fOption</legacyItalic>, and <legacyItalic>vParam</legacyItalic> will be set to the values of <legacyItalic>ConnectionHandle</legacyItalic>, <legacyItalic>Attribute</legacyItalic>, and <legacyItalic>ValuePtr</legacyItalic>, respectively. <legacyItalic>StringLengthPtr</legacyItalic> is ignored. </para>
        </listItem>
      </list>
      <alert class="note">
        <para>The ability to set statement attributes on the connection level has been deprecated. Statement attributes should never be set on the connection level by an ODBC 3.<legacyItalic>x</legacyItalic> application.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>SQLSetStmtAttr</title>
    <content>
      <para>The Driver Manager maps this to <legacyBold>SQLSetStmtOption</legacyBold>. The following call to <legacyBold>SQLSetStmtAttr</legacyBold>:</para>
      <code>SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);</code>
      <para>will result in the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is not a driver-defined connection or statement attribute and is not an attribute defined in ODBC 2.<legacyItalic>x</legacyItalic>, the Driver Manager returns SQL_ERROR with SQLSTATE HY092 (Invalid attribute/option identifier). No further rules in this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is one of the following: </para>
          <para>SQL_ATTR_APP_ROW_DESC</para>
          <para>SQL_ATTR_APP_PARAM_DESC</para>
          <para>SQL_ATTR_AUTO_IPD</para>
          <para>SQL_ATTR_ROW_BIND_TYPE</para>
          <para>SQL_ATTR_IMP_ROW_DESC</para>
          <para>SQL_ATTR_IMP_PARAM_DESC</para>
          <para>SQL_ATTR_METADATA_ID</para>
          <para>SQL_ATTR_PARAM_BIND_TYPE</para>
          <para>SQL_ATTR_PREDICATE_PTR</para>
          <para>SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR</para>
          <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR</para>
          <para>SQL_ATTR_ROW_BIND_OFFSET_PTR</para>
          <para>SQL_ATTR_ROW_OPERATION_PTR</para>
          <para>SQL_ATTR_PARAM_OPERATION_PTR</para>
          <para>the Driver Manager returns SQL_ERROR with SQLSTATE HY092 (Invalid attribute/option identifier). No further rules of this section apply. </para>
        </listItem>
        <listItem>
          <para>The Driver Manager performs the necessary checks to see whether SQLSTATE HY010 (Function sequence error) need to be raised. If so, the Driver Manager returns SQL_ERROR and SQLSTATE HY010 (Function sequence error). No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is equal to SQL_ATTR_PARAMSET_SIZE or SQL_ATTR_PARAMS_PROCESSED_PTR, see the section "Mappings for Handling Parameter Arrays," later in this topic. No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is equal to SQL_ATTR_ROWS_FETCHED_PTR, the Driver Manager caches the pointer value for later use with <legacyBold>SQLFetchScroll</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is equal to SQL_ATTR_ROW_STATUS_PTR, the Driver Manager caches the pointer value for later use with <legacyBold>SQLFetchScroll</legacyBold> or <legacyBold>SQLSetPos</legacyBold>. No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>Attribute</legacyItalic> is equal to SQL_ATTR_FETCH_BOOKMARK_PTR, the Driver Manager caches <legacyItalic>ValuePtr</legacyItalic> and will use the cached value later in a call to <legacyBold>SQLFetchScroll</legacyBold>. No further rules of this section apply.</para>
        </listItem>
        <listItem>
          <para>The Driver Manager calls <legacyBold>SQLSetStmtOption</legacyBold> as follows: </para>
          <code>SQLSetStmtOption (hstmt, fOption, vParam);</code>
          <para>where <legacyItalic>hstmt</legacyItalic>, <legacyItalic>fOption</legacyItalic>, and <legacyItalic>vParam</legacyItalic> will be set to the values of <legacyItalic>StatementHandle</legacyItalic>, <legacyItalic>Attribute</legacyItalic>, and <legacyItalic>ValuePtr</legacyItalic>, respectively. The <legacyItalic>StringLength</legacyItalic> argument is ignored.  </para>
          <para>If an ODBC 2.<legacyItalic>x</legacyItalic> driver supports character-string, driver-specific statement options, an ODBC 3.<legacyItalic>x</legacyItalic> application should call <legacyBold>SQLSetStmtOption</legacyBold> to set those options. </para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Mappings for Handling Parameter Arrays</title>
    <content>
      <para>When the application calls:</para>
      <code>SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);</code>
      <para>the Driver Manager calls:</para>
      <code>SQLParamOptions (StatementHandle, Size, &amp;RowCount);</code>
      <para>The Driver Manager later returns a pointer to this variable when the application calls <legacyBold>SQLGetStmtAttr</legacyBold> to retrieve SQL_ATTR_PARAMS_PROCESSED_PTR. The Driver Manager cannot change this internal variable until the statement handle is returned to the prepared or allocated state.</para>
      <para>An ODBC 3.<legacyItalic>x</legacyItalic> application can call <legacyBold>SQLGetStmtAttr</legacyBold> to obtain the value of SQL_ATTR_PARAMS_PROCESSED_PTR even though it has not explicitly set the SQL_DESC_ARRAY_SIZE field in the APD. This situation could arise, for example, if the application has a generic routine that checks for the current "row" of parameters being processed when <legacyBold>SQLExecute</legacyBold> returns SQL_NEED_DATA. This routine is invoked whether or not the SQL_DESC_ARRAY_SIZE is 1 or is greater than 1. To account for this, the Driver Manager will need to define this internal variable whether or not the application has called <legacyBold>SQLSetStmtAttr</legacyBold> to set the SQL_DESC_ARRAY_SIZE field in APD. If SQL_DESC_ARRAY_SIZE has not been set, the Driver Manager has to make sure that this variable contains the value 1 prior to returning from <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold>.</para>
    </content>
  </section>
  <section>
    <title>Error Handling</title>
    <content>
      <para>In ODBC 3.<legacyItalic>x</legacyItalic>, calling <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> populates the SQL_DESC_ARRAY_STATUS_PTR in the IRD, and the SQL_DIAG_ROW_NUMBER field of a given diagnostic record contains the number of the row in the rowset that this record pertains to. Using this, the application can correlate an error message with a given row position.</para>
      <para>An ODBC 2.<legacyItalic>x</legacyItalic> driver will be unable to provide this functionality. However, it will provide error demarcation with SQLSTATE 01S01 (Error in row). An ODBC 3.<legacyItalic>x</legacyItalic> application that is using <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> while going against an ODBC 2.<legacyItalic>x</legacyItalic> driver needs to be aware of this fact. Note also that such an application will be unable to call <legacyBold>SQLGetDiagField</legacyBold> to actually get the SQL_DIAG_ROW_NUMBER field anyway. An ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver will be able to call <legacyBold>SQLGetDiagField</legacyBold> only with a <legacyItalic>DiagIdentifier</legacyItalic> argument of SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE, or SQL_DIAG_SQLSTATE. The ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maintains the diagnostic data structure when working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, but the ODBC 2.<legacyItalic>x</legacyItalic> driver returns only these four fields.</para>
      <para>When an ODBC 2.<legacyItalic>x</legacyItalic> application is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, if an operation can cause multiple errors to be returned by the Driver Manager, different errors may be returned by the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager than by the ODBC 2.<legacyItalic>x</legacyItalic> Driver Manager.</para>
    </content>
  </section>
  <section>
    <title>Mappings for Bookmark Operations</title>
    <content>
      <para>The ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager performs the following mappings when an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver performs bookmark operations.</para>
    </content>
    <sections>
      <section>
        <title>SQLBindCol</title>
        <content>
          <para>When an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver calls <legacyBold>SQLBindCol</legacyBold> to bind to column 0 with <legacyItalic>fCType</legacyItalic> equal to SQL_C_VARBOOKMARK, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager checks to see whether the <legacyItalic>BufferLength</legacyItalic> argument is less than 4 or greater than 4, and if so, returns SQLSTATE HY090 (Invalid string or buffer length). If the <legacyItalic>BufferLength</legacyItalic> argument is equal to 4, the Driver Manager calls <legacyBold>SQLBindCol</legacyBold> in the driver, after replacing <legacyItalic>fCType</legacyItalic> with SQL_C_BOOKMARK.</para>
        </content>
      </section>
      <section>
        <title>SQLColAttribute</title>
        <content>
          <para>When an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver calls <legacyBold>SQLColAttribute</legacyBold> with the <legacyItalic>ColumnNumber</legacyItalic> argument set to 0, the Driver Manager returns the <legacyItalic>FieldIdentifier</legacyItalic> values listed in the following table.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>                     <legacyItalic>FieldIdentifier</legacyItalic>                   </para>
                </TD>
                <TD>
                  <para>Value</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>SQL_DESC_AUTO_UNIQUE_VALUE</para>
                </TD>
                <TD>
                  <para>SQL_FALSE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_CASE_SENSITIVE</para>
                </TD>
                <TD>
                  <para>SQL_FALSE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_CATALOG_NAME</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_CONCISE_TYPE</para>
                </TD>
                <TD>
                  <para>SQL_BINARY</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_COUNT</para>
                </TD>
                <TD>
                  <para>The same value returned by <legacyBold>SQLNumResultCols</legacyBold></para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_DATETIME_INTERVAL_CODE</para>
                </TD>
                <TD>
                  <para>0</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_DISPLAY_SIZE</para>
                </TD>
                <TD>
                  <para>8</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_FIXED_PREC_SCALE</para>
                </TD>
                <TD>
                  <para>SQL_FALSE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_LABEL</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_LENGTH</para>
                </TD>
                <TD>
                  <para>0</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_LITERAL_PREFIX</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_LITERAL_SUFFIX</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_LOCAL_TYPE_NAME</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_NAME</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_NULLABLE</para>
                </TD>
                <TD>
                  <para>SQL_NO_NULLS</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_OCTET_LENGTH</para>
                </TD>
                <TD>
                  <para>4</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_PRECISION</para>
                </TD>
                <TD>
                  <para>4</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_SCALE</para>
                </TD>
                <TD>
                  <para>0</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_SCHEMA_NAME</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_SEARCHABLE</para>
                </TD>
                <TD>
                  <para>SQL_PRED_NONE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_TABLE_NAME</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_TYPE</para>
                </TD>
                <TD>
                  <para>SQL_BINARY</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_TYPE_NAME</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_UNNAMED</para>
                </TD>
                <TD>
                  <para>SQL_UNNAMED</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_UNSIGNED</para>
                </TD>
                <TD>
                  <para>SQL_FALSE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DESC_UPDATEABLE</para>
                </TD>
                <TD>
                  <para>SQL_ATTR_READ_ONLY</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <section>
        <title>SQLDescribeCol</title>
        <content>
          <para>When an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver calls <legacyBold>SQLDescribeCol</legacyBold> with the <legacyItalic>ColumnNumber</legacyItalic> argument set to 0, the Driver Manager returns the values listed in the following table.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Buffer</para>
                </TD>
                <TD>
                  <para>Value</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>ColumnName</para>
                </TD>
                <TD>
                  <para>"" (empty string)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>*NameLengthPtr</para>
                </TD>
                <TD>
                  <para>0</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>*DataTypePtr</para>
                </TD>
                <TD>
                  <para>SQL_BINARY</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>*ColumnSizePtr</para>
                </TD>
                <TD>
                  <para>4</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>*DecimalDigitsPtr</para>
                </TD>
                <TD>
                  <para>0</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>*NullablePtr</para>
                </TD>
                <TD>
                  <para>SQL_NO_NULLS</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <section>
        <title>SQLGetData</title>
        <content>
          <para>When an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver makes the following call to <legacyBold>SQLGetData</legacyBold> to retrieve a bookmark:</para>
          <code>SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)</code>
          <para>the call is mapped to <legacyBold>SQLGetStmtOption</legacyBold> with an <legacyItalic>fOption</legacyItalic> of SQL_GET_BOOKMARK, as follows:</para>
          <code>SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)</code>
          <para>where <legacyItalic>hstmt</legacyItalic> and <legacyItalic>pvParam</legacyItalic> are set to the values in <legacyItalic>StatementHandle</legacyItalic> and <legacyItalic>TargetValuePtr</legacyItalic>, respectively. The bookmark is returned in the buffer pointed to by the <legacyItalic>pvParam</legacyItalic> (<legacyItalic>TargetValuePtr</legacyItalic>) argument. The value in the buffer pointed to by the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in the call to <legacyBold>SQLGetData</legacyBold> is set to 4.</para>
          <para>This mapping is necessary to account for the case in which <legacyBold>SQLFetch</legacyBold> was called prior to the call to <legacyBold>SQLGetData</legacyBold> and the ODBC 2.<legacyItalic>x</legacyItalic> driver did not support <legacyBold>SQLExtendedFetch</legacyBold>. In this case, <legacyBold>SQLFetch</legacyBold> would be passed through to the ODBC 2.<legacyItalic>x</legacyItalic> driver, in which case bookmark retrieval is not supported.</para>
          <para>             <legacyBold>SQLGetData</legacyBold> cannot be called multiple times in an ODBC 2.<legacyItalic>x</legacyItalic> driver to retrieve a bookmark in parts, so calling <legacyBold>SQLGetData</legacyBold> with the <legacyItalic>BufferLength</legacyItalic> argument set to a value less than 4 and the <legacyItalic>ColumnNumber</legacyItalic> argument set to 0 will return SQLSTATE HY090 (Invalid string or buffer length). <legacyBold>SQLGetData</legacyBold> can, however, be called multiple times to retrieve the same bookmark.</para>
        </content>
      </section>
      <section>
        <title>SQLSetStmtAttr</title>
        <content>
          <para>When an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver calls <legacyBold>SQLSetStmtAttr</legacyBold> to set the SQL_ATTR_USE_BOOKMARKS attribute to SQL_UB_VARIABLE, the Driver Manager sets the attribute to SQL_UB_ON in the underlying ODBC 2.<legacyItalic>x</legacyItalic> driver.</para>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>