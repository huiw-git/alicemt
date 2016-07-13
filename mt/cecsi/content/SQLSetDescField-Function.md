---
title: SQLSetDescField Function
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLSetDescField
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetDescField Function
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
          <legacyBold>SQLSetDescField</legacyBold> sets the value of a single field of a descriptor record.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLSetDescField</legacyBold>(
     SQLHDESC      <parameterReference>DescriptorHandle</parameterReference>,
     SQLSMALLINT   <parameterReference>RecNumber</parameterReference>,
     SQLSMALLINT   <parameterReference>FieldIdentifier</parameterReference>,
     SQLPOINTER    <parameterReference>ValuePtr</parameterReference>,
     SQLINTEGER    <parameterReference>BufferLength</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>DescriptorHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Descriptor handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>RecNumber</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Indicates the descriptor record containing the field that the application seeks to set. Descriptor records are numbered from 0, with record number 0 being the bookmark record. The <legacyItalic>RecNumber</legacyItalic> argument is ignored for header fields.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FieldIdentifier</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Indicates the field of the descriptor whose value is to be set. For more information, see "<legacyItalic>FieldIdentifier</legacyItalic> Argument" in the "Comments" section.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to a buffer containing the descriptor information, or an integer value. The data type depends on the value of <legacyItalic>FieldIdentifier</legacyItalic>. If <legacyItalic>ValuePtr</legacyItalic> is an integer value, it may be considered as 8 bytes (SQLLEN), 4 bytes (SQLINTEGER) or 2 bytes (SQLSMALLINT), depending on the value of the <legacyItalic>FieldIdentifier</legacyItalic> argument.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>FieldIdentifier</legacyItalic> is an ODBC-defined field and <legacyItalic>ValuePtr</legacyItalic> points to a character string or a binary buffer, this argument should be the length of *<legacyItalic>ValuePtr</legacyItalic>. For character string data, this argument should contain the number of bytes in the string.</para>
          <para>If <legacyItalic>FieldIdentifier</legacyItalic> is an ODBC-defined field and <legacyItalic>ValuePtr</legacyItalic> is an integer, <legacyItalic>BufferLength</legacyItalic> is ignored.</para>
          <para>If <legacyItalic>FieldIdentifier</legacyItalic> is a driver-defined field, the application indicates the nature of the field to the Driver Manager by setting the <legacyItalic>BufferLength</legacyItalic> argument. <legacyItalic>BufferLength</legacyItalic> can have the following values:   </para>
          <list class="bullet">
            <listItem>
              <para>If <legacyItalic>ValuePtr</legacyItalic> is a pointer to a character string, then <legacyItalic>BufferLength</legacyItalic> is the length of the string or SQL_NTS.</para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>ValuePtr</legacyItalic> is a pointer to a binary buffer, then the application places the result of the SQL_LEN_BINARY_ATTR(<legacyItalic>length</legacyItalic>) macro in <legacyItalic>BufferLength</legacyItalic>. This places a negative value in <legacyItalic>BufferLength</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>ValuePtr</legacyItalic> is a pointer to a value other than a character string or a binary string, then <legacyItalic>BufferLength</legacyItalic> should have the value SQL_IS_POINTER. </para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>ValuePtr</legacyItalic> contains a fixed-length value, then <legacyItalic>BufferLength</legacyItalic> is either SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT, or SQL_IS_USMALLINT, as appropriate.</para>
            </listItem>
          </list>
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
      <para>When <legacyBold>SQLSetDescField</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DESC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>DescriptorHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLSetDescField</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>01S02</para>
            </TD>
            <TD>
              <para>Option value changed</para>
            </TD>
            <TD>
              <para>The driver did not support the value specified in <legacyItalic>*ValuePtr</legacyItalic> (if <legacyItalic>ValuePtr</legacyItalic> was a pointer) or the value in <legacyItalic>ValuePtr</legacyItalic> (if <legacyItalic>ValuePtr </legacyItalic>was an integer value), or <legacyItalic>*ValuePtr</legacyItalic> was invalid because of implementation working conditions, so the driver substituted a similar value. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>The <legacyItalic>FieldIdentifier</legacyItalic> argument was a record field, the <legacyItalic>RecNumber</legacyItalic> argument was 0, and the <legacyItalic>DescriptorHandle</legacyItalic> argument referred to an IPD handle.</para>
              <para>The <legacyItalic>RecNumber</legacyItalic> argument was less than 0, and the <legacyItalic>DescriptorHandle</legacyItalic> argument referred to an ARD or an APD.</para>
              <para>The <legacyItalic>RecNumber</legacyItalic> argument was greater than the maximum number of columns or parameters that the data source can support, and the <legacyItalic>DescriptorHandle</legacyItalic> argument referred to an APD or ARD.</para>
              <para>(DM) The <legacyItalic>FieldIdentifier</legacyItalic> argument was SQL_DESC_COUNT, and <legacyItalic>*ValuePtr</legacyItalic> argument was less than 0.</para>
              <para>The <legacyItalic>RecNumber</legacyItalic> argument was equal to 0, and the <legacyItalic>DescriptorHandle</legacyItalic> argument referred to an implicitly allocated APD. (This error does not occur with an explicitly allocated application descriptor, because it is not known whether an explicitly allocated application descriptor is an APD or ARD until execute time.)</para>
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
              <para>22001</para>
            </TD>
            <TD>
              <para>String data, right  truncated</para>
            </TD>
            <TD>
              <para>The <legacyItalic>FieldIdentifier</legacyItalic> argument was SQL_DESC_NAME, and the <legacyItalic>BufferLength</legacyItalic> argument was a value larger than SQL_MAX_IDENTIFIER_LEN.</para>
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
              <para>Memory allocation  error</para>
            </TD>
            <TD>
              <para>The driver was unable to allocate memory required to support execution or completion of the function.</para>
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
              <para>(DM) The <legacyItalic>DescriptorHandle</legacyItalic> was associated with a <legacyItalic>StatementHandle</legacyItalic> for which an asynchronously executing function (not this one) was called and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> with which the <legacyItalic>DescriptorHandle</legacyItalic> was associated and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <parameterReference>DescriptorHandle</parameterReference>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLSetDescField</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for one of the statement handles associated with the <parameterReference>DescriptorHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
              <para>HY016</para>
            </TD>
            <TD>
              <para>Cannot modify an implementation row descriptor</para>
            </TD>
            <TD>
              <para>The <legacyItalic>DescriptorHandle</legacyItalic> argument was associated with an IRD, and the <legacyItalic>FieldIdentifier</legacyItalic> argument was not SQL_DESC_ARRAY_STATUS_PTR or SQL_DESC_ROWS_PROCESSED_PTR.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY021</para>
            </TD>
            <TD>
              <para>Inconsistent descriptor information</para>
            </TD>
            <TD>
              <para>The SQL_DESC_TYPE and SQL_DESC_DATETIME_INTERVAL_CODE fields do not form a valid ODBC SQL type or a valid driver-specific SQL type (for IPDs) or a valid ODBC C type (for APDs or ARDs).</para>
              <para>Descriptor information checked during a consistency check was not consistent. (See "Consistency Check" in <legacyBold>SQLSetDescRec</legacyBold>.)</para>
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
              <para>(DM) <legacyItalic>*ValuePtr</legacyItalic> is a character string, and <legacyItalic>BufferLength</legacyItalic> was less than zero but was not equal to SQL_NTS. </para>
              <para>(DM) The driver was an ODBC 2<legacyItalic>.x</legacyItalic> driver, the descriptor was an ARD, the <legacyItalic>ColumnNumber</legacyItalic> argument was set to 0, and the value specified for the argument <legacyItalic>BufferLength</legacyItalic> was not equal to 4. </para>
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
              <para>The value specified for the <legacyItalic>FieldIdentifier</legacyItalic> argument was not an ODBC-defined field and was not an implementation-defined value. </para>
              <para>The <legacyItalic>FieldIdentifier</legacyItalic> argument was invalid for the <legacyItalic>DescriptorHandle</legacyItalic> argument.</para>
              <para>The <legacyItalic>FieldIdentifier</legacyItalic> argument was a read-only, ODBC-defined field.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY092</para>
            </TD>
            <TD>
              <para>Invalid attribute/option identifier</para>
            </TD>
            <TD>
              <para>The value in <legacyItalic>*ValuePtr</legacyItalic> was not valid for the <legacyItalic>FieldIdentifier</legacyItalic> argument.</para>
              <para>The <legacyItalic>FieldIdentifier</legacyItalic> argument was SQL_DESC_UNNAMED, and <legacyItalic>ValuePtr</legacyItalic> was SQL_NAMED.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY105</para>
            </TD>
            <TD>
              <para>Invalid parameter type</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the SQL_DESC_PARAMETER_TYPE field was invalid. (For more information, see the "<legacyItalic>InputOutputType</legacyItalic> Argument" section in <legacyBold>SQLBindParameter</legacyBold>.)</para>
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
              <para>(DM) For more information about suspended state, see <link xlink:href="854f0bb4-17e9-489b-9595-eefffb8ba99f">What's New in ODBC 3.8</link>.</para>
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
              <para>(DM) The driver associated with the <legacyItalic>DescriptorHandle</legacyItalic> does not support the function.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>An application can call <legacyBold>SQLSetDescField</legacyBold> to set any descriptor field one at a time. One call to <legacyBold>SQLSetDescField</legacyBold> sets a single field in a single descriptor. This function can be called to set any field in any descriptor type, provided the field can be set. (See the table later in this section.)</para>
      <alert class="note">
        <para>If a call to <legacyBold>SQLSetDescField</legacyBold> fails, the contents of the descriptor record identified by the <legacyItalic>RecNumber</legacyItalic> argument are undefined.</para>
      </alert>
      <para>Other functions can be called to set multiple descriptor fields with a single call of the function. The <legacyBold>SQLSetDescRec</legacyBold> function sets a variety of fields that affect the data type and buffer bound to a column or parameter (the SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR, and SQL_DESC_INDICATOR_PTR fields). <legacyBold>SQLBindCol </legacyBold>or <legacyBold>SQLBindParameter</legacyBold> can be used to make a complete specification for the binding of a column or parameter. These functions set a specific group of descriptor fields with one function call.</para>
      <para>
        <legacyBold>SQLSetDescField</legacyBold> can be called to change the binding buffers by adding an offset to the binding pointers (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, or SQL_DESC_OCTET_LENGTH_PTR). This changes the binding buffers without calling <legacyBold>SQLBindCol </legacyBold>or <legacyBold>SQLBindParameter</legacyBold>, which allows an application to change SQL_DESC_DATA_PTR without changing other fields, such as SQL_DESC_DATA_TYPE.</para>
      <para>If an application calls <legacyBold>SQLSetDescField</legacyBold> to set any field other than SQL_DESC_COUNT or the deferred fields SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR, or SQL_DESC_INDICATOR_PTR, the record becomes unbound.</para>
      <para>Descriptor header fields are set by calling <legacyBold>SQLSetDescField </legacyBold>with the appropriate <legacyItalic>FieldIdentifier</legacyItalic>. Many header fields are also statement attributes, so they can also be set by a call to <legacyBold>SQLSetStmtAttr</legacyBold>. This allows applications to set a descriptor field without first obtaining a descriptor handle. When <legacyBold>SQLSetDescField</legacyBold> is called to set a header field, the <legacyItalic>RecNumber</legacyItalic> argument is ignored.</para>
      <para>A <legacyItalic>RecNumber</legacyItalic> of 0 is used to set bookmark fields.</para>
      <alert class="note">
        <para>The statement attribute SQL_ATTR_USE_BOOKMARKS should always be set before calling <legacyBold>SQLSetDescField</legacyBold> to set bookmark fields. While this is not mandatory, it is strongly recommended.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Sequence of Setting Descriptor Fields</title>
    <content>
      <para>When setting descriptor fields by calling <legacyBold>SQLSetDescField</legacyBold>, the application must follow a specific sequence:  </para>
      <list class="ordered">
        <listItem>
          <para>The application must first set the SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE, or SQL_DESC_DATETIME_INTERVAL_CODE field. </para>
        </listItem>
        <listItem>
          <para>After one of these fields has been set, the application can set an attribute of a data type, and the driver sets data type attribute fields to the appropriate default values for the data type. Automatic defaulting of type attribute fields ensures that the descriptor is always ready to use once the application has specified a data type. If the application explicitly sets a data type attribute, it is overriding the default attribute.</para>
        </listItem>
        <listItem>
          <para>After one of the fields listed in step 1 has been set, and data type attributes have been set, the application can set SQL_DESC_DATA_PTR. This prompts a consistency check of descriptor fields. If the application changes the data type or attributes after setting the SQL_DESC_DATA_PTR field, the driver sets SQL_DESC_DATA_PTR to a null pointer, unbinding the record. This forces the application to complete the proper steps in sequence, before the descriptor record is usable.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Initialization of Descriptor Fields</title>
    <content>
      <para>When a descriptor is allocated, the fields in the descriptor can be initialized to a default value, be initialized without a default value, or be undefined for the type of descriptor. The following tables indicate the initialization of each field for each type of descriptor, with "D" indicating that the field is initialized with a default, and "ND" indicating that the field is initialized without a default. If a number is shown, the default value of the field is that number. The tables also indicate whether a field is read/write (R/W) or read-only (R). </para>
      <para>The fields of an IRD have a default value only after the statement has been prepared or executed and the IRD has been populated, not when the statement handle or descriptor has been allocated. Until the IRD has been populated, any attempt to gain access to a field of an IRD will return an error.</para>
      <para>Some descriptor fields are defined for one or more, but not all, of the descriptor types (ARDs and IRDs, and APDs and IPDs). When a field is undefined for a type of descriptor, it is not needed by any of the functions that use that descriptor.</para>
      <para>The fields that can be accessed by <legacyBold>SQLGetDescField</legacyBold> cannot necessarily be set by <legacyBold>SQLSetDescField</legacyBold>. Fields that can be set by <legacyBold>SQLSetDescField</legacyBold> are listed in the following tables.</para>
      <para>The initialization of header fields is outlined in the table that follows.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Header field name</para>
            </TD>
            <TD>
              <para>Type</para>
            </TD>
            <TD>
              <para>R/W</para>
            </TD>
            <TD>
              <para>Default</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_DESC_ALLOC_TYPE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: R APD: R IRD: R IPD: R </para>
            </TD>
            <TD>
              <para>ARD: SQL_DESC_ALLOC_AUTO for implicit or SQL_DESC_ALLOC_USER for explicit</para>
              <para>APD: SQL_DESC_ALLOC_AUTO for implicit or SQL_DESC_ALLOC_USER for explicit</para>
              <para>IRD: SQL_DESC_ALLOC_AUTO</para>
              <para>IPD: SQL_DESC_ALLOC_AUTO</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_ARRAY_SIZE</para>
            </TD>
            <TD>
              <para>SQLULEN</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: Unused IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD:[1] APD:[1] IRD: Unused IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_ARRAY_STATUS_PTR</para>
            </TD>
            <TD>
              <para>SQLUSMALLINT*</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R/W IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: Null ptr APD: Null ptr IRD: Null ptr IPD: Null ptr</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_BIND_OFFSET_PTR</para>
            </TD>
            <TD>
              <para>SQLLEN*</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: Unused IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Null ptr APD: Null ptr IRD: Unused IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_BIND_TYPE</para>
            </TD>
            <TD>
              <para>SQLINTEGER</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: Unused IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: SQL_BIND_BY_COLUMN</para>
              <para>APD: SQL_BIND_BY_COLUMN</para>
              <para>IRD: Unused</para>
              <para>IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_COUNT</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: 0 APD: 0 IRD: D IPD: 0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_ROWS_PROCESSED_PTR</para>
            </TD>
            <TD>
              <para>SQLULEN*</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R/W IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: Null ptr IPD: Null ptr</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   These fields are defined only when the IPD is automatically populated by the driver. If not, they are undefined. If an application attempts to set these fields, SQLSTATE HY091 (Invalid descriptor field identifier) will be returned.</para>
      <para>The initialization of record fields is as shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Record field name</para>
            </TD>
            <TD>
              <para>Type</para>
            </TD>
            <TD>
              <para>R/W</para>
            </TD>
            <TD>
              <para>Default</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_DESC_AUTO_UNIQUE_VALUE</para>
            </TD>
            <TD>
              <para>SQLINTEGER</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_BASE_COLUMN_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_BASE_TABLE_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_CASE_SENSITIVE</para>
            </TD>
            <TD>
              <para>SQLINTEGER</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: R</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: D[1]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_CATALOG_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_CONCISE_TYPE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: SQL_C_ DEFAULT APD: SQL_C_ DEFAULT IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_DATA_PTR</para>
            </TD>
            <TD>
              <para>SQLPOINTER</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: Unused IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Null ptr APD: Null ptr IRD: Unused IPD: Unused[2]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_DATETIME_INTERVAL_CODE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_DATETIME_INTERVAL_PRECISION</para>
            </TD>
            <TD>
              <para>SQLINTEGER</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_DISPLAY_SIZE</para>
            </TD>
            <TD>
              <para>SQLLEN</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_FIXED_PREC_SCALE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: R</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: D[1]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_INDICATOR_PTR</para>
            </TD>
            <TD>
              <para>SQLLEN *</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: Unused IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Null ptr APD: Null ptr IRD: Unused IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LABEL</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LENGTH</para>
            </TD>
            <TD>
              <para>SQLULEN</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LITERAL_PREFIX</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LITERAL_SUFFIX</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_LOCAL_TYPE_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: R</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: D[1]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_NULLABLE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: R</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_NUM_PREC_RADIX</para>
            </TD>
            <TD>
              <para>SQLINTEGER</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_OCTET_LENGTH</para>
            </TD>
            <TD>
              <para>SQLLEN</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_OCTET_LENGTH_PTR</para>
            </TD>
            <TD>
              <para>SQLLEN *</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: Unused IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Null ptr APD: Null ptr IRD: Unused IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_PARAMETER_TYPE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: Unused IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: Unused IPD: D=SQL_PARAM_INPUT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_PRECISION</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_ROWVER</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: Unused</para>
              <para>APD: Unused</para>
              <para>IRD: R</para>
              <para>IPD: R</para>
            </TD>
            <TD>
              <para>ARD: Unused</para>
              <para>APD: Unused</para>
              <para>IRD: ND</para>
              <para>IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_SCALE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_SCHEMA_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_SEARCHABLE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_TABLE_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_TYPE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: R/W APD: R/W IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: SQL_C_DEFAULT APD: SQL_C_DEFAULT IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_TYPE_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: R</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: D[1]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_UNNAMED</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: R/W</para>
            </TD>
            <TD>
              <para>ARD: ND APD: ND IRD: D IPD: ND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_UNSIGNED</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: R</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: D[1]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESC_UPDATABLE</para>
            </TD>
            <TD>
              <para>SQLSMALLINT</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: R IPD: Unused</para>
            </TD>
            <TD>
              <para>ARD: Unused APD: Unused IRD: D IPD: Unused</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   These fields are defined only when the IPD is automatically populated by the driver. If not, they are undefined. If an application attempts to set these fields, SQLSTATE HY091 (Invalid descriptor field identifier) will be returned.</para>
      <para>[2]   The SQL_DESC_DATA_PTR field in the IPD can be set to force a consistency check. In a subsequent call to <legacyBold>SQLGetDescField</legacyBold> or <legacyBold>SQLGetDescRec</legacyBold>, the driver is not required to return the value that SQL_DESC_DATA_PTR was set to.</para>
    </content>
  </section>
  <section>
    <title>FieldIdentifier Argument</title>
    <content>
      <para>The <legacyItalic>FieldIdentifier</legacyItalic> argument indicates the descriptor field to be set. A descriptor contains the <legacyItalic>descriptor header,</legacyItalic> consisting of the header fields described in the next section, "Header Fields," and zero or more <legacyItalic>descriptor records,</legacyItalic> consisting of the record fields described in the section following the "Header Fields" section.</para>
    </content>
  </section>
  <section>
    <title>Header Fields</title>
    <content>
      <para>Each descriptor has a header consisting of the following fields:  </para>
      <definitionTable>
        <definedTerm> <legacyBold>SQL_DESC_ALLOC_TYPE [All]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLSMALLINT header field specifies whether the descriptor was allocated automatically by the driver or explicitly by the application. The application can obtain, but not modify, this field. The field is set to SQL_DESC_ALLOC_AUTO by the driver if the descriptor was automatically allocated by the driver. It is set to SQL_DESC_ALLOC_USER by the driver if the descriptor was explicitly allocated by the application.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_ARRAY_SIZE [Application descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>In ARDs, this SQLULEN header field specifies the number of rows in the rowset. This is the number of rows to be returned by a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> or to be operated on by a call to <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>.</para>
          <para>In APDs, this SQLULEN header field specifies the number of values for each parameter.</para>
          <para>The default value of this field is 1. If SQL_DESC_ARRAY_SIZE is greater than 1, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR of the APD or ARD point to arrays. The cardinality of each array is equal to the value of this field.   </para>
          <para>This field in the ARD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_ROW_ARRAY_SIZE attribute. This field in the APD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_PARAMSET_SIZE attribute. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_ARRAY_STATUS_PTR [All]</legacyBold> </definedTerm>
        <definition>
          <para>For each descriptor type, this SQLUSMALLINT * header field points to an array of SQLUSMALLINT values. These arrays are named as follows: row status array (IRD), parameter status array (IPD), row operation array (ARD), and parameter operation array (APD).</para>
          <para>In the IRD, this header field points to a row status array containing status values after a call to <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLSetPos</legacyBold>. The array has as many elements as there are rows in the rowset. The application must allocate an array of SQLUSMALLINTs and set this field to point to the array. The field is set to a null pointer by default. The driver will populate the array — unless the SQL_DESC_ARRAY_STATUS_PTR field is set to a null pointer, in which case no status values are generated and the array is not populated.    </para>
          <alert class="caution">
            <para>Driver behavior is undefined if the application sets the elements of the row status array pointed to by the SQL_DESC_ARRAY_STATUS_PTR field of the IRD.</para>
          </alert>
          <para>The array is initially populated by a call to <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLSetPos</legacyBold>. If the call did not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the contents of the array pointed to by this field are undefined. The elements in the array can contain the following values:   </para>
          <list class="bullet">
            <listItem>
              <para>SQL_ROW_SUCCESS: The row was successfully fetched and has not changed since it was last fetched.</para>
            </listItem>
            <listItem>
              <para>SQL_ROW_SUCCESS_WITH_INFO: The row was successfully fetched and has not changed since it was last fetched. However, a warning was returned about the row.</para>
            </listItem>
            <listItem>
              <para>SQL_ROW_ERROR: An error occurred while fetching the row.</para>
            </listItem>
            <listItem>
              <para>SQL_ROW_UPDATED: The row was successfully fetched and has been updated since it was last fetched. If the row is fetched again, its status is SQL_ROW_SUCCESS.</para>
            </listItem>
            <listItem>
              <para>SQL_ROW_DELETED: The row has been deleted since it was last fetched.</para>
            </listItem>
            <listItem>
              <para>SQL_ROW_ADDED: The row was inserted by <legacyBold>SQLBulkOperations</legacyBold>. If the row is fetched again, its status is SQL_ROW_SUCCESS.</para>
            </listItem>
            <listItem>
              <para>SQL_ROW_NOROW: The rowset overlapped the end of the result set, and no row was returned that corresponded to this element of the row status array.</para>
            </listItem>
          </list>
          <para>This field in the IRD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_ROW_STATUS_PTR attribute.   </para>
          <para>The SQL_DESC_ARRAY_STATUS_PTR field of the IRD is valid only after SQL_SUCCESS or SQL_SUCCESS_WITH_INFO has been returned. If the return code is not one of these, the location pointed to by SQL_DESC_ROWS_PROCESSED_PTR is undefined.</para>
          <para>In the IPD, this header field points to a parameter status array containing status information for each set of parameter values after a call to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>. If the call to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> did not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the contents of the array pointed to by this field are undefined. The application must allocate an array of SQLUSMALLINTs and set this field to point to the array. The driver will populate the array — unless the SQL_DESC_ARRAY_STATUS_PTR field is set to a null pointer, in which case no status values are generated and the array is not populated. The elements in the array can contain the following values:   </para>
          <list class="bullet">
            <listItem>
              <para>SQL_PARAM_SUCCESS: The SQL statement was successfully executed for this set of parameters.</para>
            </listItem>
            <listItem>
              <para>SQL_PARAM_SUCCESS_WITH_INFO: The SQL statement was successfully executed for this set of parameters; however, warning information is available in the diagnostics data structure.</para>
            </listItem>
            <listItem>
              <para>SQL_PARAM_ERROR: An error occurred in processing this set of parameters. Additional error information is available in the diagnostics data structure.</para>
            </listItem>
            <listItem>
              <para>SQL_PARAM_UNUSED: This parameter set was unused, possibly due to the fact that some previous parameter set caused an error that aborted further processing, or because SQL_PARAM_IGNORE was set for that set of parameters in the array specified by the SQL_DESC_ARRAY_STATUS_PTR field of the APD.</para>
            </listItem>
            <listItem>
              <para>SQL_PARAM_DIAG_UNAVAILABLE: Diagnostic information is not available. An example of this is when the driver treats arrays of parameters as a monolithic unit and so does not generate this level of error information.</para>
            </listItem>
          </list>
          <para>This field in the IPD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_PARAM_STATUS_PTR attribute.   </para>
          <para>In the ARD, this header field points to a row operation array of values that can be set by the application to indicate whether this row is to be ignored for <legacyBold>SQLSetPos</legacyBold> operations. The elements in the array can contain the following values:   </para>
          <list class="bullet">
            <listItem>
              <para>SQL_ROW_PROCEED: The row is included in the bulk operation using <legacyBold>SQLSetPos</legacyBold>. (This setting does not guarantee that the operation will occur on the row. If the row has the status SQL_ROW_ERROR in the IRD row status array, the driver might not be able to perform the operation in the row.)</para>
            </listItem>
            <listItem>
              <para>SQL_ROW_IGNORE: The row is excluded from the bulk operation using <legacyBold>SQLSetPos</legacyBold>.</para>
            </listItem>
          </list>
          <para>If no elements of the array are set, all rows are included in the bulk operation. If the value in the SQL_DESC_ARRAY_STATUS_PTR field of the ARD is a null pointer, all rows are included in the bulk operation; the interpretation is the same as if the pointer pointed to a valid array and all elements of the array were SQL_ROW_PROCEED. If an element in the array is set to SQL_ROW_IGNORE, the value in the row status array for the ignored row is not changed.   </para>
          <para>This field in the ARD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_ROW_OPERATION_PTR attribute.   </para>
          <para>In the APD, this header field points to a parameter operation array of values that can be set by the application to indicate whether this set of parameters is to be ignored when <legacyBold>SQLExecute</legacyBold> or<legacyBold> SQLExecDirect</legacyBold> is called. The elements in the array can contain the following values:   </para>
          <list class="bullet">
            <listItem>
              <para>SQL_PARAM_PROCEED: The set of parameters is included in the <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> call.</para>
            </listItem>
            <listItem>
              <para>SQL_PARAM_IGNORE: The set of parameters is excluded from the <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> call.</para>
            </listItem>
          </list>
          <para>If no elements of the array are set, all sets of parameters in the array are used in the <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> calls. If the value in the SQL_DESC_ARRAY_STATUS_PTR field of the APD is a null pointer, all sets of parameters are used; the interpretation is the same as if the pointer pointed to a valid array and all elements of the array were SQL_PARAM_PROCEED.   </para>
          <para>This field in the APD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_PARAM_OPERATION_PTR attribute. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_BIND_OFFSET_PTR [Application descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLLEN * header field points to the binding offset. It is set to a null pointer by default. If this field is not a null pointer, the driver dereferences the pointer and adds the dereferenced value to each of the deferred fields that has a non-null value in the descriptor record (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR) at fetch time and uses the new pointer values when binding.</para>
          <para>The binding offset is always added directly to the values in the SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR fields. If the offset is changed to a different value, the new value is still added directly to the value in each descriptor field. The new offset is not added to the field value plus any earlier offset.   </para>
          <para>This field is a <legacyItalic>deferred field</legacyItalic>: It is not used at the time it is set but is used at a later time by the driver when it needs to determine addresses for data buffers.   </para>
          <para>This field in the ARD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_ROW_BIND_OFFSET_PTR attribute. This field in the ARD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_PARAM_BIND_OFFSET_PTR attribute.   </para>
          <para>For more information, see the description of row-wise binding in <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll</legacyLink> and <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink>. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_BIND_TYPE [Application descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLUINTEGER header field sets the binding orientation to be used for binding either columns or parameters.</para>
          <para>In ARDs, this field specifies the binding orientation when <legacyBold>SQLFetchScroll</legacyBold> or <legacyBold>SQLFetch</legacyBold> is called on the associated statement handle.   </para>
          <para>To select column-wise binding for columns, this field is set to SQL_BIND_BY_COLUMN (the default).   </para>
          <para>This field in the ARD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_ROW_BIND_TYPE <legacyItalic>Attribute</legacyItalic>.   </para>
          <para>In APDs, this field specifies the binding orientation to be used for dynamic parameters.   </para>
          <para>To select column-wise binding for parameters, this field is set to SQL_BIND_BY_COLUMN (the default).   </para>
          <para>This field in the APD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_PARAM_BIND_TYPE <legacyItalic>Attribute</legacyItalic>. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_COUNT [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLSMALLINT header field specifies the 1-based index of the highest-numbered record that contains data. When the driver sets the data structure for the descriptor, it must also set the SQL_DESC_COUNT field to show how many records are significant. When an application allocates an instance of this data structure, it does not have to specify how many records to reserve room for. As the application specifies the contents of the records, the driver takes any required action to ensure that the descriptor handle refers to a data structure of the adequate size.</para>
          <para>SQL_DESC_COUNT is not a count of all data columns that are bound (if the field is in an ARD) or of all parameters that are bound (if the field is in an APD), but the number of the highest-numbered record. If the highest-numbered column or parameter is unbound, then SQL_DESC_COUNT is changed to the number of the next highest-numbered column or parameter. If a column or a parameter with a number that is less than the number of the highest-numbered column is unbound (by calling <legacyBold>SQLBindCol</legacyBold> with the <legacyItalic>TargetValuePtr</legacyItalic> argument set to a null pointer, or <legacyBold>SQLBindParameter</legacyBold> with the <legacyItalic>ParameterValuePtr</legacyItalic> argument set to a null pointer), SQL_DESC_COUNT is not changed. If additional columns or parameters are bound with numbers greater than the highest-numbered record that contains data, the driver automatically increases the value in the SQL_DESC_COUNT field. If all columns are unbound by calling <legacyBold>SQLFreeStmt</legacyBold> with the SQL_UNBIND option, the SQL_DESC_COUNT fields in the ARD and IRD are set to 0. If <legacyBold>SQLFreeStmt</legacyBold> is called with the SQL_RESET_PARAMS option, the SQL_DESC_COUNT fields in the APD and IPD are set to 0.   </para>
          <para>The value in SQL_DESC_COUNT can be set explicitly by an application by calling <legacyBold>SQLSetDescField</legacyBold>. If the value in SQL_DESC_COUNT is explicitly decreased, all records with numbers greater than the new value in SQL_DESC_COUNT are effectively removed. If the value in SQL_DESC_COUNT is explicitly set to 0 and the field is in an ARD, all data buffers except a bound bookmark column are released.   </para>
          <para>The record count in this field of an ARD does not include a bound bookmark column. The only way to unbind a bookmark column is to set the SQL_DESC_DATA_PTR field to a null pointer. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_ROWS_PROCESSED_PTR [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>In an IRD, this SQLULEN * header field points to a buffer containing the number of rows fetched after a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>, or the number of rows affected in a bulk operation performed by a call to <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>, including error rows.</para>
          <para>In an IPD, this SQLUINTEGER * header field points to a buffer containing the number of sets of parameters that have been processed, including error sets. No number will be returned if this is a null pointer.   </para>
          <para>SQL_DESC_ROWS_PROCESSED_PTR is valid only after SQL_SUCCESS or SQL_SUCCESS_WITH_INFO has been returned after a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll </legacyBold>(for an IRD field) or <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or <legacyBold>SQLParamData</legacyBold> (for an IPD field). If the call that fills in the buffer pointed to by this field does not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the contents of the buffer are undefined, unless it returns SQL_NO_DATA, in which case the value in the buffer is set to 0.   </para>
          <para>This field in the ARD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_ROWS_FETCHED_PTR attribute. This field in the APD can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_PARAMS_PROCESSED_PTR attribute.   </para>
          <para>The buffer pointed to by this field is allocated by the application. It is a deferred output buffer that is set by the driver. It is set to a null pointer by default. </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Record Fields</title>
    <content>
      <para>Each descriptor contains one or more records consisting of fields that define either column data or dynamic parameters, depending on the type of descriptor. Each record is a complete definition of a single column or parameter.  </para>
      <definitionTable>
        <definedTerm> <legacyBold>SQL_DESC_AUTO_UNIQUE_VALUE [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLINTEGER record field contains SQL_TRUE if the column is an auto-incrementing column, or SQL_FALSE if the column is not an auto-incrementing column. This field is read-only, but the underlying auto-incrementing column is not necessarily read-only.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_BASE_COLUMN_NAME [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains the base column name for the result set column. If a base column name does not exist (as in the case of columns that are expressions), this variable contains an empty string.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_BASE_TABLE_NAME [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains the base table name for the result set column. If a base table name cannot be defined or is not applicable, this variable contains an empty string.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_CASE_SENSITIVE [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLINTEGER record field contains SQL_TRUE if the column or parameter is treated as case-sensitive for collations and comparisons, or SQL_FALSE if the column is not treated as case-sensitive for collations and comparisons or if it is a noncharacter column.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_CATALOG_NAME [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains the catalog for the base table that contains the column. The return value is driver-dependent if the column is an expression or if the column is part of a view. If the data source does not support catalogs or the catalog cannot be determined, this variable contains an empty string.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_CONCISE_TYPE [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLSMALLINT header field specifies the concise data type for all data types, including the datetime and interval data types.</para>
          <para>The values in the SQL_DESC_CONCISE_TYPE, SQL_DESC_TYPE, and SQL_DESC_DATETIME_INTERVAL_CODE fields are interdependent. Each time one of the fields is set, the other must also be set. SQL_DESC_CONCISE_TYPE can be set by a call to <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLBindParameter</legacyBold>, or <legacyBold>SQLSetDescField</legacyBold>. SQL_DESC_TYPE can be set by a call to <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>.    </para>
          <para>If SQL_DESC_CONCISE_TYPE is set to a concise data type other than an interval or datetime data type, the SQL_DESC_TYPE field is set to the same value and the SQL_DESC_DATETIME_INTERVAL_CODE field is set to 0.   </para>
          <para>If SQL_DESC_CONCISE_TYPE is set to the concise datetime or interval data type, the SQL_DESC_TYPE field is set to the corresponding verbose type (SQL_DATETIME or SQL_INTERVAL) and the SQL_DESC_DATETIME_INTERVAL_CODE field is set to the appropriate subcode. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_DATA_PTR [Application descriptors and IPDs]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLPOINTER record field points to a variable that will contain the parameter value (for APDs) or the column value (for ARDs). This field is a <legacyItalic>deferred field</legacyItalic>. It is not used at the time it is set but is used at a later time by the driver to retrieve data.</para>
          <para>The column specified by the SQL_DESC_DATA_PTR field of the ARD is unbound if the <legacyItalic>TargetValuePtr</legacyItalic> argument in a call to <legacyBold>SQLBindCol</legacyBold> is a null pointer or if the SQL_DESC_DATA_PTR field in the ARD is set by a call to <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold> to a null pointer. Other fields are not affected if the SQL_DESC_DATA_PTR field is set to a null pointer.    </para>
          <para>If the call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll </legacyBold>that fills in the buffer pointed to by this field did not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the contents of the buffer are undefined.   </para>
          <para>Whenever the SQL_DESC_DATA_PTR field of an APD, ARD, or IPD is set, the driver checks that the value in the SQL_DESC_TYPE field contains one of the valid ODBC C data types or a driver-specific data type, and that all other fields affecting the data types are consistent. Prompting a consistency check is the only use of the SQL_DESC_DATA_PTR field of an IPD. Specifically, if an application sets the SQL_DESC_DATA_PTR field of an IPD and later calls <legacyBold>SQLGetDescField</legacyBold> on this field, it is not necessarily returned the value that it had set. For more information, see "Consistency Checks" in <legacyLink xlink:href="bf55256c-7eb7-4e3f-97ef-b0fee09ba829">SQLSetDescRec</legacyLink>. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_DATETIME_INTERVAL_CODE [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLSMALLINT record field contains the subcode for the specific datetime or interval data type when the SQL_DESC_TYPE field is SQL_DATETIME or SQL_INTERVAL. This is true for both SQL and C data types. The code consists of the data type name with "CODE" substituted for either "TYPE" or "C_TYPE" (for datetime types), or "CODE" substituted for "INTERVAL" or "C_INTERVAL" (for interval types).</para>
          <para>If SQL_DESC_TYPE and SQL_DESC_CONCISE_TYPE in an application descriptor are set to SQL_C_DEFAULT and the descriptor is not associated with a statement handle, the contents of SQL_DESC_DATETIME_INTERVAL_CODE are undefined.   </para>
          <para>This field can be set for the datetime data types listed in the following table.   </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Datetime types</para>
                </TD>
                <TD>
                  <para>DATETIME_INTERVAL_CODE</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>SQL_TYPE_DATE/SQL_C_TYPE_DATE</para>
                </TD>
                <TD>
                  <para>SQL_CODE_DATE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_TYPE_TIME/SQL_C_TYPE_TIME</para>
                </TD>
                <TD>
                  <para>SQL_CODE_TIME</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_TYPE_TIMESTAMP/ SQL_C_TYPE_TIMESTAMP</para>
                </TD>
                <TD>
                  <para>SQL_CODE_TIMESTAMP</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>This field can be set for the interval data types listed in the following table.   </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Interval type</para>
                </TD>
                <TD>
                  <para>DATETIME_INTERVAL_CODE</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_DAY/ SQL_C_INTERVAL_DAY</para>
                </TD>
                <TD>
                  <para>SQL_CODE_DAY</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_DAY_TO_HOUR/ SQL_C_INTERVAL_DAY_TO_HOUR</para>
                </TD>
                <TD>
                  <para>SQL_CODE_DAY_TO_HOUR</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_DAY_TO_MINUTE/ SQL_C_INTERVAL_DAY_TO_MINUTE</para>
                </TD>
                <TD>
                  <para>SQL_CODE_DAY_TO_MINUTE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_DAY_TO_SECOND/ SQL_C_INTERVAL_DAY_TO_SECOND</para>
                </TD>
                <TD>
                  <para>SQL_CODE_DAY_TO_SECOND</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_HOUR/ SQL_C_INTERVAL_HOUR</para>
                </TD>
                <TD>
                  <para>SQL_CODE_HOUR</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_HOUR_TO_MINUTE/ SQL_C_INTERVAL_HOUR_TO_MINUTE</para>
                </TD>
                <TD>
                  <para>SQL_CODE_HOUR_TO_MINUTE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_HOUR_TO_SECOND/ SQL_C_INTERVAL_HOUR_TO_SECOND</para>
                </TD>
                <TD>
                  <para>SQL_CODE_HOUR_TO_SECOND</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_MINUTE/ SQL_C_INTERVAL_MINUTE</para>
                </TD>
                <TD>
                  <para>SQL_CODE_MINUTE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_MINUTE_TO_SECOND/ SQL_C_INTERVAL_MINUTE_TO_SECOND</para>
                </TD>
                <TD>
                  <para>SQL_CODE_MINUTE_TO_SECOND</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_MONTH/ SQL_C_INTERVAL_MONTH</para>
                </TD>
                <TD>
                  <para>SQL_CODE_MONTH</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_SECOND/ SQL_C_INTERVAL_SECOND</para>
                </TD>
                <TD>
                  <para>SQL_CODE_SECOND</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_YEAR/ SQL_C_INTERVAL_YEAR</para>
                </TD>
                <TD>
                  <para>SQL_CODE_YEAR</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL_YEAR_TO_MONTH/ SQL_C_INTERVAL_YEAR_TO_MONTH</para>
                </TD>
                <TD>
                  <para>SQL_CODE_YEAR_TO_MONTH</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>For more information about the data intervals and this field, see <legacyLink xlink:href="f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab">Data Type Identifiers and Descriptors</legacyLink>. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_DATETIME_INTERVAL_PRECISION [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLINTEGER record field contains the interval leading precision if the SQL_DESC_TYPE field is SQL_INTERVAL. When the SQL_DESC_DATETIME_INTERVAL_CODE field is set to an interval data type, this field is set to the default interval leading precision.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_DISPLAY_SIZE [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLINTEGER record field contains the maximum number of characters required to display the data from the column. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_FIXED_PREC_SCALE [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLSMALLINT record field is set to SQL_TRUE if the column is an exact numeric column and has a fixed precision and nonzero scale, or to SQL_FALSE if the column is not an exact numeric column with a fixed precision and scale.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_INDICATOR_PTR [Application descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>In ARDs, this SQLLEN * record field points to the indicator variable. This variable contains SQL_NULL_DATA if the column value is a NULL. For APDs, the indicator variable is set to SQL_NULL_DATA to specify NULL dynamic arguments. Otherwise, the variable is zero (unless the values in SQL_DESC_INDICATOR_PTR and SQL_DESC_OCTET_LENGTH_PTR are the same pointer).</para>
          <para>If the SQL_DESC_INDICATOR_PTR field in an ARD is a null pointer, the driver is prevented from returning information about whether the column is NULL or not. If the column is NULL and SQL_DESC_INDICATOR_PTR is a null pointer, SQLSTATE 22002 (Indicator variable required but not supplied) is returned when the driver attempts to populate the buffer after a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. If the call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll </legacyBold>did not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the contents of the buffer are undefined.   </para>
          <para>The SQL_DESC_INDICATOR_PTR field determines whether the field pointed to by SQL_DESC_OCTET_LENGTH_PTR is set. If the data value for a column is NULL, the driver sets the indicator variable to SQL_NULL_DATA. The field pointed to by SQL_DESC_OCTET_LENGTH_PTR is then not set. If a NULL value is not encountered during the fetch, the buffer pointed to by SQL_DESC_INDICATOR_PTR is set to zero and the buffer pointed to by SQL_DESC_OCTET_LENGTH_PTR is set to the length of the data.   </para>
          <para>If the SQL_DESC_INDICATOR_PTR field in an APD is a null pointer, the application cannot use this descriptor record to specify NULL arguments.   </para>
          <para>This field is a <legacyItalic>deferred field</legacyItalic>: It is not used at the time it is set but is used at a later time by the driver to indicate nullability (for ARDs) or to determine nullability (for APDs). </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_LABEL [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains the column label or title. If the column does not have a label, this variable contains the column name. If the column is unnamed and unlabeled, this variable contains an empty string.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_LENGTH [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLULEN record field is either the maximum or actual length of a character string in characters or a binary data type in bytes. It is the maximum length for a fixed-length data type, or the actual length for a variable-length data type. Its value always excludes the null-termination character that ends the character string. For values whose type is SQL_TYPE_DATE, SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP, or one of the SQL interval data types, this field has the length in characters of the character string representation of the datetime or interval value. </para>
          <para>The value in this field may be different from the value for "length" as defined in ODBC 2<legacyItalic>.x</legacyItalic>. For more information, see <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_LITERAL_PREFIX [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains the character or characters that the driver recognizes as a prefix for a literal of this data type. This variable contains an empty string for a data type for which a literal prefix is not applicable.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_LITERAL_SUFFIX [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains the character or characters that the driver recognizes as a suffix for a literal of this data type. This variable contains an empty string for a data type for which a literal suffix is not applicable.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_LOCAL_TYPE_NAME [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains any localized (native language) name for the data type that may be different from the regular name of the data type. If there is no localized name, an empty string is returned. This field is for display purposes only.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_NAME [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLCHAR * record field in a row descriptor contains the column alias, if it applies. If the column alias does not apply, the column name is returned. In either case, the driver sets the SQL_DESC_UNNAMED field to SQL_NAMED when it sets the SQL_DESC_NAME field. If there is no column name or a column alias, the driver returns an empty string in the SQL_DESC_NAME field and sets the SQL_DESC_UNNAMED field to SQL_UNNAMED. </para>
          <para>An application can set the SQL_DESC_NAME field of an IPD to a parameter name or alias to specify stored procedure parameters by name. (For more information, see <legacyLink xlink:href="e2c3da5a-6c10-4dd5-acf9-e951eea71a6b">Binding Parameters by Name (Named Parameters)</legacyLink>.) The SQL_DESC_NAME field of an IRD is a read-only field; SQLSTATE HY091 (Invalid descriptor field identifier) will be returned if an application attempts to set it.   </para>
          <para>In IPDs, this field is undefined if the driver does not support named parameters. If the driver supports named parameters and is capable of describing parameters, the parameter name is returned in this field. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_NULLABLE [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>In IRDs, this read-only SQLSMALLINT record field is SQL_NULLABLE if the column can have NULL values, SQL_NO_NULLS if the column does not have NULL values, or SQL_NULLABLE_UNKNOWN if it is not known whether the column accepts NULL values. This field pertains to the result set column, not the base column.</para>
          <para>In IPDs, this field is always set to SQL_NULLABLE because dynamic parameters are always nullable and cannot be set by an application. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_NUM_PREC_RADIX [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLINTEGER field contains a value of 2 if the data type in the SQL_DESC_TYPE field is an approximate numeric data type, because the SQL_DESC_PRECISION field contains the number of bits. This field contains a value of 10 if the data type in the SQL_DESC_TYPE field is an exact numeric data type, because the SQL_DESC_PRECISION field contains the number of decimal digits. This field is set to 0 for all non-numeric data types.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_OCTET_LENGTH [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLLEN record field contains the length, in bytes, of a character string or binary data type. For fixed-length character or binary types, this is the actual length in bytes. For variable-length character or binary types, this is the maximum length in bytes. This value always excludes space for the null-termination character for implementation descriptors and always includes space for the null-termination character for application descriptors. For application data, this field contains the size of the buffer. For APDs, this field is defined only for output or input/output parameters.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_OCTET_LENGTH_PTR [Application descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLLEN * record field points to a variable that will contain the total length in bytes of a dynamic argument (for parameter descriptors) or of a bound column value (for row descriptors). </para>
          <para>For an APD, this value is ignored for all arguments except character string and binary; if this field points to SQL_NTS, the dynamic argument must be null-terminated. To indicate that a bound parameter will be a data-at-execution parameter, an application sets this field in the appropriate record of the APD to a variable that, at execute time, will contain the value SQL_DATA_AT_EXEC or the result of the SQL_LEN_DATA_AT_EXEC macro. If there is more than one such field, SQL_DESC_DATA_PTR can be set to a value uniquely identifying the parameter to help the application determine which parameter is being requested.   </para>
          <para>If the OCTET_LENGTH_PTR field of an ARD is a null pointer, the driver does not return length information for the column. If the SQL_DESC_OCTET_LENGTH_PTR field of an APD is a null pointer, the driver assumes that character strings and binary values are null-terminated. (Binary values should not be null-terminated but should be given a length to avoid truncation.)   </para>
          <para>If the call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> that fills in the buffer pointed to by this field did not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the contents of the buffer are undefined. This field is a <legacyItalic>deferred field</legacyItalic>. It is not used at the time it is set but is used at a later time by the driver to determine or indicate the octet length of the data. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_PARAMETER_TYPE [IPDs]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLSMALLINT record field is set to SQL_PARAM_INPUT for an input parameter, SQL_PARAM_INPUT_OUTPUT for an input/output parameter, SQL_PARAM_OUTPUT for an output parameter, SQL_PARAM_INPUT_OUTPUT_STREAM for an input/output streamed parameter, or SQL_PARAM_OUTPUT_STREAM for an output streamed parameter. It is set to SQL_PARAM_INPUT by default. </para>
          <para>For an IPD, the field is set to SQL_PARAM_INPUT by default if the IPD is not automatically populated by the driver (the SQL_ATTR_ENABLE_AUTO_IPD statement attribute is SQL_FALSE). An application should set this field in the IPD for parameters that are not input parameters. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_PRECISION [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLSMALLINT record field contains the number of digits for an exact numeric type, the number of bits in the mantissa (binary precision) for an approximate numeric type, or the numbers of digits in the fractional seconds component for the SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP, or SQL_INTERVAL_SECOND data type. This field is undefined for all other data types.</para>
          <para>The value in this field may be different from the value for "precision" as defined in ODBC 2<legacyItalic>.x</legacyItalic>. For more information, see <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_ROWVER [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLSMALLINTrecord field indicates whether a column is automatically modified by the DBMS when a row is updated (for example, a column of the type "timestamp" in SQL Server). The value of this record field is set to SQL_TRUE if the column is a row versioning column, and to SQL_FALSE otherwise. This column attribute is similar to calling <legacyBold>SQLSpecialColumns</legacyBold> with IdentifierType of SQL_ROWVER to determine whether a column is automatically updated.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_SCALE [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLSMALLINT record field contains the defined scale for decimal and numeric data types. The field is undefined for all other data types.</para>
          <para>The value in this field may be different from the value for "scale" as defined in ODBC 2<legacyItalic>.x</legacyItalic>. For more information, see <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_SCHEMA_NAME [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains the schema name of the base table that contains the column. The return value is driver-dependent if the column is an expression or if the column is part of a view. If the data source does not support schemas or the schema name cannot be determined, this variable contains an empty string.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_SEARCHABLE [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLSMALLINT record field is set to one of the following values:</para>
          <list class="bullet">
            <listItem>
              <para>SQL_PRED_NONE if the column cannot be used in a <legacyBold>WHERE</legacyBold> clause. (This is the same as the SQL_UNSEARCHABLE value in ODBC 2<legacyItalic>.x</legacyItalic>.)</para>
            </listItem>
            <listItem>
              <para>SQL_PRED_CHAR if the column can be used in a <legacyBold>WHERE</legacyBold> clause but only with the <legacyBold>LIKE</legacyBold> predicate. (This is the same as the SQL_LIKE_ONLY value in ODBC 2<legacyItalic>.x</legacyItalic>.)</para>
            </listItem>
            <listItem>
              <para>SQL_PRED_BASIC if the column can be used in a <legacyBold>WHERE</legacyBold> clause with all the comparison operators except <legacyBold>LIKE</legacyBold>. (This is the same as the SQL_EXCEPT_LIKE value in ODBC 2<legacyItalic>.x</legacyItalic>.)</para>
            </listItem>
            <listItem>
              <para>SQL_PRED_SEARCHABLE if the column can be used in a <legacyBold>WHERE</legacyBold> clause with any comparison operator.</para>
            </listItem>
          </list>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_TABLE_NAME [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains the name of the base table that contains this column. The return value is driver-dependent if the column is an expression or if the column is part of a view.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_TYPE [All]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLSMALLINT record field specifies the concise SQL or C data type for all data types except datetime and interval data types. For the datetime and interval data types, this field specifies the verbose data type, which is SQL_DATETIME or SQL_INTERVAL.</para>
          <para>Whenever this field contains SQL_DATETIME or SQL_INTERVAL, the SQL_DESC_DATETIME_INTERVAL_CODE field must contain the appropriate subcode for the concise type. For datetime data types, SQL_DESC_TYPE contains SQL_DATETIME, and the SQL_DESC_DATETIME_INTERVAL_CODE field contains a subcode for the specific datetime data type. For interval data types, SQL_DESC_TYPE contains SQL_INTERVAL and the SQL_DESC_DATETIME_INTERVAL_CODE field contains a subcode for the specific interval data type.   </para>
          <para>The values in the SQL_DESC_TYPE and SQL_DESC_CONCISE_TYPE fields are interdependent. Each time one of the fields is set, the other must also be set. SQL_DESC_TYPE can be set by a call to <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>. SQL_DESC_CONCISE_TYPE can be set by a call to <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLBindParameter</legacyBold>, or <legacyBold>SQLSetDescField</legacyBold>.    </para>
          <para>If SQL_DESC_TYPE is set to a concise data type other than an interval or datetime data type, the SQL_DESC_CONCISE_TYPE field is set to the same value and the SQL_DESC_DATETIME_INTERVAL_CODE field is set to 0.   </para>
          <para>If SQL_DESC_TYPE is set to the verbose datetime or interval data type (SQL_DATETIME or SQL_INTERVAL) and the SQL_DESC_DATETIME_INTERVAL_CODE field is set to the appropriate subcode, the SQL_DESC_CONCISE TYPE field is set to the corresponding concise type. Trying to set SQL_DESC_TYPE to one of the concise datetime or interval types will return SQLSTATE HY021 (Inconsistent descriptor information).   </para>
          <para>When the SQL_DESC_TYPE field is set by a call to <legacyBold>SQLBindCol</legacyBold>, <legacyBold>SQLBindParameter</legacyBold>, or <legacyBold>SQLSetDescField</legacyBold>, the following fields are set to the following default values, as shown in the table below. The values of the remaining fields of the same record are undefined.   </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Value of SQL_DESC_TYPE</para>
                </TD>
                <TD>
                  <para>Other fields implicitly set</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>SQL_CHAR, SQL_VARCHAR, SQL_C_CHAR, SQL_C_VARCHAR</para>
                </TD>
                <TD>
                  <para>SQL_DESC_LENGTH is set to 1. SQL_DESC_PRECISION is set to 0.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DATETIME</para>
                </TD>
                <TD>
                  <para>When SQL_DESC_DATETIME_INTERVAL_CODE is set to SQL_CODE_DATE or SQL_CODE_TIME, SQL_DESC_PRECISION is set to 0. When it is set to SQL_DESC_TIMESTAMP, SQL_DESC_PRECISION is set to 6.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_DECIMAL, SQL_NUMERIC, SQL_C_NUMERIC</para>
                </TD>
                <TD>
                  <para>SQL_DESC_SCALE is set to 0. SQL_DESC_PRECISION is set to the implementation-defined precision for the respective data type.</para>
                  <para>See <link xlink:href="76f8b5d5-4bd0-4dcb-a90a-698340e0d36e">SQL to C: Numeric</link> for information on how to manually bind a SQL_C_NUMERIC value.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_FLOAT, SQL_C_FLOAT</para>
                </TD>
                <TD>
                  <para>SQL_DESC_PRECISION is set to the implementation-defined default precision for SQL_FLOAT.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_INTERVAL</para>
                </TD>
                <TD>
                  <para>When SQL_DESC_DATETIME_INTERVAL_CODE is set to an interval data type, SQL_DESC_DATETIME_INTERVAL_PRECISION is set to 2 (the default interval leading precision). When the interval has a seconds component, SQL_DESC_PRECISION is set to 6 (the default interval seconds precision).</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>When an application calls <legacyBold>SQLSetDescField</legacyBold> to set fields of a descriptor rather than calling <legacyBold>SQLSetDescRec</legacyBold>, the application must first declare the data type. When it does, the other fields indicated in the previous table are implicitly set. If any of the values implicitly set are unacceptable, the application can then call <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold> to set the unacceptable value explicitly. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_TYPE_NAME [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLCHAR * record field contains the data source–dependent type name (for example, "CHAR", "VARCHAR", and so on). If the data type name is unknown, this variable contains an empty string.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_UNNAMED [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This SQLSMALLINT record field in a row descriptor is set by the driver to either SQL_NAMED or SQL_UNNAMED when it sets the SQL_DESC_NAME field. If the SQL_DESC_NAME field contains a column alias or if the column alias does not apply, the driver sets the SQL_DESC_UNNAMED field to SQL_NAMED. If an application sets the SQL_DESC_NAME field of an IPD to a parameter name or alias, the driver sets the SQL_DESC_UNNAMED field of the IPD to SQL_NAMED. If there is no column name or a column alias, the driver sets the SQL_DESC_UNNAMED field to SQL_UNNAMED. </para>
          <para>An application can set the SQL_DESC_UNNAMED field of an IPD to SQL_UNNAMED. A driver returns SQLSTATE HY091 (Invalid descriptor field identifier) if an application attempts to set the SQL_DESC_UNNAMED field of an IPD to SQL_NAMED. The SQL_DESC_UNNAMED field of an IRD is read-only; SQLSTATE HY091 (Invalid descriptor field identifier) will be returned if an application attempts to set it. </para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_UNSIGNED [Implementation descriptors]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLSMALLINT record field is set to SQL_TRUE if the column type is unsigned or non-numeric, or SQL_FALSE if the column type is signed.</para>
        </definition>
        <definedTerm> <legacyBold>SQL_DESC_UPDATABLE [IRDs]</legacyBold> </definedTerm>
        <definition>
          <para>This read-only SQLSMALLINT record field is set to one of the following values:</para>
          <list class="bullet">
            <listItem>
              <para>SQL_ATTR_READ_ONLY if the result set column is read-only.</para>
            </listItem>
            <listItem>
              <para>SQL_ATTR_WRITE if the result set column is read-write.</para>
            </listItem>
            <listItem>
              <para>SQL_ATTR_READWRITE_UNKNOWN if it is not known whether the result set column is updatable or not.</para>
            </listItem>
          </list>
          <para>SQL_DESC_UPDATABLE describes the updatability of the column in the result set, not the column in the base table. The updatability of the column in the base table on which this result set column is based may be different than the value in this field. Whether a column is updatable can be based on the data type, user privileges, and the definition of the result set itself. If it is unclear whether a column is updatable, SQL_ATTR_READWRITE_UNKNOWN should be returned. </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Consistency Checks</title>
    <content>
      <para>A consistency check is performed by the driver automatically whenever an application passes in a value for the SQL_DESC_DATA_PTR field of the ARD, APD, or IPD. If any of the fields is inconsistent with other fields, <legacyBold>SQLSetDescField</legacyBold> will return SQLSTATE HY021 (Inconsistent descriptor information). For more information, see "Consistency Check" in <legacyLink xlink:href="bf55256c-7eb7-4e3f-97ef-b0fee09ba829">SQLSetDescRec</legacyLink>.</para>
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
              <para>Binding a column</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Binding a parameter</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Getting a descriptor field</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="f09ff660-1e4a-4370-be85-90d4da0487d3">SQLGetDescField Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Getting multiple descriptor fields</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="325e0907-8e87-44e8-a111-f39e636a9cbc">SQLGetDescRec Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting multiple descriptor fields</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="bf55256c-7eb7-4e3f-97ef-b0fee09ba829">SQLSetDescRec Function</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>