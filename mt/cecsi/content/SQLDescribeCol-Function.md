---
title: SQLDescribeCol Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLDescribeCol
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: eddef353-83f3-4a3c-8f24-f9ed888890a4
translation.priority.ht: 
  - en-gb
---
# SQLDescribeCol Function
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
          <legacyBold>SQLDescribeCol</legacyBold> returns the result descriptor — column name,type, column size, decimal digits, and nullability — for one column in the result set. This information also is available in the fields of the IRD.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLDescribeCol</legacyBold>(
      SQLHSTMT       <parameterReference>StatementHandle</parameterReference>,
      SQLUSMALLINT   <parameterReference>ColumnNumber</parameterReference>,
      SQLCHAR *      <parameterReference>ColumnName</parameterReference>,
      SQLSMALLINT    <parameterReference>BufferLength</parameterReference>,
      SQLSMALLINT *  <parameterReference>NameLengthPtr</parameterReference>,
      SQLSMALLINT *  <parameterReference>DataTypePtr</parameterReference>,
      SQLULEN *      <parameterReference>ColumnSizePtr</parameterReference>,
      SQLSMALLINT *  <parameterReference>DecimalDigitsPtr</parameterReference>,
      SQLSMALLINT *  <parameterReference>NullablePtr</parameterReference>);</legacySyntax>
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
          <para>[Input] Column number of result data, ordered sequentially in increasing column order, starting at 1. The <legacyItalic>ColumnNumber</legacyItalic> argument can also be set to 0 to describe the bookmark column.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ColumnName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a null-terminated buffer in which to return the column name. This value is read from the SQL_DESC_NAME field of the IRD. If the column is unnamed or the column name cannot be determined, the driver returns an empty string.</para>
          <para>If <legacyItalic>ColumnName</legacyItalic> is NULL, <legacyItalic>NameLengthPtr</legacyItalic> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>ColumnName</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>ColumnName</legacyItalic> buffer, in characters. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of characters (excluding the null termination) available to return in *<legacyItalic>ColumnName</legacyItalic>. If the number of characters available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the column name in *<legacyItalic>ColumnName</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DataTypePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the SQL data type of the column. This value is read from the SQL_DESC_CONCISE_TYPE field of the IRD. This will be one of the values in <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink>, or a driver-specific SQL data type. If the data type cannot be determined, the driver returns SQL_UNKNOWN_TYPE.</para>
          <para>In ODBC 3.<legacyItalic>x</legacyItalic>, SQL_TYPE_DATE, SQL_TYPE_TIME, or SQL_TYPE_TIMESTAMP is returned in <legacyItalic>*DataTypePtr</legacyItalic> for date, time, or timestamp data, respectively; in ODBC 2.<legacyItalic>x</legacyItalic>, SQL_DATE, SQL_TIME, or SQL_TIMESTAMP is returned. The Driver Manager performs the required mappings when an ODBC 2.<legacyItalic>x</legacyItalic> application is working with an ODBC 3.<legacyItalic>x</legacyItalic> driver or when an ODBC 3.<legacyItalic>x</legacyItalic> application is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver.   </para>
          <para>When <legacyItalic>ColumnNumber</legacyItalic> is equal to 0 (for a bookmark column), SQL_BINARY is returned in <legacyItalic>*DataTypePtr</legacyItalic> for variable-length bookmarks. (SQL_INTEGER is returned if bookmarks are used by an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver or by an ODBC 2.<legacyItalic>x</legacyItalic> application working with an ODBC 3.<legacyItalic>x</legacyItalic> driver.)   </para>
          <para>For more information on these data types, see <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink> in Appendix D: Data Types. For information about driver-specific SQL data types, see the driver's documentation. </para>
        </definition>
        <definedTerm>
          <legacyItalic>ColumnSizePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the size (in characters) of the column on the data source. If the column size cannot be determined, the driver returns 0. For more information on column size, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DecimalDigitsPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the number of decimal digits of the column on the data source. If the number of decimal digits cannot be determined or is not applicable, the driver returns 0. For more information on decimal digits, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NullablePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return a value that indicates whether the column allows NULL values. This value is read from the SQL_DESC_NULLABLE field of the IRD. The value is one of the following:</para>
          <para>SQL_NO_NULLS: The column does not allow NULL values.   </para>
          <para>SQL_NULLABLE: The column allows NULL values.   </para>
          <para>SQL_NULLABLE_UNKNOWN: The driver cannot determine if the column allows NULL values. </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLDescribeCol</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLDescribeCol</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>01004</para>
            </TD>
            <TD>
              <para>String data, right truncated</para>
            </TD>
            <TD>
              <para>The buffer *<legacyItalic>ColumnName</legacyItalic> was not large enough to return the entire column name, so the column name was truncated. The length of the untruncated column name is returned in *<legacyItalic>NameLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07005</para>
            </TD>
            <TD>
              <para>Prepared statement not a <legacyItalic>cursor-specification</legacyItalic></para>
            </TD>
            <TD>
              <para>The statement associated with the <legacyItalic>StatementHandle</legacyItalic> did not return a result set. There were no columns to describe.</para>
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
              <para>(DM) The value specified for the argument <legacyItalic>ColumnNumber</legacyItalic> was equal to 0, and the SQL_ATTR_USE_BOOKMARKS statement option was SQL_UB_OFF.</para>
              <para>The value specified for the argument <legacyItalic>ColumnNumber</legacyItalic> was greater than the number of columns in the result set.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>08S01</para>
            </TD>
            <TD>
              <para>Communication link failure</para>
            </TD>
            <TD>
              <para>The communication link between the driver and the data source to which the driver was connected failed before the function completed processing.</para>
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
              <para>Memory allocation failure</para>
            </TD>
            <TD>
              <para>The driver was unable to allocate memory required to support execution or completion of the function.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY008</para>
            </TD>
            <TD>
              <para>Operation canceled</para>
            </TD>
            <TD>
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>. Then the function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic> from a different thread in a multithread application.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when <unmanagedCodeEntityReference>SQLDescribeCol</unmanagedCodeEntityReference> was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) The function was called prior to calling <legacyBold>SQLPrepare</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or a catalog function on the statement handle.</para>
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
              <para>Invalid string or buffer length </para>
            </TD>
            <TD>
              <para>(DM) The value specified for argument <legacyItalic>BufferLength</legacyItalic> was less than 0.</para>
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
          <tr>
            <TD>
              <para>IM017</para>
            </TD>
            <TD>
              <para>Polling is disabled in asynchronous notification mode</para>
            </TD>
            <TD>
              <para>Whenever the notification model is used, polling is disabled.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM018</para>
            </TD>
            <TD>
              <para>
                <languageKeyword>SQLCompleteAsync</languageKeyword> has not been called to complete the previous asynchronous operation on this handle.</para>
            </TD>
            <TD>
              <para>If the previous function call on the handle returns SQL_STILL_EXECUTING and if notification mode is enabled, <languageKeyword>SQLCompleteAsync</languageKeyword> must be called on the handle to do post-processing and complete the operation.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>
        <legacyBold>SQLDescribeCol</legacyBold> can return any SQLSTATE that can be returned by <legacyBold>SQLPrepare</legacyBold> or <legacyBold>SQLExecute</legacyBold> when called after <legacyBold>SQLPrepare</legacyBold> and before <legacyBold>SQLExecute</legacyBold>, depending on when the data source evaluates the SQL statement associated with the statement handle.</para>
      <para>For performance reasons, an application should not call <legacyBold>SQLDescribeCol</legacyBold> before executing a statement.</para>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>An application typically calls <legacyBold>SQLDescribeCol</legacyBold> after a call to <legacyBold>SQLPrepare</legacyBold> and before or after the associated call to <legacyBold>SQLExecute</legacyBold>. An application can also call <legacyBold>SQLDescribeCol</legacyBold> after a call to <legacyBold>SQLExecDirect</legacyBold>. For more information, see <legacyLink xlink:href="6d134515-e34d-4563-96d7-8ad7714818fd">Result Set Metadata</legacyLink>.</para>
      <para>
        <legacyBold>SQLDescribeCol</legacyBold> retrieves the column name, type, and length generated by a <legacyBold>SELECT</legacyBold> statement. If the column is an expression, *<legacyItalic>ColumnName</legacyItalic> is either an empty string or a driver-defined name.</para>
      <alert class="note">
        <para>ODBC supports SQL_NULLABLE_UNKNOWN as an extension, even though the Open Group and SQL Access Group Call Level Interface specification does not specify the option for <legacyBold>SQLDescribeCol</legacyBold>. </para>
      </alert>
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
              <para>Binding a buffer to a column in a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Canceling statement processing</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning information about a column in a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="8c45c598-cb01-4789-a571-e93619a18ed9">SQLColAttribute</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching multiple rows of data</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the number of result set columns</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="d863179f-12a9-4b55-ac6b-7d84202d3da3">SQLNumResultCols</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preparing a statement for execution</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare</legacyLink>
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