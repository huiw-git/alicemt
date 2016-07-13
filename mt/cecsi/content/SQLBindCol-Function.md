---
title: SQLBindCol Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLBindCol
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 41a37655-84cd-423f-9daa-e0b47b88dc54
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLBindCol Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: ISO 92</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLBindCol</legacyBold> binds application data buffers to columns in the result set.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLBindCol</legacyBold>(
      SQLHSTMT       <parameterReference>StatementHandle</parameterReference>,
      SQLUSMALLINT   <parameterReference>ColumnNumber</parameterReference>,
      SQLSMALLINT    <parameterReference>TargetType</parameterReference>,
      SQLPOINTER     <parameterReference>TargetValuePtr</parameterReference>,
      SQLLEN         <parameterReference>BufferLength</parameterReference>,
      SQLLEN *       <parameterReference>StrLen_or_Ind</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>StatementHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Statement handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ColumnNumber</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Number of the result set column to bind. Columns are numbered in increasing column order starting at 0, where column 0 is the bookmark column. If bookmarks are not used — that is, the SQL_ATTR_USE_BOOKMARKS statement attribute is set to SQL_UB_OFF — then column numbers start at 1.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TargetType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The identifier of the C data type of the *<legacyItalic>TargetValuePtr</legacyItalic> buffer. When it is retrieving data from the data source with <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold>, the driver converts the data to this type; when it sends data to the data source with <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>, the driver converts the data from this type. For a list of valid C data types and type identifiers, see the <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink> section in Appendix D: Data Types.</para>
          <para>If the <legacyItalic>TargetType</legacyItalic> argument is an interval data type, the default interval leading precision (2) and the default interval seconds precision (6), as set in the SQL_DESC_DATETIME_INTERVAL_PRECISION and SQL_DESC_PRECISION fields of the ARD, respectively, are used for the data. If the <legacyItalic>TargetType</legacyItalic> argument is SQL_C_NUMERIC, the default precision (driver-defined) and default scale (0), as set in the SQL_DESC_PRECISION and SQL_DESC_SCALE fields of the ARD, are used for the data. If any default precision or scale is not appropriate, the application should explicitly set the appropriate descriptor field by a call to <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>.</para>
          <para>You can also specify an extended C data type. For more information, see <link xlink:href="c91bef31-3794-4736-966a-d50997b2233c">C Data Types in ODBC</link>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TargetValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Deferred Input/Output] Pointer to the data buffer to bind to the column. <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> return data in this buffer. <legacyBold>SQLBulkOperations</legacyBold> returns data in this buffer when <legacyItalic>Operation</legacyItalic> is SQL_FETCH_BY_BOOKMARK; it retrieves data from this buffer when <legacyItalic>Operation</legacyItalic> is SQL_ADD or SQL_UPDATE_BY_BOOKMARK. <legacyBold>SQLSetPos</legacyBold> returns data in this buffer when <legacyItalic>Operation</legacyItalic> is SQL_REFRESH; it retrieves data from this buffer when <legacyItalic>Operation</legacyItalic> is SQL_UPDATE.</para>
          <para>If <legacyItalic>TargetValuePtr</legacyItalic> is a null pointer, the driver unbinds the data buffer for the column. An application can unbind all columns by calling <legacyBold>SQLFreeStmt</legacyBold> with the SQL_UNBIND option. An application can unbind the data buffer for a column but still have a length/indicator buffer bound for the column, if the <legacyItalic>TargetValuePtr</legacyItalic> argument in the call to <legacyBold>SQLBindCol</legacyBold> is a null pointer but the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument is a valid value. </para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>TargetValuePtr</legacyItalic> buffer in bytes.</para>
          <para>The driver uses <legacyItalic>BufferLength</legacyItalic> to avoid writing past the end of the *<legacyItalic>TargetValuePtr</legacyItalic> buffer when it returns variable-length data, such as character or binary data. Notice that the driver counts the null-termination character when it returns character data to *<legacyItalic>TargetValuePtr</legacyItalic>. *<legacyItalic>TargetValuePtr</legacyItalic> must therefore contain space for the null-termination character or the driver will truncate the data.</para>
          <para>When the driver returns fixed-length data, such as an integer or a date structure, the driver ignores <legacyItalic>BufferLength</legacyItalic> and assumes the buffer is large enough to hold the data. Therefore, it is important for the application to allocate a large enough buffer for fixed-length data or the driver will write past the end of the buffer.</para>
          <para>
            <legacyBold>SQLBindCol</legacyBold> returns SQLSTATE HY090 (Invalid string or buffer length) when <legacyItalic>BufferLength</legacyItalic> is less than 0 but not when <legacyItalic>BufferLength</legacyItalic> is 0. However, if <legacyItalic>TargetType</legacyItalic> specifies a character type, an application should not set <legacyItalic>BufferLength</legacyItalic> to 0, because ISO CLI–compliant drivers return SQLSTATE HY090 (Invalid string or buffer length) in that case.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StrLen_or_IndPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Deferred Input/Output] Pointer to the length/indicator buffer to bind to the column. <legacyBold>SQLFetch </legacyBold>and <legacyBold>SQLFetchScroll</legacyBold> return a value in this buffer. <legacyBold>SQLBulkOperations</legacyBold> retrieves a value from this buffer when <legacyItalic>Operation</legacyItalic> is SQL_ADD, SQL_UPDATE_BY_BOOKMARK, or SQL_DELETE_BY_BOOKMARK. <legacyBold>SQLBulkOperations</legacyBold> returns a value in this buffer when <legacyItalic>Operation</legacyItalic> is SQL_FETCH_BY_BOOKMARK. <legacyBold>SQLSetPos</legacyBold> returns a value in this buffer when <legacyItalic>Operation</legacyItalic> is SQL_REFRESH; it retrieves a value from this buffer when <legacyItalic>Operation</legacyItalic> is SQL_UPDATE.</para>
          <para>
            <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, and <legacyBold>SQLSetPos</legacyBold> can return the following values in the length/indicator buffer:</para>
          <list class="bullet">
            <listItem>
              <para>The length of the data available to return</para>
            </listItem>
            <listItem>
              <para>SQL_NO_TOTAL</para>
            </listItem>
            <listItem>
              <para>SQL_NULL_DATA</para>
            </listItem>
          </list>
          <para>The application can put the following values in the length/indicator buffer for use with <legacyBold>SQLBulkOperations</legacyBold> or<legacyBold> SQLSetPos</legacyBold>:</para>
          <list class="bullet">
            <listItem>
              <para>The length of the data being sent</para>
            </listItem>
            <listItem>
              <para>SQL_NTS</para>
            </listItem>
            <listItem>
              <para>SQL_NULL_DATA</para>
            </listItem>
            <listItem>
              <para>SQL_DATA_AT_EXEC</para>
            </listItem>
            <listItem>
              <para>The result of the SQL_LEN_DATA_AT_EXEC macro</para>
            </listItem>
            <listItem>
              <para>SQL_COLUMN_IGNORE</para>
            </listItem>
          </list>
          <para>If the indicator buffer and the length buffer are separate buffers, the indicator buffer can return only SQL_NULL_DATA, whereas the length buffer can return all other values. </para>
          <para>For more information, see <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations Function</legacyLink>, <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</legacyLink>, <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</legacyLink>, and <legacyLink xlink:href="849792f1-cb1e-4bc2-b568-c0aff0b66199">Using Length/Indicator Values</legacyLink>.</para>
          <para>If <legacyItalic>StrLen_or_IndPtr</legacyItalic> is a null pointer, no length or indicator value is used. This is an error when fetching data and the data is NULL.</para>
          <para>See <link xlink:href="ed9851ce-44ee-4c8e-b626-1d0b52da30fe">ODBC 64-Bit Information</link>, if your application will run on a 64-bit operating system.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLBindCol</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLBindCol</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQLSTATE</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>01000</para>
            </TD>
            <TD>
              <para>General warning</para>
            </TD>
            <TD>
              <para>Driver-specific informational message. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07006</para>
            </TD>
            <TD>
              <para>Restricted data type attribute violation</para>
            </TD>
            <TD>
              <para>(DM) The <legacyItalic>ColumnNumber</legacyItalic> argument was 0, and the <legacyItalic>TargetType</legacyItalic> argument was not SQL_C_BOOKMARK or SQL_C_VARBOOKMARK.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07009</para>
            </TD>
            <TD>
              <para>Invalid descriptor index</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>ColumnNumber</legacyItalic> exceeded the maximum number of columns in the result set.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY000</para>
            </TD>
            <TD>
              <para>General error</para>
            </TD>
            <TD>
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>*MessageText</legacyItalic> buffer describes the error and its cause.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY001</para>
            </TD>
            <TD>
              <para>Memory allocation error</para>
            </TD>
            <TD>
              <para>The driver was unable to allocate memory that is required to support execution or completion of the function.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY003</para>
            </TD>
            <TD>
              <para>Invalid application buffer type</para>
            </TD>
            <TD>
              <para>The argument <legacyItalic>TargetType</legacyItalic> was neither a valid data type nor SQL_C_DEFAULT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence error</para>
            </TD>
            <TD>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when <unmanagedCodeEntityReference>SQLBindCol</unmanagedCodeEntityReference> was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) An asynchronously executing function was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY013</para>
            </TD>
            <TD>
              <para>Memory management error</para>
            </TD>
            <TD>
              <para>The function call could not be processed because the underlying memory objects could not be accessed, possibly because of low memory conditions.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY090</para>
            </TD>
            <TD>
              <para>Invalid string or buffer length</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the argument <legacyItalic>BufferLength</legacyItalic> was less than 0.</para>
              <para>(DM) The driver was an ODBC 2.<legacyItalic>x</legacyItalic> driver, the <legacyItalic>ColumnNumber</legacyItalic> argument was set to 0, and the value specified for the argument <legacyItalic>BufferLength</legacyItalic> was not equal to 4.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY117</para>
            </TD>
            <TD>
              <para>Connection is suspended due to unknown transaction state. Only disconnect and read-only functions are allowed.</para>
            </TD>
            <TD>
              <para>(DM) For more information about suspended state, see <link xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HYC00</para>
            </TD>
            <TD>
              <para>Optional feature not implemented</para>
            </TD>
            <TD>
              <para>The driver or data source does not support the conversion specified by the combination of the <legacyItalic>TargetType</legacyItalic> argument and the driver-specific SQL data type of the corresponding column.</para>
              <para>The argument <legacyItalic>ColumnNumber</legacyItalic> was 0 and the driver does not support bookmarks.</para>
              <para>The driver supports only ODBC 2.<legacyItalic>x</legacyItalic> and the argument <legacyItalic>TargetType</legacyItalic> was one of the following:</para>
              <para>SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT</para>
              <para>and any of the interval C data types listed in <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink> in Appendix D: Data Types. </para>
              <para>The driver only supports ODBC versions prior to 3.50, and the argument <legacyItalic>TargetType</legacyItalic> was SQL_C_GUID.</para>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HYT01</para>
            </TD>
            <TD>
              <para>Connection timeout expired</para>
            </TD>
            <TD>
              <para>The connection timeout period expired before the data source responded to the request. The connection timeout period is set through <legacyBold>SQLSetConnectAttr</legacyBold>, SQL_ATTR_CONNECTION_TIMEOUT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM001</para>
            </TD>
            <TD>
              <para>Driver does not support this function</para>
            </TD>
            <TD>
              <para>(DM) The driver associated with the <legacyItalic>StatementHandle</legacyItalic> does not support the function.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLBindCol</legacyBold> is used to associate, or <legacyItalic>bind,</legacyItalic> columns in the result set to data buffers and length/indicator buffers in the application. When the application calls <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> to fetch data, the driver returns the data for the bound columns in the specified buffers; for more information, see <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</legacyLink>. When the application calls <legacyBold>SQLBulkOperations</legacyBold> to update or insert a row or <legacyBold>SQLSetPos</legacyBold> to update a row, the driver retrieves the data for the bound columns from the specified buffers; for more information, see <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations Function</legacyLink> or <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</legacyLink>. For more information about binding, see <legacyLink xlink:href="052870e3-3f3f-4f07-91da-b649348225f4">Retrieving Results (Basic)</legacyLink>.</para>
      <para>Notice that columns do not have to be bound to retrieve data from them. An application can also call <legacyBold>SQLGetData</legacyBold> to retrieve data from columns. Although it is possible to bind some columns in a row and call <legacyBold>SQLGetData</legacyBold> for others, this is subject to some restrictions. For more information, see <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Binding, Unbinding, and Rebinding Columns</title>
    <content>
      <para>A column can be bound, unbound, or rebound at any time, even after data has been fetched from the result set. The new binding takes effect the next time that a function that uses bindings is called. For example, suppose an application binds the columns in a result set and calls <legacyBold>SQLFetch</legacyBold>. The driver returns the data in the bound buffers. Now suppose the application binds the columns to a different set of buffers. The driver does not put the data for the just-fetched row in the newly bound buffers. Instead, it waits until <legacyBold>SQLFetch</legacyBold> is called again and then places the data for the next row in the newly bound buffers.</para>
      <alert class="note">
        <para>The statement attribute SQL_ATTR_USE_BOOKMARKS should always be set before binding a column to column 0. This is not required but is strongly recommended.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Binding Columns</title>
    <content>
      <para>To bind a column, an application calls <legacyBold>SQLBindCol</legacyBold> and passes the column number, type, address, and length of a data buffer, and the address of a length/indicator buffer. For information about how these addresses are used, see "Buffer Addresses," later in this section. For more information about binding columns, see <legacyLink xlink:href="17277ab3-33ad-44d3-a81c-a26b5e338512">Using SQLBindCol</legacyLink>.</para>
      <para>The use of these buffers is deferred; that is, the application binds them in <legacyBold>SQLBindCol</legacyBold> but the driver accesses them from other functions — namely <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLSetPos</legacyBold>. It is the application's responsibility to make sure that the pointers specified in <legacyBold>SQLBindCol</legacyBold> remain valid as long as the binding remains in effect. If the application allows these pointers to become invalid — for example, it frees a buffer — and then calls a function that expects them to be valid, the consequences are undefined. For more information, see <legacyLink xlink:href="02c9a75c-2103-4f68-a1db-e31f7e0f1f03">Deferred Buffers</legacyLink>.</para>
      <para>The binding remains in effect until it is replaced by a new binding, the column is unbound, or the statement is freed.</para>
    </content>
  </section>
  <section>
    <title>Unbinding Columns</title>
    <content>
      <para>To unbind a single column, an application calls <legacyBold>SQLBindCol</legacyBold> with <legacyItalic>ColumnNumber</legacyItalic> set to the number of that column and <legacyItalic>TargetValuePtr</legacyItalic> set to a null pointer. If <legacyItalic>ColumnNumber</legacyItalic> refers to an unbound column, <legacyBold>SQLBindCol</legacyBold> still returns SQL_SUCCESS.</para>
      <para>To unbind all columns, an application calls <legacyBold>SQLFreeStmt</legacyBold> with <legacyItalic>fOption</legacyItalic> set to SQL_UNBIND. This can also be accomplished by setting the SQL_DESC_COUNT field of the ARD to zero.</para>
    </content>
  </section>
  <section>
    <title>Rebinding Columns</title>
    <content>
      <para>An application can perform either of two operations to change a binding:  </para>
      <list class="bullet">
        <listItem>
          <para>Call <legacyBold>SQLBindCol</legacyBold> to specify a new binding for a column that is already bound. The driver overwrites the old binding with the new one.</para>
        </listItem>
        <listItem>
          <para>Specify an offset to be added to the buffer address that was specified by the binding call to <legacyBold>SQLBindCol</legacyBold>. For more information, see the next section, "Binding Offsets."</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Binding Offsets</title>
    <content>
      <para>A binding offset is a value that is added to the addresses of the data and length/indicator buffers (as specified in the <legacyItalic>TargetValuePtr</legacyItalic> and <legacyItalic>StrLen_or_IndPtr </legacyItalic>argument) before they are dereferenced. When offsets are used, the bindings are a "template" of how the application's buffers are laid out, and the application can move this "template" to different areas of memory by changing the offset. Because the same offset is added to each address in each binding, the relative offsets between buffers for different columns must be the same within each set of buffers. This is always true when row-wise binding is used; the application must carefully lay out its buffers for this to be true when column-wise binding is used.</para>
      <para>Using a binding offset has basically the same effect as rebinding a column by calling <legacyBold>SQLBindCol</legacyBold>. The difference is that a new call to <legacyBold>SQLBindCol</legacyBold> specifies new addresses for the data buffer and length/indicator buffer, whereas use of a binding offset does not change the addresses but just adds an offset to them. The application can specify a new offset whenever it wants, and this offset is always added to the originally bound addresses. In particular, if the offset is set to 0 or if the statement attribute is set to a null pointer, the driver uses the originally bound addresses.</para>
      <para>To specify a binding offset, the application sets the SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute to the address of an SQLINTEGER buffer. Before the application calls a function that uses bindings, it puts an offset in bytes in this buffer. To determine the address of the buffer to use, the driver adds the offset to the address in the binding. The sum of the address and the offset must be a valid address, but the address to which the offset is added does not have to be valid. For more information about how binding offsets are used, see "Buffer Addresses," later in this section.</para>
    </content>
  </section>
  <section>
    <title>Binding Arrays</title>
    <content>
      <para>If the rowset size (the value of the SQL_ATTR_ROW_ARRAY_SIZE statement attribute) is greater than 1, the application binds arrays of buffers instead of single buffers. For more information, see <legacyLink xlink:href="1a92b5d8-7c6e-4ce5-8c99-600a387026aa">Block Cursors</legacyLink>.</para>
      <para>The application can bind arrays in two ways:  </para>
      <list class="bullet">
        <listItem>
          <para>Bind an array to each column. This is referred to as <legacyItalic>column-wise binding</legacyItalic> because each data structure (array) contains data for a single column.</para>
        </listItem>
        <listItem>
          <para>Define a structure to hold the data for a whole row and bind an array of these structures. This is referred to as <legacyItalic>row-wise binding</legacyItalic> because each data structure contains the data for a single row.</para>
        </listItem>
      </list>
      <para>Each array of buffers must have at least as many elements as the size of the rowset.</para>
      <alert class="note">
        <para>An application must verify that alignment is valid. For more information about alignment considerations, see <legacyLink xlink:href="06a01e51-e7a5-495f-aa27-e304b0d005ff">Alignment</legacyLink>.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Column-Wise Binding</title>
    <content>
      <para>In column-wise binding, the application binds separate data and length/indicator arrays to each column.</para>
      <para>To use column-wise binding, the application first sets the SQL_ATTR_ROW_BIND_TYPE statement attribute to SQL_BIND_BY_COLUMN. (This is the default.) For each column to be bound, the application performs the following steps:</para>
      <list class="ordered">
        <listItem>
          <para>Allocates a data buffer array.</para>
        </listItem>
        <listItem>
          <para>Allocates an array of length/indicator buffers. </para>
          <alert class="note">
            <para>If the application writes directly to descriptors when column-wise binding is used, separate arrays can be used for length and indicator data.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBindCol</legacyBold> with the following arguments: </para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyItalic>TargetType</legacyItalic> is the type of a single element in the data buffer array.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>TargetValuePtr</legacyItalic> is the address of the data buffer array.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>BufferLength</legacyItalic> is the size of a single element in the data buffer array. The <legacyItalic>BufferLength</legacyItalic> argument is ignored when the data is fixed-length data.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>StrLen_or_IndPtr</legacyItalic> is the address of the length/indicator array.</para>
            </listItem>
          </list>
        </listItem>
      </list>
      <para>For more information about how this information is used, see "Buffer Addresses," later in this section. For more information about column-wise binding, see <legacyLink xlink:href="86d37637-3a25-455d-9c82-a0d7bff8d70d">Column-Wise Binding</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Row-Wise Binding</title>
    <content>
      <para>In row-wise binding, the application defines a structure that contains data and length/indicator buffers for each column to be bound.</para>
      <para>To use row-wise binding, the application performs the following steps:  </para>
      <list class="ordered">
        <listItem>
          <para>Defines a structure to hold a single row of data (including both data and length/indicator buffers) and allocates an array of these structures. </para>
          <alert class="note">
            <para>If the application writes directly to descriptors when row-wise binding is used, separate fields can be used for length and indicator data.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Sets the SQL_ATTR_ROW_BIND_TYPE statement attribute to the size of the structure that contains a single row of data or to the size of an instance of a buffer into which the results columns will be bound. The length must include space for all the bound columns, and any padding of the structure or buffer, to make sure that when the address of a bound column is incremented with the specified length, the result will point to the beginning of the same column in the next row. When using the <legacyItalic>sizeof</legacyItalic> operator in ANSI C, this behavior is guaranteed.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBindCol</legacyBold> with the following arguments for each column to be bound: </para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyItalic>TargetType</legacyItalic> is the type of the data buffer member to be bound to the column.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>TargetValuePtr</legacyItalic> is the address of the data buffer member in the first array element.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>BufferLength</legacyItalic> is the size of the data buffer member.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>StrLen_or_IndPtr</legacyItalic> is the address of the length/indicator member to be bound.</para>
            </listItem>
          </list>
        </listItem>
      </list>
      <para>For more information about how this information is used, see "Buffer Addresses," later in this section. For more information about column-wise binding, see <legacyLink xlink:href="4f622cf4-0603-47a1-a48b-944c4ef46364">Row-Wise Binding</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Buffer Addresses</title>
    <content>
      <para>The <legacyItalic>buffer address</legacyItalic> is the actual address of the data or length/indicator buffer. The driver calculates the buffer address just before it writes to the buffers (such as during fetch time). It is calculated from the following formula, which uses the addresses specified in the <legacyItalic>TargetValuePtr</legacyItalic> and <legacyItalic>StrLen_or_IndPtr</legacyItalic> arguments, the binding offset, and the row number:</para>
      <para>
        <legacyItalic>Bound Address</legacyItalic> + <legacyItalic>Binding Offset</legacyItalic> + ((<legacyItalic>Row Number</legacyItalic> – 1) x <legacyItalic>Element Size</legacyItalic>)</para>
      <para>where the formula's variables are defined as described in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>Bound Address</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>For data buffers, the address specified with the <legacyItalic>TargetValuePtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold>.</para>
              <para>For length/indicator buffers, the address specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold>. For more information, see "Additional Comments" in the "Descriptors and SQLBindCol" section.</para>
              <para>If the bound address is 0, no data value is returned, even if the address as calculated by the previous formula is nonzero.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Binding Offset</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>If row-wise binding is used, the value stored at the address specified with the SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute.</para>
              <para>If column-wise binding is used or if the value of the SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute is a null pointer, <legacyItalic>Binding Offset</legacyItalic> is 0.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Row Number</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The 1-based number of the row in the rowset. For single-row fetches, which are the default, this is 1.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Element Size</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The size of an element in the bound array.</para>
              <para>If column-wise binding is used, this is <legacyBold>sizeof(SQLINTEGER)</legacyBold> for length/indicator buffers. For data buffers, it is the value of the <legacyItalic>BufferLength</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold> if the data type is variable length, and the size of the data type if the data type is fixed length.</para>
              <para>If row-wise binding is used, this is the value of the SQL_ATTR_ROW_BIND_TYPE statement attribute for both data and length/indicator buffers.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Descriptors and SQLBindCol</title>
    <content>
      <para>The following sections describe how <legacyBold>SQLBindCol</legacyBold> interacts with descriptors.</para>
      <alert class="caution">
        <para>Calling <legacyBold>SQLBindCol</legacyBold> for one statement can affect other statements. This occurs when the ARD associated with the statement is explicitly allocated and is also associated with other statements. Because <legacyBold>SQLBindCol</legacyBold> modifies the descriptor, the modifications apply to all statements with which this descriptor is associated. If this is not the required behavior, the application should dissociate this descriptor from the other statements before it calls <legacyBold>SQLBindCol</legacyBold>.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Argument Mappings</title>
    <content>
      <para>Conceptually, <legacyBold>SQLBindCol</legacyBold> performs the following steps in sequence:  </para>
      <list class="ordered">
        <listItem>
          <para>Calls <legacyBold>SQLGetStmtAttr</legacyBold> to obtain the ARD handle.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLGetDescField</legacyBold> to get this descriptor's SQL_DESC_COUNT field, and if the value in the <legacyItalic>ColumnNumber</legacyItalic> argument exceeds the value of SQL_DESC_COUNT, calls <legacyBold>SQLSetDescField</legacyBold> to increase the value of SQL_DESC_COUNT to <legacyItalic>ColumnNumber</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLSetDescField</legacyBold> multiple times to assign values to the following fields of the ARD: </para>
          <list class="bullet">
            <listItem>
              <para>Sets SQL_DESC_TYPE and SQL_DESC_CONCISE_TYPE to the value of <legacyItalic>TargetType</legacyItalic>, except that if <legacyItalic>TargetType</legacyItalic> is one of the concise identifiers of a datetime or interval subtype, it sets SQL_DESC_TYPE to SQL_DATETIME or SQL_INTERVAL, respectively; sets SQL_DESC_CONCISE_TYPE to the concise identifier; and sets SQL_DESC_DATETIME_INTERVAL_CODE to the corresponding datetime or interval subcode.</para>
            </listItem>
            <listItem>
              <para>Sets one or more of SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE, and SQL_DESC_DATETIME_INTERVAL_PRECISION, as appropriate for <legacyItalic>TargetType</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>Sets the SQL_DESC_OCTET_LENGTH field to the value of <legacyItalic>BufferLength</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>Sets the SQL_DESC_DATA_PTR field to the value of <legacyItalic>TargetValue</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>Sets the SQL_DESC_INDICATOR_PTR field to the value of <legacyItalic>StrLen_or_Ind</legacyItalic>. (See the following paragraph.)</para>
            </listItem>
            <listItem>
              <para>Sets the SQL_DESC_OCTET_LENGTH_PTR field to the value of <legacyItalic>StrLen_or_Ind</legacyItalic>. (See the following paragraph.)</para>
            </listItem>
          </list>
        </listItem>
      </list>
      <para>The variable that the <legacyItalic>StrLen_or_Ind</legacyItalic> argument refers to is used for both indicator and length information. If a fetch encounters a null value for the column, it stores SQL_NULL_DATA in this variable; otherwise, it stores the data length in this variable. Passing a null pointer as <legacyItalic>StrLen_or_Ind</legacyItalic> keeps the fetch operation from returning the data length but makes the fetch fail if it encounters a null value and has no way to return SQL_NULL_DATA.</para>
      <para>If the call to <legacyBold>SQLBindCol</legacyBold> fails, the content of the descriptor fields that it would have set in the ARD are undefined and the value of the SQL_DESC_COUNT field of the ARD is unchanged.</para>
    </content>
  </section>
  <section>
    <title>Implicit Resetting of COUNT Field</title>
    <content>
      <para>
        <legacyBold>SQLBindCol</legacyBold> sets SQL_DESC_COUNT to the value of the <legacyItalic>ColumnNumber</legacyItalic> argument only when this would increase the value of SQL_DESC_COUNT. If the value in the <legacyItalic>TargetValuePtr</legacyItalic> argument is a null pointer and the value in the <legacyItalic>ColumnNumber</legacyItalic> argument is equal to SQL_DESC_COUNT (that is, when unbinding the highest bound column), then SQL_DESC_COUNT is set to the number of the highest remaining bound column.</para>
    </content>
  </section>
  <section>
    <title>Cautions Regarding SQL_DEFAULT</title>
    <content>
      <para>To retrieve column data successfully, the application must determine correctly the length and starting point of the data in the application buffer. When the application specifies an explicit <legacyItalic>TargetType</legacyItalic>, application misconceptions are easily detected. However, when the application specifies a <legacyItalic>TargetType</legacyItalic> of SQL_DEFAULT, <legacyBold>SQLBindCol</legacyBold> can be applied to a column of a different data type from the one intended by the application, either from changes to the metadata or by applying the code to a different column. In this case, the application may not always determine the start or length of the fetched column data. This may lead to unreported data errors or memory violations.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>In the following example, an application executes a <legacyBold>SELECT</legacyBold> statement on the Customers table to return a result set of the customer IDs, names, and phone numbers, sorted by name. It then calls <legacyBold>SQLBindCol</legacyBold> to bind the columns of data to local buffers. Finally, the application fetches each row of data with <legacyBold>SQLFetch</legacyBold> and prints each customer's name, ID, and phone number.</para>
      <para>For more code examples, see <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations Function</legacyLink>, <legacyLink xlink:href="4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0">SQLColumns Function</legacyLink>, <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll Function</legacyLink>, and <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</legacyLink>.</para>
      <code>// SQLBindCol_ref.cpp
