---
title: SQLGetDiagField Function
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
  - SQLGetDiagField
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 1dbc4398-97a8-4585-bb77-1f7ea75e24c4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetDiagField Function
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
          <legacyBold>SQLGetDiagField</legacyBold> returns the current value of a field of a record of the diagnostic data structure (associated with a specified handle) that contains error, warning, and status information.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetDiagField</legacyBold>(
     SQLSMALLINT     <parameterReference>HandleType</parameterReference>,
     SQLHANDLE       <parameterReference>Handle</parameterReference>,
     SQLSMALLINT     <parameterReference>RecNumber</parameterReference>,
     SQLSMALLINT     <parameterReference>DiagIdentifier</parameterReference>,
     SQLPOINTER      <parameterReference>DiagInfoPtr</parameterReference>,
     SQLSMALLINT     <parameterReference>BufferLength</parameterReference>,
     SQLSMALLINT *   <parameterReference>StringLengthPtr</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>HandleType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A handle type identifier that describes the type of handle for which diagnostics are required. Must be one of the following:</para>
          <list class="bullet">
            <listItem>
              <para>SQL_HANDLE_DBC</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_DBC_INFO_TOKEN</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_DESC</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_ENV</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_STMT</para>
            </listItem>
          </list>
          <para>SQL_HANDLE_DBC_INFO_TOKEN handle is used only by the Driver Manager and driver. Applications should not use this handle type. For more information about SQL_HANDLE_DBC_INFO_TOKEN, see <link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Handle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A handle for the diagnostic data structure, of the type indicated by <legacyItalic>HandleType</legacyItalic>. If <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_ENV, <legacyItalic>Handle</legacyItalic> can be either a shared or an unshared environment handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>RecNumber</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Indicates the status record from which the application seeks information. Status records are numbered from 1. If the <legacyItalic>DiagIdentifier</legacyItalic> argument indicates any field of the diagnostics header, <legacyItalic>RecNumber</legacyItalic> is ignored. If not, it should be more than 0.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DiagIdentifier</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Indicates the field of the diagnostic whose value is to be returned. For more information, see the "<legacyItalic>DiagIdentifier</legacyItalic> Argument" section in "Comments."</para>
        </definition>
        <definedTerm>
          <legacyItalic>DiagInfoPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the diagnostic information. The data type depends on the value of <legacyItalic>DiagIdentifier</legacyItalic>. If <legacyItalic>DiagInfoPtr</legacyItalic> is an integer type, applications should use a buffer of SQLULEN and initialize the value to 0 before calling this function, as some drivers may only write the lower 32-bit or 16-bit of a buffer and leave the higher-order bit unchanged.</para>
          <para>If <legacyItalic>DiagInfoPtr</legacyItalic> is NULL, <legacyItalic>StringLengthPtr</legacyItalic> will still return the total number of bytes (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>DiagInfoPtr</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>DiagIdentifier</legacyItalic> is an ODBC-defined diagnostic and<legacyItalic> DiagInfoPtr</legacyItalic> points to a character string or a binary buffer, this argument should be the length of *<legacyItalic>DiagInfoPtr</legacyItalic>. If <legacyItalic>DiagIdentifier</legacyItalic> is an ODBC-defined field and *<legacyItalic>DiagInfoPtr</legacyItalic> is an integer, <legacyItalic>BufferLength</legacyItalic> is ignored. If the value in <legacyItalic>*DiagInfoPtr</legacyItalic> is a Unicode string (when calling <legacyBold>SQLGetDiagFieldW</legacyBold>), the <legacyItalic>BufferLength</legacyItalic> argument must be an even number. </para>
          <para>If <legacyItalic>DiagIdentifier</legacyItalic> is a driver-defined field, the application indicates the nature of the field to the Driver Manager by setting the <legacyItalic>BufferLength</legacyItalic> argument. <legacyItalic>BufferLength</legacyItalic> can have the following values: </para>
        </definition>
      </definitionTable>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>DiagInfoPtr</legacyItalic> is a pointer to a character string, <legacyItalic>BufferLength</legacyItalic> is the length of the string or SQL_NTS.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>DiagInfoPtr</legacyItalic> is a pointer to a binary buffer, the application places the result of the SQL_LEN_BINARY_ATTR(<legacyItalic>length</legacyItalic>) macro in <legacyItalic>BufferLength</legacyItalic>. This places a negative value in <legacyItalic>BufferLength</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>DiagInfoPtr</legacyItalic> is a pointer to a value other than a character string or binary string, <legacyItalic>BufferLength</legacyItalic> should have the value SQL_IS_POINTER. </para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>*DiagInfoPtr</legacyItalic> contains a fixed-length data type, <legacyItalic>BufferLength</legacyItalic> is SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT, or SQL_IS_USMALLINT, as appropriate.</para>
        </listItem>
      </list>
      <definitionTable>
        <definedTerm>
          <legacyItalic>StringLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of bytes (excluding the number of bytes required for the null-termination character) available to return in *<legacyItalic>DiagInfoPtr</legacyItalic>, for character data. If the number of bytes available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the text in *<legacyItalic>DiagInfoPtr</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_NO_DATA.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>
        <legacyBold>SQLGetDiagField</legacyBold> does not post diagnostic records for itself. It uses the following return values to report the outcome of its own execution:  </para>
      <list class="bullet">
        <listItem>
          <para>SQL_SUCCESS: The function successfully returned diagnostic information.</para>
        </listItem>
        <listItem>
          <para>SQL_SUCCESS_WITH_INFO: *<legacyItalic>DiagInfoPtr</legacyItalic> was too small to hold the requested diagnostic field. Therefore, the data in the diagnostic field was truncated. To determine that a truncation occurred, the application must compare <legacyItalic>BufferLength</legacyItalic> to the actual number of bytes available, which is written to *<legacyItalic>StringLengthPtr</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>SQL_INVALID_HANDLE: The handle indicated by <legacyItalic>HandleType</legacyItalic> and <legacyItalic>Handle</legacyItalic> was not a valid handle.</para>
        </listItem>
        <listItem>
          <para>SQL_ERROR: One of the following occurred: </para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyItalic>The DiagIdentifier</legacyItalic> argument was not one of the valid values.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>The DiagIdentifier</legacyItalic> argument was SQL_DIAG_CURSOR_ROW_COUNT, SQL_DIAG_DYNAMIC_FUNCTION, SQL_DIAG_DYNAMIC_FUNCTION_CODE, or SQL_DIAG_ROW_COUNT, but <legacyItalic>Handle</legacyItalic> was not a statement handle. (The Driver Manager returns this diagnostic.)</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>The RecNumber</legacyItalic> argument was negative or 0 when <legacyItalic>DiagIdentifier</legacyItalic> indicated a field from a diagnostic record. <legacyItalic>RecNumber</legacyItalic> is ignored for header fields.</para>
            </listItem>
            <listItem>
              <para>The value requested was a character string and <legacyItalic>BufferLength</legacyItalic> was less than zero.</para>
            </listItem>
            <listItem>
              <para>When using asynchronous notification, the asynchronous operation on the handle was not complete.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>SQL_NO_DATA: <legacyItalic>RecNumber</legacyItalic> was greater than the number of diagnostic records that existed for the handle specified in <legacyItalic>Handle.</legacyItalic> The function also returns SQL_NO_DATA for any positive <legacyItalic>RecNumber</legacyItalic> if there are no diagnostic records for <legacyItalic>Handle</legacyItalic>.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>An application typically calls <legacyBold>SQLGetDiagField</legacyBold> to accomplish one of three goals:  </para>
      <list class="ordered">
        <listItem>
          <para>To obtain specific error or warning information when a function call has returned SQL_ERROR or SQL_SUCCESS_WITH_INFO (or SQL_NEED_DATA for the <legacyBold>SQLBrowseConnect</legacyBold> function).</para>
        </listItem>
        <listItem>
          <para>To determine the number of rows in the data source that were affected when insert, delete, or update operations were performed with a call to <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> (from the SQL_DIAG_ROW_COUNT header field), or to determine the number of rows that exist in the current open cursor, if the driver can provide this information (from the SQL_DIAG_CURSOR_ROW_COUNT header field).</para>
        </listItem>
        <listItem>
          <para>To determine which function was executed by a call to <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold> (from the SQL_DIAG_DYNAMIC_FUNCTION and SQL_DIAG_DYNAMIC_FUNCTION_CODE header fields).</para>
        </listItem>
      </list>
      <para>Any ODBC function can post zero or more diagnostic records every time that it is called, so an application can call <legacyBold>SQLGetDiagField</legacyBold> after any ODBC function call. There is no limit to the number of diagnostic records that can be stored at any one time. <legacyBold>SQLGetDiagField</legacyBold> retrieves only the diagnostic information most recently associated with the diagnostic data structure specified in the <legacyItalic>Handle</legacyItalic> argument. If the application calls an ODBC function other than <legacyBold>SQLGetDiagField</legacyBold> or <legacyBold>SQLGetDiagRec</legacyBold>, any diagnostic information from a previous call with the same handle is lost. </para>
      <para>An application can scan all diagnostic records by incrementing <legacyItalic>RecNumber</legacyItalic>, as long as <legacyBold>SQLGetDiagField</legacyBold> returns SQL_SUCCESS. The number of status records is indicated in the SQL_DIAG_NUMBER header field. Calls to <legacyBold>SQLGetDiagField</legacyBold> are nondestructive to the header and record fields. The application can call <legacyBold>SQLGetDiagField</legacyBold> again later to retrieve a field from a record, as long as a function other than the diagnostic functions has not been called in the interim, which would post records on the same handle.</para>
      <para>An application can call <legacyBold>SQLGetDiagField</legacyBold> to return any diagnostic field at any time, except for SQL_DIAG_CURSOR_ROW_COUNT or SQL_DIAG_ROW_COUNT, which will return SQL_ERROR if <legacyItalic>Handle</legacyItalic> is not a statement handle. If any other diagnostic field is undefined, the call to <legacyBold>SQLGetDiagField</legacyBold> will return SQL_SUCCESS (provided no other diagnostic is encountered) and an undefined value is returned for the field.</para>
      <para>For more information, see <legacyLink xlink:href="4f486bb1-fad8-4064-ac9d-61f2de85b68b">Using SQLGetDiagRec and SQLGetDiagField</legacyLink> and <legacyLink xlink:href="11ba1857-b533-4517-8131-a2a8a0154a0a">Implementing SQLGetDiagRec and SQLGetDiagField</legacyLink>.</para>
      <para>Calling an API other than the one that’s being executed asynchronously will generate HY010 "Function sequence error". However, the error record cannot be retrieved before the asynchronous operation completes.</para>
    </content>
  </section>
  <section>
    <title>HandleType Argument</title>
    <content>
      <para>Each handle type can have diagnostic information associated with it. The <legacyItalic>HandleType</legacyItalic> argument indicates the handle type of <legacyItalic>Handle</legacyItalic>. </para>
      <para>Some header and record fields cannot be returned for environment, connection, statement, and descriptor handles. Those handles for which a field is not applicable are indicated in the "Header Fields" and "Record Fields" sections following. </para>
      <para>If <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_ENV, <legacyItalic>Handle</legacyItalic> can be either a shared or unshared environment handle.</para>
      <para>No driver-specific header diagnostic fields should be associated with an environment handle. </para>
      <para>The only diagnostic header fields that are defined for a descriptor handle are SQL_DIAG_NUMBER and SQL_DIAG_RETURNCODE.</para>
    </content>
  </section>
  <section>
    <title>DiagIdentifier Argument</title>
    <content>
      <para>This argument indicates the identifier of the field required from the diagnostic data structure. If <legacyItalic>RecNumber</legacyItalic> is greater than or equal to 1, the data in the field describes the diagnostic information returned by a function. If <legacyItalic>RecNumber</legacyItalic> is 0, the field is in the header of the diagnostic data structure and therefore contains data pertaining to the function call that returned the diagnostic information, not to the specific information. </para>
      <para>Drivers can define driver-specific header and record fields in the diagnostic data structure.</para>
      <para>An ODBC 3<legacyItalic>.x</legacyItalic> application working with an ODBC 2<legacyItalic>.x</legacyItalic> driver will be able to call <legacyBold>SQLGetDiagField</legacyBold> only with a <legacyItalic>DiagIdentifier</legacyItalic> argument of SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_NUMBER, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME, or SQL_DIAG_SQLSTATE. All other diagnostic fields will return SQL_ERROR.</para>
    </content>
  </section>
  <section>
    <title>Header Fields</title>
    <content>
      <para>The header fields listed in the following table can be included in the <legacyItalic>DiagIdentifier</legacyItalic> argument. </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>DiagIdentifier</para>
            </TD>
            <TD>
              <para>Return type</para>
            </TD>
            <TD>
              <para>Returns</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_DIAG_CURSOR_ROW_COUNT</para>
            </TD>
            <TD>
              <para>SQLLEN</para>
            </TD>
            <TD>
              <para>This field contains the count of rows in the cursor. Its semantics depend on the <legacyBold>SQLGetInfo</legacyBold> information types SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2, and SQL_STATIC_CURSOR_ATTRIBUTES2, which indicate which row counts are available for each cursor type (in the SQL_CA2_CRC_EXACT and SQL_CA2_CRC_APPROXIMATE bits). </para>
              <para>The contents of this field are defined only for statement handles and only after <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or <legacyBold>SQLMoreResults</legacyBold> has been called. Calling <legacyBold>SQLGetDiagField</legacyBold> with a <legacyItalic>DiagIdentifier</legacyItalic> of SQL_DIAG_CURSOR_ROW_COUNT on other than a statement handle will return SQL_ERROR.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_DYNAMIC_FUNCTION</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>This is a string that describes the SQL statement that the underlying function executed. (See "Values of the Dynamic Function fields," later in this section, for specific values.) The contents of this field are defined only for statement handles and only after a call to <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or <legacyBold>SQLMoreResults</legacyBold>. Calling <legacyBold>SQLGetDiagField</legacyBold> with a <legacyItalic>DiagIdentifier</legacyItalic> of SQL_DIAG_DYNAMIC_FUNCTION on other than a statement handle will return SQL_ERROR. The value of this field is undefined before a call to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_DYNAMIC_FUNCTION_CODE</para>
            </TD>
            <TD>
              <para>SQLINTEGER</para>
            </TD>
            <TD>
              <para>This is a numeric code that describes the SQL statement that was executed by the underlying function. (See "Values of the Dynamic Function Fields," later in this section, for specific value.) The contents of this field are defined only for statement handles and only after a call to <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or <legacyBold>SQLMoreResults</legacyBold>. Calling <legacyBold>SQLGetDiagField</legacyBold> with a <legacyItalic>DiagIdentifier</legacyItalic> of SQL_DIAG_DYNAMIC_FUNCTION_CODE on other than a statement handle will return SQL_ERROR. The value of this field is undefined before a call to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_NUMBER</para>
            </TD>
            <TD>
              <para>SQLINTEGER</para>
            </TD>
            <TD>
              <para>The number of status records that are available for the specified handle.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_RETURNCODE</para>
            </TD>
            <TD>
              <para>SQLRETURN</para>
            </TD>
            <TD>
              <para>Return code returned by the function. For a list of return codes, see <legacyLink xlink:href="e893b719-4392-476f-911a-5ed6da6f7e94">Return Codes</legacyLink>. The driver does not have to implement SQL_DIAG_RETURNCODE; it is always implemented by the Driver Manager. If no function has yet been called on the <legacyItalic>Handle</legacyItalic>, SQL_SUCCESS will be returned for SQL_DIAG_RETURNCODE.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_ROW_COUNT</para>
            </TD>
            <TD>
              <para>SQLLEN</para>
            </TD>
            <TD>
              <para>The number of rows affected by an insert, delete, or update performed by <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold>. It is driver-defined after a <legacyItalic>cursor specification</legacyItalic> has been executed. The contents of this field are defined only for statement handles. Calling <legacyBold>SQLGetDiagField</legacyBold> with a <legacyItalic>DiagIdentifier</legacyItalic> of SQL_DIAG_ROW_COUNT on other than a statement handle will return SQL_ERROR. The data in this field is also returned in the <legacyItalic>RowCountPtr</legacyItalic> argument of <legacyBold>SQLRowCount</legacyBold>. The data in this field is reset after every nondiagnostic function call, whereas the row count returned by <legacyBold>SQLRowCount</legacyBold> remains the same until the statement is set back to the prepared or allocated state.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Record Fields</title>
    <content>
      <para>The record fields listed in the following table can be included in the <legacyItalic>DiagIdentifier</legacyItalic> argument.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>DiagIdentifier</para>
            </TD>
            <TD>
              <para>Return type</para>
            </TD>
            <TD>
              <para>Returns</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_DIAG_CLASS_ORIGIN</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>A string that indicates the document that defines the class portion of the SQLSTATE value in this record. Its value is "ISO 9075" for all SQLSTATEs defined by Open Group and ISO call-level interface. For ODBC-specific SQLSTATEs (all those whose SQLSTATE class is "IM"), its value is "ODBC 3.0".</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_COLUMN_NUMBER</para>
            </TD>
            <TD>
              <para>SQLINTEGER</para>
            </TD>
            <TD>
              <para>If the SQL_DIAG_ROW_NUMBER field is a valid row number in a rowset or a set of parameters, this field contains the value that represents the column number in the result set or the parameter number in the set of parameters. Result set column numbers always start at 1; if this status record pertains to a bookmark column, the field can be zero. Parameter numbers start at 1. It has the value SQL_NO_COLUMN_NUMBER if the status record is not associated with a column number or parameter number. If the driver cannot determine the column number or parameter number that this record is associated with, this field has the value SQL_COLUMN_NUMBER_UNKNOWN. </para>
              <para>The contents of this field are defined only for statement handles.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_CONNECTION_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>A string that indicates the name of the connection that the diagnostic record relates to. This field is driver-defined. For diagnostic data structures associated with the environment handle and for diagnostics that do not relate to any connection, this field is a zero-length string.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_MESSAGE_TEXT</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>An informational message on the error or warning. This field is formatted as described in <legacyLink xlink:href="98027871-9901-476e-a722-ee58b7723c1f">Diagnostic Messages</legacyLink>. There is no maximum length to the diagnostic message text.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_NATIVE</para>
            </TD>
            <TD>
              <para>SQLINTEGER</para>
            </TD>
            <TD>
              <para>A driver/data source–specific native error code. If there is no native error code, the driver returns 0.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_ROW_NUMBER</para>
            </TD>
            <TD>
              <para>SQLLEN</para>
            </TD>
            <TD>
              <para>This field contains the row number in the rowset, or the parameter number in the set of parameters, with which the status record is associated. Row numbers and parameter numbers start with 1. This field has the value SQL_NO_ROW_NUMBER if this status record is not associated with a row number or parameter number. If the driver cannot determine the row number or parameter number that this record is associated with, this field has the value SQL_ROW_NUMBER_UNKNOWN. </para>
              <para>The contents of this field are defined only for statement handles.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_SERVER_NAME</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>A string that indicates the server name that the diagnostic record relates to. It is the same as the value returned for a call to <legacyBold>SQLGetInfo</legacyBold> with the SQL_DATA_SOURCE_NAME option. For diagnostic data structures associated with the environment handle and for diagnostics that do not relate to any server, this field is a zero-length string.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_SQLSTATE</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>A five-character SQLSTATE diagnostic code. For more information, see <legacyLink xlink:href="f29fff2e-3d09-4a8c-a2f9-2059062cbebf">SQLSTATEs</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DIAG_SUBCLASS_ORIGIN</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>A string with the same format and valid values as SQL_DIAG_CLASS_ORIGIN, that identifies the defining portion of the subclass portion of the SQLSTATE code. The ODBC-specific SQLSTATES for which "ODBC 3.0" is returned include the following:</para>
              <para>01S00, 01S01, 01S02, 01S06, 01S07, 07S01, 08S01, 21S01, 21S02, 25S01, 25S02, 25S03, 42S01, 42S02, 42S11, 42S12, 42S21, 42S22, HY095, HY097, HY098, HY099, HY100, HY101, HY105, HY107, HY109, HY110, HY111, HYT00, HYT01, IM001, IM002, IM003, IM004, IM005, IM006, IM007, IM008, IM010, IM011, IM012.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Values of the Dynamic Function Fields</title>
    <content>
      <para>The following table describes the values of SQL_DIAG_DYNAMIC_FUNCTION and SQL_DIAG_DYNAMIC_FUNCTION_CODE that apply to each type of SQL statement executed by a call to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>. The driver can add driver-defined values to those listed.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQL statement</para>
              <para>executed</para>
            </TD>
            <TD>
              <para>Value of</para>
              <para>SQL_DIAG_DYNAMIC_FUNCTION</para>
            </TD>
            <TD>
              <para>Value of</para>
              <para>SQL_DIAG_DYNAMIC_FUNCTION_CODE</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>alter-domain-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"ALTER DOMAIN"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_ALTER_DOMAIN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>alter-table-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"ALTER TABLE"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_ALTER_TABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>assertion-definition</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CREATE ASSERTION"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_CREATE_ASSERTION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>character-set-definition</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CREATE CHARACTER SET"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_CREATE_CHARACTER_SET</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>collation-definition</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CREATE COLLATION"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_CREATE_COLLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>create-index-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CREATE INDEX"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_CREATE_INDEX</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>create-table-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CREATE TABLE"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_CREATE_TABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>create-view-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CREATE VIEW"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_CREATE_VIEW</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>cursor-specification</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"SELECT CURSOR"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_SELECT_CURSOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>delete-statement-positioned</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DYNAMIC DELETE CURSOR"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DYNAMIC_DELETE_CURSOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>delete-statement-searched</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DELETE WHERE"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DELETE_WHERE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>domain-definition</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CREATE DOMAIN"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_CREATE_DOMAIN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>drop-assertion-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DROP ASSERTION"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DROP_ASSERTION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>drop-character-set-stmt</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DROP CHARACTER SET"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DROP_CHARACTER_SET</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>drop-collation-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DROP COLLATION"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DROP_COLLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>drop-domain-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DROP DOMAIN"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DROP_DOMAIN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>drop-index-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DROP INDEX"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DROP_INDEX</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>drop-schema-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DROP SCHEMA"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DROP_SCHEMA</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>drop-table-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DROP TABLE"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DROP_TABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>drop-translation-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DROP TRANSLATION"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DROP_TRANSLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>drop-view-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DROP VIEW"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DROP_VIEW</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>grant-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"GRANT"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_GRANT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>insert-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"INSERT"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_INSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>ODBC-procedure-extension</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CALL"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_ CALL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>revoke-statement</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"REVOKE"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_REVOKE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>schema-definition</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CREATE SCHEMA"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_CREATE_SCHEMA</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>translation-definition</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"CREATE TRANSLATION"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_CREATE_TRANSLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>update-statement-positioned</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"DYNAMIC UPDATE CURSOR"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_DYNAMIC_UPDATE_CURSOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>update-statement-searched</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>"UPDATE WHERE"</para>
            </TD>
            <TD>
              <para>SQL_DIAG_UPDATE_WHERE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Unknown</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>empty string</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>SQL_DIAG_UNKNOWN_STATEMENT</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Sequence of Status Records</title>
    <content>
      <para>Status records are positioned in a sequence based on row number and the type of the diagnostic. The Driver Manager determines the final order in which to return status records that it generates. The driver determines the final order in which to return status records that it generates.</para>
      <para>If diagnostic records are posted by both the Driver Manager and the driver, the Driver Manager is responsible for ordering them.</para>
      <para>If there are two or more status records, the sequence of the records is determined first by row number. The following rules apply to determining the sequence of diagnostic records by row:  </para>
      <list class="bullet">
        <listItem>
          <para>Records that do not correspond to any row appear in front of records that correspond to a particular row, because SQL_NO_ROW_NUMBER is defined to be –1.</para>
        </listItem>
        <listItem>
          <para>Records for which the row number is unknown appear in front of all other records, because SQL_ROW_NUMBER_UNKNOWN is defined to be –2.</para>
        </listItem>
        <listItem>
          <para>For all records that pertain to specific rows, records are sorted by the value in the SQL_DIAG_ROW_NUMBER field. All errors and warnings of the first row affected are listed, and then all errors and warnings of the next row affected, and so on. </para>
        </listItem>
      </list>
      <alert class="note">
        <para>The ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager does not order status records in the diagnostic queue if SQLSTATE 01S01 (Error in row) is returned by an ODBC 2<legacyItalic>.x</legacyItalic> driver or if SQLSTATE 01S01 (Error in row) is returned by an ODBC 3<legacyItalic>.x</legacyItalic> driver when <legacyBold>SQLExtendedFetch</legacyBold> is called or <legacyBold>SQLSetPos</legacyBold> is called on a cursor that has been positioned with <legacyBold>SQLExtendedFetch</legacyBold>.</para>
      </alert>
      <para>Within each row, or for all those records that do not correspond to a row or for which the row number is unknown, or for all those records with a row number equal to SQL_NO_ROW_NUMBER, the first record listed is determined by using a set of sorting rules. After the first record, the order of the other records affecting a row is undefined. An application cannot assume that errors precede warnings after the first record. Applications should scan the complete diagnostic data structure to obtain complete information about an unsuccessful call to a function.</para>
      <para>The following rules are used to determine the first record within a row. The record with the highest rank is the first record. The source of a record (Driver Manager, driver, gateway, and so on) is not considered when ranking records.   </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>Errors</legacyBold> Status records that describe errors have the highest rank. The following rules are applied to sort errors: </para>
          <list class="bullet">
            <listItem>
              <para>Records that indicate a transaction failure or possible transaction failure outrank all other records. </para>
            </listItem>
            <listItem>
              <para>If two or more records describe the same error condition, then SQLSTATEs defined by the Open Group CLI specification (classes 03 through HZ) outrank ODBC- and driver-defined SQLSTATEs. </para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Implementation-defined No Data Values</legacyBold> Status records that describe driver-defined No Data values (class 02) have the second highest rank.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Warnings</legacyBold> Status records that describe warnings (class 01) have the lowest rank. If two or more records describe the same warning condition, then warning SQLSTATEs defined by the Open Group CLI specification outrank ODBC-defined and driver-defined SQLSTATEs.</para>
        </listItem>
      </list>
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
              <para>Obtaining multiple fields of a diagnostic data structure</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ebdbac93-3d68-438f-8416-ef1f08e04269">SQLGetDiagRec Function</legacyLink>
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