---
title: SQLColAttribute Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLColAttribute
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 8c45c598-cb01-4789-a571-e93619a18ed9
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLColAttribute Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.0 Standards Compliance: ISO 92</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLColAttribute</legacyBold> returns descriptor information for a column in a result set. Descriptor information is returned as a character string, a descriptor-dependent value, or an integer value.</para>
        <alert class="note">
          <para>For more information about what the Driver Manager maps this function to when an ODBC 3.<legacyItalic>x</legacyItalic> application is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, see <legacyLink xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</legacyLink>.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLColAttribute</legacyBold> (
      SQLHSTMT        <parameterReference>StatementHandle</parameterReference>,
      SQLUSMALLINT    <parameterReference>ColumnNumber</parameterReference>,
      SQLUSMALLINT    <parameterReference>FieldIdentifier</parameterReference>,
      SQLPOINTER      <parameterReference>CharacterAttributePtr</parameterReference>,
      SQLSMALLINT     <parameterReference>BufferLength</parameterReference>,
      SQLSMALLINT *   <parameterReference>StringLengthPtr</parameterReference>,
      SQLLEN *        <parameterReference>NumericAttributePtr</parameterReference>);</legacySyntax>
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
          <para>[Input] The number of the record in the IRD from which the field value is to be retrieved. This argument corresponds to the column number of result data, ordered sequentially in increasing column order, starting at 1. Columns can be described in any order.</para>
          <para>Column 0 can be specified in this argument, but all values except SQL_DESC_TYPE and SQL_DESC_OCTET_LENGTH will return undefined values.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FieldIdentifier</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The descriptor handle. This handle defines which field in the IRD should be queried (for example, SQL_COLUMN_TABLE_NAME).</para>
        </definition>
        <definedTerm>
          <legacyItalic>CharacterAttributePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the value in the <legacyItalic>FieldIdentifier</legacyItalic> field of the <legacyItalic>ColumnNumber</legacyItalic> row of the IRD, if the field is a character string. Otherwise, the field is unused.</para>
          <para>If <legacyItalic>CharacterAttributePtr</legacyItalic> is NULL, <legacyItalic>StringLengthPtr</legacyItalic> will still return the total number of bytes (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>CharacterAttributePtr</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>FieldIdentifier</legacyItalic> is an ODBC-defined field and <legacyItalic>CharacterAttributePtr</legacyItalic> points to a character string or binary buffer, this argument should be the length of *<legacyItalic>CharacterAttributePtr</legacyItalic>. If <legacyItalic>FieldIdentifier</legacyItalic> is an ODBC-defined field and *<legacyItalic>CharacterAttribute</legacyItalic>Ptr is an integer, this field is ignored. If the <legacyItalic>*CharacterAttributePtr</legacyItalic> is a Unicode string (when calling <legacyBold>SQLColAttributeW</legacyBold>), the <legacyItalic>BufferLength</legacyItalic> argument must be an even number. If <legacyItalic>FieldIdentifier</legacyItalic> is a driver-defined field, the application indicates the nature of the field to the Driver Manager by setting the <legacyItalic>BufferLength</legacyItalic> argument. <legacyItalic>BufferLength</legacyItalic> can have the following values:</para>
          <list class="bullet">
            <listItem>
              <para>If <legacyItalic>CharacterAttributePtr</legacyItalic> is a pointer to a pointer, <legacyItalic>BufferLength</legacyItalic> should have the value SQL_IS_POINTER. </para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>CharacterAttributePtr</legacyItalic> is a pointer to a character string, the <legacyItalic>BufferLength</legacyItalic> is the length of the buffer.</para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>CharacterAttributePtr</legacyItalic> is a pointer to a binary buffer, the application places the result of the SQL_LEN_BINARY_ATTR(<legacyItalic>length</legacyItalic>) macro in <legacyItalic>BufferLength</legacyItalic>. This places a negative value in <legacyItalic>BufferLength</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>CharacterAttributePtr</legacyItalic> is a pointer to a fixed-length data type, <legacyItalic>BufferLength</legacyItalic> must be one of the following: SQL_IS_INTEGER, SQL_IS_UNINTEGER, SQL_SMALLINT, or SQLUSMALLINT.</para>
            </listItem>
          </list>
        </definition>
        <definedTerm>
          <legacyItalic>StringLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of bytes (excluding the null-termination byte for character data) available to return in *<legacyItalic>CharacterAttributePtr</legacyItalic>.</para>
          <para>For character data, if the number of bytes available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the descriptor information in *<legacyItalic>CharacterAttributePtr</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character and is null-terminated by the driver.</para>
          <para>For all other types of data, the value of <legacyItalic>BufferLength</legacyItalic> is ignored and the driver assumes the size of *<legacyItalic>CharacterAttributePtr</legacyItalic> is 32 bits.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NumericAttributePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to an integer buffer in which to return the value in the <legacyItalic>FieldIdentifier</legacyItalic> field of the <legacyItalic>ColumnNumber</legacyItalic> row of the IRD, if the field is a numeric descriptor type, such as SQL_DESC_COLUMN_LENGTH. Otherwise, the field is unused. Please note that some drivers may only write the lower 32-bit or 16-bit of a buffer and leave the higher-order bit unchanged. Therefore, applications should initialize the value to 0 before calling this function.</para>
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
      <para>When <legacyBold>SQLColAttribute</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value may be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLColAttribute </legacyBold>and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The buffer *<legacyItalic>CharacterAttributePtr</legacyItalic> was not large enough to return the entire string value, so the string value was truncated. The length of the untruncated string value is returned in *<legacyItalic>StringLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>The statement associated with the <legacyItalic>StatementHandle</legacyItalic> did not return a result set and <legacyItalic>FieldIdentifier</legacyItalic> was not SQL_DESC_COUNT. There were no columns to describe.</para>
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
              <para>(DM) The value specified for <legacyItalic>ColumnNumber</legacyItalic> was equal to 0, and the SQL_ATTR_USE_BOOKMARKS statement attribute was SQL_UB_OFF.</para>
              <para>The value specified for the argument <legacyItalic>ColumnNumber</legacyItalic> was greater than the number of columns in the result set.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagField</legacyBold> from the diagnostic data structure describes the error and its cause.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This aynchronous function was still executing when SQLColAttribute was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) The function was called prior to calling <legacyBold>SQLPrepare</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or a catalog function for the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
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
              <para>(DM) <legacyItalic>*CharacterAttributePtr</legacyItalic> is a character string, and <legacyItalic>BufferLength</legacyItalic> was less than 0 but not equal to SQL_NTS.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY091</para>
            </TD>
            <TD>
              <para>Invalid descriptor field identifier</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>FieldIdentifier</legacyItalic> was not one of the defined values and was not an implementation-defined value.</para>
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
              <para>Driver not capable</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>FieldIdentifier</legacyItalic> was not supported by the driver.</para>
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
      <para>When called after <legacyBold>SQLPrepare</legacyBold> and before <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLColAttribute</legacyBold> can return any SQLSTATE that can be returned by <legacyBold>SQLPrepare</legacyBold> or <legacyBold>SQLExecute</legacyBold>, depending on when the data source evaluates the SQL statement associated with the <legacyItalic>StatementHandle</legacyItalic>.</para>
      <para>For performance reasons, an application should not call <legacyBold>SQLColAttribute</legacyBold> before executing a statement.</para>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>For information about how applications use the information returned by <legacyBold>SQLColAttribute</legacyBold>, see <legacyLink xlink:href="6d134515-e34d-4563-96d7-8ad7714818fd">Result Set Metadata</legacyLink>.</para>
      <para>
        <legacyBold>SQLColAttribute</legacyBold> returns information either in *<legacyItalic>NumericAttributePtr</legacyItalic> or in *<legacyItalic>CharacterAttributePtr</legacyItalic>. Integer information is returned in *<legacyItalic>NumericAttributePtr</legacyItalic> as a SQLLEN value; all other formats of information are returned in *<legacyItalic>CharacterAttributePtr</legacyItalic>. When information is returned in *<legacyItalic>NumericAttributePtr</legacyItalic>, the driver ignores <legacyItalic>CharacterAttributePtr</legacyItalic>, <legacyItalic>BufferLength</legacyItalic>, and <legacyItalic>StringLengthPtr</legacyItalic>. When information is returned in *<legacyItalic>CharacterAttributePtr</legacyItalic>, the driver ignores <legacyItalic>NumericAttributePtr</legacyItalic>.</para>
      <para>
        <legacyBold>SQLColAttribute</legacyBold> returns values from the descriptor fields of the IRD. The function is called with a statement handle rather than a descriptor handle. The values returned by <legacyBold>SQLColAttribute</legacyBold> for the <legacyItalic>FieldIdentifier</legacyItalic> values listed later in this section can also be retrieved by calling <legacyBold>SQLGetDescField</legacyBold> with the appropriate IRD handle.</para>
      <para>The currently defined descriptor fields, the version of ODBC in which they were introduced, and the arguments in which information is returned for them are shown later in this section; more descriptor types may be defined by drivers to take advantage of different data sources.</para>
      <para>An ODBC 3.<legacyItalic>x</legacyItalic> driver must return a value for each of the descriptor fields. If a descriptor field does not apply to a driver or data source and unless otherwise stated, the driver returns 0 in *<legacyItalic>StringLengthPtr</legacyItalic> or an empty string in *<legacyItalic>CharacterAttributePtr</legacyItalic>.</para>
    </content>
  </section>
  <section>
    <title>Backward Compatibility</title>
    <content>
      <para>The ODBC 3.<legacyItalic>x</legacyItalic> function <legacyBold>SQLColAttribute</legacyBold> replaces the deprecated ODBC 2.<legacyItalic>x</legacyItalic> function <legacyBold>SQLColAttributes</legacyBold>. When mapping <legacyBold>SQLColAttributes</legacyBold> to <legacyBold>SQLColAttribute</legacyBold> (when an ODBC 2.<legacyItalic>x</legacyItalic> application is working with an ODBC 3.<legacyItalic>x</legacyItalic> driver), or mapping <legacyBold>SQLColAttribute</legacyBold> to <legacyBold>SQLColAttributes</legacyBold> (when an ODBC 3.<legacyItalic>x</legacyItalic> application is working with an ODBC 2.<legacyItalic>x </legacyItalic>driver), the Driver Manager either passes the value of <legacyItalic>FieldIdentifier</legacyItalic> through, maps it to a new value, or returns an error, as follows:</para>
      <alert class="note">
        <para>The prefix used in <legacyItalic>FieldIdentifier</legacyItalic> values in ODBC 3.<legacyItalic>x</legacyItalic> has been changed from that used in ODBC 2.<legacyItalic>x</legacyItalic>. The new prefix is "SQL_DESC"; the old prefix was "SQL_COLUMN".</para>
      </alert>
      <list class="bullet">
        <listItem>
          <para>If the <legacyBold>#define </legacyBold>value of the ODBC 2.<legacyItalic>x</legacyItalic> <legacyItalic>FieldIdentifier</legacyItalic> is the same as the <legacyBold>#define </legacyBold>value of the ODBC 3.<legacyItalic>x</legacyItalic> <legacyItalic>FieldIdentifier</legacyItalic>, the value in the function call is just passed through.</para>
        </listItem>
        <listItem>
          <para>The <legacyBold>#define</legacyBold> values of the ODBC 2.<legacyItalic>x</legacyItalic> <legacyItalic>FieldIdentifiers</legacyItalic> SQL_COLUMN_LENGTH, SQL_COLUMN_PRECISION, and SQL_COLUMN_SCALE are different from the <legacyBold>#define</legacyBold> values of the ODBC 3.<legacyItalic>x</legacyItalic> <legacyItalic>FieldIdentifiers</legacyItalic> SQL_DESC_PRECISION, SQL_DESC_SCALE, and SQL_DESC_LENGTH. An ODBC 2.<legacyItalic>x</legacyItalic> driver need only support the ODBC 2.<legacyItalic>x</legacyItalic> values. An ODBC 3.<legacyItalic>x</legacyItalic> driver must support both "SQL_COLUMN" and "SQL_DESC" values for these three <legacyItalic>FieldIdentifiers</legacyItalic>. These values are different because precision, scale, and length are defined differently in ODBC 3.<legacyItalic>x</legacyItalic> than they were in ODBC 2.<legacyItalic>x</legacyItalic>. For more information, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>If the <legacyBold>#define</legacyBold> value of the ODBC 2.<legacyItalic>x</legacyItalic> <legacyItalic>FieldIdentifier</legacyItalic> is different from the <legacyBold>#define</legacyBold> value of the ODBC 3.<legacyItalic>x</legacyItalic> <legacyItalic>FieldIdentifier</legacyItalic>, as occurs with the COUNT, NAME, and NULLABLE values, the value in the function call is mapped to the corresponding value. For example, SQL_COLUMN_COUNT is mapped to SQL_DESC_COUNT, and SQL_DESC_COUNT is mapped to SQL_COLUMN_COUNT, depending on the direction of the mapping.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>FieldIdentifier</legacyItalic> is a new value in ODBC 3.<legacyItalic>x</legacyItalic>, for which there was no corresponding value in ODBC 2.<legacyItalic>x</legacyItalic>, it will not be mapped when an ODBC 3.<legacyItalic>x</legacyItalic> application uses it in a call to <legacyBold>SQLColAttribute</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver, and the call will return SQLSTATE HY091 (Invalid descriptor field identifier).</para>
        </listItem>
      </list>
      <para>The following table lists the descriptor types returned by <legacyBold>SQLColAttribute</legacyBold>. The type for <parameterReference>NumericAttributePtr</parameterReference> values is <languageKeyword>SQLLEN *</languageKeyword>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>FieldIdentifier</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Information</para>
              <para>returned in</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_DESC_AUTO_UNIQUE_VALUE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>SQL_TRUE if the column is an autoincrementing column.</para>
              <para>SQL_FALSE if the column is not an autoincrementing column or is not numeric.</para>
              <para>This field is valid for numeric data type columns only. An application can insert values into a row containing an autoincrement column, but typically cannot update values in the column.</para>
              <para>When an insert is made into an autoincrement column, a unique value is inserted into the column at insert time. The increment is not defined, but is data source–specific. An application should not assume that an autoincrement column starts at any particular point or increments by any particular value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_BASE_COLUMN_NAME (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The base column name for the result set column. If a base column name does not exist (as in the case of columns that are expressions), then this variable contains an empty string.</para>
              <para>This information is returned from the SQL_DESC_BASE_COLUMN_NAME record field of the IRD, which is a read-only field.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_BASE_TABLE_NAME (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The name of the base table that contains the column. If the base table name cannot be defined or is not applicable, then this variable contains an empty string.</para>
              <para>This information is returned from the SQL_DESC_BASE_TABLE_NAME record field of the IRD, which is a read-only field.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_CASE_SENSITIVE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>SQL_TRUE if the column is treated as case-sensitive for collations and comparisons.</para>
              <para>SQL_FALSE if the column is not treated as case-sensitive for collations and comparisons or is noncharacter.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_CATALOG_NAME (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The catalog of the table that contains the column. The returned value is implementation-defined if the column is an expression or if the column is part of a view. If the data source does not support catalogs or the catalog name cannot be determined, an empty string is returned. This VARCHAR record field is not limited to 128 characters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_CONCISE_TYPE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The concise data type. </para>
              <para>For the datetime and interval data types, this field returns the concise data type; for example, SQL_TYPE_TIME or SQL_INTERVAL_YEAR. (For more information, see <legacyLink xlink:href="f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab">Data Type Identifiers and Descriptors</legacyLink> in Appendix D: Data Types.)</para>
              <para>This information is returned from the SQL_DESC_CONCISE_TYPE record field of the IRD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_COUNT  (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The number of columns available in the result set. This returns 0 if there are no columns in the result set. The value in the <legacyItalic>ColumnNumber</legacyItalic> argument is ignored. </para>
              <para>This information is returned from the SQL_DESC_COUNT header field of the IRD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_DISPLAY_SIZE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Maximum number of characters required to display data from the column. For more information about display size, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_FIXED_PREC_SCALE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>SQL_TRUE if the column has a fixed precision and nonzero scale that are data source–specific.</para>
              <para>SQL_FALSE if the column does not have a fixed precision and nonzero scale that are data source–specific.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LABEL (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The column label or title. For example, a column named EmpName might be labeled Employee Name or might be labeled with an alias.</para>
              <para>If a column does not have a label, the column name is returned. If the column is unlabeled and unnamed, an empty string is returned.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LENGTH  (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>A numeric value that is either the maximum or actual character length of a character string or binary data type. It is the maximum character length for a fixed-length data type, or the actual character length for a variable-length data type. Its value always excludes the null-termination byte that ends the character string. </para>
              <para>This information is returned from the SQL_DESC_LENGTH record field of the IRD.</para>
              <para>For more information about length, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LITERAL_PREFIX (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>This VARCHAR(128) record field contains the character or characters that the driver recognizes as a prefix for a literal of this data type. This field contains an empty string for a data type for which a literal prefix is not applicable. For more information, see <legacyLink xlink:href="29f468f2-f557-4a92-b31d-569c63cc6272">Literal Prefixes and Suffixes</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LITERAL_SUFFIX (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>This VARCHAR(128) record field contains the character or characters that the driver recognizes as a suffix for a literal of this data type. This field contains an empty string for a data type for which a literal suffix is not applicable. For more information, see <legacyLink xlink:href="29f468f2-f557-4a92-b31d-569c63cc6272">Literal Prefixes and Suffixes</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LOCAL_TYPE_NAME (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>This VARCHAR(128) record field contains any localized (native language) name for the data type that may be different from the regular name of the data type. If there is no localized name, then an empty string is returned. This field is for display purposes only. The character set of the string is locale-dependent and is typically the default character set of the server.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_NAME (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The column alias, if it applies. If the column alias does not apply, the column name is returned. In either case, SQL_DESC_UNNAMED is set to SQL_NAMED. If there is no column name or a column alias, an empty string is returned and SQL_DESC_UNNAMED is set to SQL_UNNAMED.</para>
              <para>This information is returned from the SQL_DESC_NAME record field of the IRD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_NULLABLE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>SQL_ NULLABLE if the column can have NULL values; SQL_NO_NULLS if the column does not have NULL values; or SQL_NULLABLE_UNKNOWN if it is not known whether the column accepts NULL values. </para>
              <para>This information is returned from the SQL_DESC_NULLABLE record field of the IRD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_NUM_PREC_RADIX (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>If the data type in the SQL_DESC_TYPE field is an approximate numeric data type, this SQLINTEGER field contains a value of 2 because the SQL_DESC_PRECISION field contains the number of bits. If the data type in the SQL_DESC_TYPE field is an exact numeric data type, this field contains a value of 10 because the SQL_DESC_PRECISION field contains the number of decimal digits. This field is set to 0 for all non-numeric data types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_OCTET_LENGTH (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The length, in bytes, of a character string or binary data type. For fixed-length character or binary types, this is the actual length in bytes. For variable-length character or binary types, this is the maximum length in bytes. This value does not include the null terminator.</para>
              <para>This information is returned from the SQL_DESC_OCTET_LENGTH record field of the IRD.</para>
              <para>For more information about length, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_PRECISION (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>A numeric value that for a numeric data type denotes the applicable precision. For data types SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP, and all the interval data types that represent a time interval, its value is the applicable precision of the fractional seconds component. </para>
              <para>This information is returned from the SQL_DESC_PRECISION record field of the IRD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_SCALE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>A numeric value that is the applicable scale for a numeric data type. For DECIMAL and NUMERIC data types, this is the defined scale. It is undefined for all other data types. </para>
              <para>This information is returned from the SCALE record field of the IRD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_SCHEMA_NAME (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The schema of the table that contains the column. The returned value is implementation-defined if the column is an expression or if the column is part of a view. If the data source does not support schemas or the schema name cannot be determined, an empty string is returned. This VARCHAR record field is not limited to 128 characters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_SEARCHABLE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>SQL_PRED_NONE if the column cannot be used in a WHERE clause. (This is the same as the SQL_UNSEARCHABLE value in ODBC 2.<legacyItalic>x</legacyItalic>.)</para>
              <para>SQL_PRED_CHAR if the column can be used in a WHERE clause but only with the LIKE predicate. (This is the same as the SQL_LIKE_ONLY value in ODBC 2.<legacyItalic>x</legacyItalic>.)</para>
              <para>SQL_PRED_BASIC if the column can be used in a WHERE clause with all the comparison operators except LIKE. (This is the same as the SQL_EXCEPT_LIKE value in ODBC 2.<legacyItalic>x</legacyItalic>.)</para>
              <para>SQL_PRED_SEARCHABLE if the column can be used in a WHERE clause with any comparison operator.</para>
              <para>Columns of type SQL_LONGVARCHAR and SQL_LONGVARBINARY usually return SQL_PRED_CHAR.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_TABLE_NAME (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The name of the table that contains the column. The returned value is implementation-defined if the column is an expression or if the column is part of a view.</para>
              <para>If the table name cannot be determined, an empty string is returned.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_TYPE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>A numeric value that specifies the SQL data type. </para>
              <para>When <legacyItalic>ColumnNumber</legacyItalic> is equal to 0, SQL_BINARY is returned for variable-length bookmarks and SQL_INTEGER is returned for fixed-length bookmarks.</para>
              <para>For the datetime and interval data types, this field returns the verbose data type: SQL_DATETIME or SQL_INTERVAL. (For more information, see <legacyLink xlink:href="f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab">Data Type Identifiers and Descriptors</legacyLink> in Appendix D: Data Types.</para>
              <para>This information is returned from the SQL_DESC_TYPE record field of the IRD.</para>
              <alert class="note">
                <para>To work against ODBC 2.<legacyItalic>x</legacyItalic> drivers, use SQL_DESC_CONCISE_TYPE instead.</para>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_TYPE_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CharacterAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Data source–dependent data type name; for example, "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY", or "CHAR ( ) FOR BIT DATA".</para>
              <para>If the type is unknown, an empty string is returned.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_UNNAMED (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>SQL_NAMED or SQL_UNNAMED. If the SQL_DESC_NAME field of the IRD contains a column alias or a column name, SQL_NAMED is returned. If there is no column name or column alias, SQL_UNNAMED is returned.</para>
              <para>This information is returned from the SQL_DESC_UNNAMED record field of the IRD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_UNSIGNED (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>SQL_TRUE if the column is unsigned (or not numeric).</para>
              <para>SQL_FALSE if the column is signed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_UPDATABLE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NumericAttributePtr</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Column is described by the values for the defined constants:</para>
              <para>SQL_ATTR_READONLY SQL_ATTR_WRITE SQL_ATTR_READWRITE_UNKNOWN</para>
              <para>SQL_DESC_UPDATABLE describes the updatability of the column in the result set, not the column in the base table. The updatability of the base column on which the result set column is based may be different from the value in this field. Whether a column is updatable can be based on the data type, user privileges, and the definition of the result set itself. If it is unclear whether a column is updatable, SQL_ATTR_READWRITE_UNKNOWN should be returned.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>
        <legacyBold>SQLColAttribute</legacyBold> is an extensible alternative to <legacyBold>SQLDescribeCol</legacyBold>. <legacyBold>SQLDescribeCol</legacyBold> returns a fixed set of descriptor information based on ANSI-89 SQL. <legacyBold>SQLColAttribute</legacyBold> allows access to the more extensive set of descriptor information available in ANSI SQL-92 and DBMS vendor extensions.</para>
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
                <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Canceling statement processing</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel Function</legacyLink>
              </para>
            </TD>
          </tr>
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
        </tbody>
      </table>
    </content>
  </section>
  <codeExample>
    <description>
      <content>
        <para>The following sample code does not free handles and connections. See <link xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle</link>, <link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link>, and <link xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt</link> for code samples to free handles and statements.</para>
      </content>
    </description>
    <code>// SQLColAttibute.cpp
// compile with: user32.lib odbc32.lib

#define UNICODE

#include &lt;windows.h&gt;
#include &lt;sqlext.h&gt;
#include &lt;strsafe.h&gt;

struct DataBinding {
   SQLSMALLINT TargetType;
   SQLPOINTER TargetValuePtr;
   SQLINTEGER BufferLength;
   SQLLEN StrLen_or_Ind;
};

void printStatementResult(SQLHSTMT hstmt) {
   int bufferSize = 1024, i;
   SQLRETURN retCode;
   SQLSMALLINT numColumn = 0, bufferLenUsed;
   SQLPOINTER* columnLabels = (SQLPOINTER *)malloc( numColumn * sizeof(SQLPOINTER*) );
   struct DataBinding* columnData = (struct DataBinding*)malloc( numColumn * sizeof(struct DataBinding) );

   retCode = SQLNumResultCols(hstmt, &amp;numColumn);

   printf( "Columns from that table:\n" );
   for ( i = 0 ; i &lt; numColumn ; i++ ) {
      columnLabels[i] = (SQLPOINTER)malloc( bufferSize*sizeof(char) );

      retCode = SQLColAttribute(hstmt, (SQLUSMALLINT)i + 1, SQL_DESC_LABEL, columnLabels[i], (SQLSMALLINT)bufferSize, &amp;bufferLenUsed, NULL);
      wprintf( L"Column %d: %s\n", i, (wchar_t*)columnLabels[i] );
   }

   // allocate memory for the binding
   for ( i = 0 ; i &lt; numColumn ; i++ ) {
      columnData[i].TargetType = SQL_C_CHAR;
      columnData[i].BufferLength = (bufferSize+1);
      columnData[i].TargetValuePtr = malloc( sizeof(unsigned char)*columnData[i].BufferLength );
   }

   // setup the binding 
   for ( i = 0 ; i &lt; numColumn ; i++ ) {
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, columnData[i].TargetType, 
         columnData[i].TargetValuePtr, columnData[i].BufferLength, &amp;(columnData[i].StrLen_or_Ind));
   }

   printf( "Data from that table:\n" );
   // fetch the data and print out the data
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt) ) {
      int j;
      for ( j = 0 ; j &lt; numColumn ; j++ )
         wprintf( L"%s: %hs\n", columnLabels[j], columnData[j].TargetValuePtr );
      printf( "\n" );
   }
   printf( "\n" ); 
}

int main() {
   int bufferSize = 1024, i, count = 1, numCols = 5;
   wchar_t firstTableName[1024], * dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize ), * userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle
   SQLWCHAR connStrbuffer[1024];
   SQLSMALLINT connStrBufferLen, bufferLen;
   SQLRETURN retCode;

   SQLHENV henv = NULL;   // Environment   
   SQLHDBC hdbc = NULL;   // Connection handle
   SQLHSTMT hstmt = NULL;   // Statement handle

   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );
   SQLWCHAR* selectAllQuery = (SQLWCHAR *)malloc( sizeof(SQLWCHAR) * bufferSize );

   // connect to database
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLCHAR *)(void*)SQL_OV_ODBC3, -1);
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc);
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);
   retCode = SQLDriverConnect(hdbc, desktopHandle, L"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &amp;connStrBufferLen, SQL_DRIVER_PROMPT);
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt);

   // display the database information
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&amp;bufferLen);
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, &amp;bufferLen);

   for ( i = 0 ; i &lt; numCols ; i++ ) {
      catalogResult[i].TargetType = SQL_C_CHAR;
      catalogResult[i].BufferLength = (bufferSize + 1);
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );
   }

   // Set up the binding. This can be used even if the statement is closed by closeStatementHandle
   for ( i = 0 ; i &lt; numCols ; i++ )
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &amp;(catalogResult[i].StrLen_or_Ind));

   retCode = SQLTables( hstmt, (SQLWCHAR*)SQL_ALL_CATALOGS, SQL_NTS, L"", SQL_NTS, L"", SQL_NTS, L"", SQL_NTS );
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);

   retCode = SQLTables( hstmt, dbName, SQL_NTS, userName, SQL_NTS, L"%", SQL_NTS, L"TABLE", SQL_NTS );
   
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt), ++count )
      if ( count == 1 )
         StringCchPrintfW( firstTableName, 1024, L"%hs", catalogResult[2].TargetValuePtr );
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);

   wprintf( L"Select all data from the first table (%s)\n", firstTableName );
   StringCchPrintfW( selectAllQuery, bufferSize, L"SELECT * FROM %s", firstTableName );

   retCode = SQLExecDirect(hstmt, selectAllQuery, SQL_NTS);
   printStatementResult(hstmt);
}</code>
  </codeExample>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
<link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link></relatedTopics>
</developerReferenceWithSyntaxDocument>