// compile with: odbc32.lib
#include &lt;windows.h&gt;
#include &lt;stdio.h&gt;

#define UNICODE
#include &lt;sqlext.h&gt;

#define NAME_LEN 50
#define PHONE_LEN 20

void show_error() {
   printf("error\n");
}

int main() {
   SQLHENV henv;
   SQLHDBC hdbc;
   SQLHSTMT hstmt = 0;
   SQLRETURN retcode;
   SQLWCHAR szName[NAME_LEN], szPhone[PHONE_LEN], sCustID[NAME_LEN];
   SQLLEN cbName = 0, cbCustID = 0, cbPhone = 0;

   // Allocate environment handle
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);

   // Set the ODBC version environment attribute
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0); 

      // Allocate connection handle
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc);

         // Set login timeout to 5 seconds
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);

            // Connect to data source
            retcode = SQLConnect(hdbc, (SQLWCHAR*) L"NorthWind", SQL_NTS, (SQLWCHAR*) NULL, 0, NULL, 0);

            // Allocate statement handle
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) { 
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt); 

               retcode = SQLExecDirect(hstmt, (SQLWCHAR *) L"SELECT CustomerID, ContactName, Phone FROM CUSTOMERS ORDER BY 2, 1, 3", SQL_NTS);
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {

                  // Bind columns 1, 2, and 3
                  retcode = SQLBindCol(hstmt, 1, SQL_C_CHAR, &amp;sCustID, 100, &amp;cbCustID);
                  retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &amp;cbName);
                  retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN, &amp;cbPhone); 

                  // Fetch and print each row of data. On an error, display a message and exit.
                  for (i ; ; i++) {
                     retcode = SQLFetch(hstmt);
                     if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)
                        show_error();
                     if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)
                        wprintf(L"%d: %S %S %S\n", i + 1, sCustID, szName, szPhone);
                     else
                        break;
                  }
               }

               // Process data
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
                  SQLCancel(hstmt);
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);
               }

               SQLDisconnect(hdbc);
            }

            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);
         }
      }
      SQLFreeHandle(SQL_HANDLE_ENV, henv);
   }
}</code>
      <para>Also see, <link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link>.</para>
    </content>
  </section>
  <section>
    <title>Related Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>For information about</para>
            </TD>
            <TD>
              <para>See</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Returning information about a column in a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="eddef353-83f3-4a3c-8f24-f9ed888890a4">SQLDescribeCol Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching a block of data or scrolling through a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching multiple rows of data</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Releasing column buffers on the statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching part or all of a column of data</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the number of result set columns</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="d863179f-12a9-4b55-ac6b-7d84202d3da3">SQLNumResultCols Function</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>