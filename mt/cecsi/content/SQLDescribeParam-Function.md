---
title: "SQLDescribeParam Function"
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
  - SQLDescribeParam
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
caps.latest.revision: 27
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLDescribeParam Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: ODBC </para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLDescribeParam</legacyBold> returns the description of a parameter marker associated with a prepared SQL statement. This information is also available in the fields of the IPD.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLDescribeParam</legacyBold>(
      SQLHSTMT        <parameterReference>StatementHandle</parameterReference>,
      SQLUSMALLINT    <parameterReference>ParameterNumber</parameterReference>,
      SQLSMALLINT *   <parameterReference>DataTypePtr</parameterReference>,
      SQLULEN *       <parameterReference>ParameterSizePtr</parameterReference>,
      SQLSMALLINT *   <parameterReference>DecimalDigitsPtr</parameterReference>,
      SQLSMALLINT *   <parameterReference>NullablePtr</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Argument</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>StatementHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Statement handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ParameterNumber</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Parameter marker number ordered sequentially in increasing parameter order, starting at 1.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DataTypePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the SQL data type of the parameter. This value is read from the SQL_DESC_CONCISE_TYPE record field of the IPD. This will be one of the values in the <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink> section of Appendix D: Data Types, or a driver-specific SQL data type.</para>
          <para>In ODBC 3.<legacyItalic>x</legacyItalic>, SQL_TYPE_DATE, SQL_TYPE_TIME, or SQL_TYPE_TIMESTAMP will be returned in <legacyItalic>*DataTypePtr</legacyItalic> for date, time, or timestamp data, respectively; in ODBC 2.<legacyItalic>x</legacyItalic>, SQL_DATE, SQL_TIME, or SQL_TIMESTAMP will be returned. The Driver Manager performs the required mappings when an ODBC 2.<legacyItalic>x</legacyItalic> application is working with an ODBC 3.<legacyItalic>x</legacyItalic> driver or when an ODBC 3.<legacyItalic>x</legacyItalic> application is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver.   </para>
          <para>When <legacyItalic>ColumnNumber</legacyItalic> is equal to 0 (for a bookmark column), SQL_BINARY is returned in <legacyItalic>*DataTypePtr</legacyItalic> for variable-length bookmarks. (SQL_INTEGER is returned if bookmarks are used by an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver or by an ODBC 2.<legacyItalic>x</legacyItalic> application working with an ODBC 3.<legacyItalic>x</legacyItalic> driver.)   </para>
          <para>For more information, see <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink> in Appendix D: Data Types. For information about driver-specific SQL data types, see the driver's documentation. </para>
        </definition>
        <definedTerm>
          <legacyItalic>ParameterSizePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the size, in characters, of the column or expression of the corresponding parameter marker as defined by the data source. For more information about column size, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DecimalDigitsPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the number of decimal digits of the column or expression of the corresponding parameter as defined by the data source. For more information about decimal digits, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NullablePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return a value that indicates whether the parameter allows NULL values. This value is read from the SQL_DESC_NULLABLE field of the IPD. One of the following:</para>
        </definition>
      </definitionTable>
      <list class="bullet">
        <listItem>
          <para>SQL_NO_NULLS: The parameter does not allow NULL values (this is the default value).</para>
        </listItem>
        <listItem>
          <para>SQL_NULLABLE: The parameter allows NULL values.</para>
        </listItem>
        <listItem>
          <para>SQL_NULLABLE_UNKNOWN: The driver cannot determine whether the parameter allows NULL values.</para>
        </listItem>
      </list>
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
      <para>When <legacyBold>SQLDescribeParam</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLDescribeParam</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>07009</para>
            </TD>
            <TD>
              <para>Invalid descriptor index</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the argument <legacyItalic>ParameterNumber</legacyItalic> is less than 1.</para>
              <para>The value specified for the argument <legacyItalic>ParameterNumber</legacyItalic> was greater than the number of parameters in the associated SQL statement.</para>
              <para>The parameter marker was part of a non-DML statement.</para>
              <para>The parameter marker was part of a <legacyBold>SELECT</legacyBold> list.</para>
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
              <para>21S01</para>
            </TD>
            <TD>
              <para>Insert value list does not match column list</para>
            </TD>
            <TD>
              <para>The number of parameters in the <legacyBold>INSERT</legacyBold> statement did not match the number of columns in the table named in the statement.</para>
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
              <para> (DM) The function was called before calling <legacyBold>SQLPrepare</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> for the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLDescribeParam</unmanagedCodeEntityReference> function was called.</para>
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
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>Parameter markers are numbered in increasing parameter order, starting with 1, in the order they appear in the SQL statement.</para>
      <para>
        <legacyBold>SQLDescribeParam</legacyBold> does not return the type (input, input/output, or output) of a parameter in an SQL statement. Except in calls to procedures, all parameters in SQL statements are input parameters. To determine the type of each parameter in a call to a procedure, an application calls <legacyBold>SQLProcedureColumns</legacyBold>.</para>
      <para>For more information, see <legacyLink xlink:href="118d0f47-2afd-4955-bb47-38b1e2c2f38f">Describing Parameters</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>The following example prompts the user for an SQL statement and then prepares that statement. Next, it calls <legacyBold>SQLNumParams</legacyBold> to determine whether the statement contains any parameters. If the statement contains parameters, it calls <legacyBold>SQLDescribeParam</legacyBold> to describe those parameters and <legacyBold>SQLBindParameter</legacyBold> to bind them. Finally, it prompts the user for the values of any parameters and then executes the statement.</para>
      <code>SQLCHAR       Statement[100];
SQLSMALLINT   NumParams, i, DataType, DecimalDigits, Nullable;
SQLUINTEGER   ParamSize;
SQLHSTMT      hstmt;

// Prompt the user for an SQL statement and prepare it.
GetSQLStatement(Statement);
SQLPrepare(hstmt, Statement, SQL_NTS);

// Check to see if there are any parameters. If so, process them.
SQLNumParams(hstmt, &amp;NumParams);
if (NumParams) {
   // Allocate memory for three arrays. The first holds pointers to buffers in which
   // each parameter value will be stored in character form. The second contains the
   // length of each buffer. The third contains the length/indicator value for each
   // parameter.
   SQLPOINTER * PtrArray = (SQLPOINTER *) malloc(NumParams * sizeof(SQLPOINTER));
   SQLINTEGER * BufferLenArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));
   SQLINTEGER * LenOrIndArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));

   for (i = 0; i &lt; NumParams; i++) {
   // Describe the parameter.
   SQLDescribeParam(hstmt, i + 1, &amp;DataType, &amp;ParamSize, &amp;DecimalDigits, &amp;Nullable);

   // Call a helper function to allocate a buffer in which to store the parameter
   // value in character form. The function determines the size of the buffer from
   // the SQL data type and parameter size returned by SQLDescribeParam and returns
   // a pointer to the buffer and the length of the buffer.
   AllocParamBuffer(DataType, ParamSize, &amp;PtrArray[i], &amp;BufferLenArray[i]);

   // Bind the memory to the parameter. Assume that we only have input parameters.
   SQLBindParameter(hstmt, i + 1, SQL_PARAM_INPUT, SQL_C_CHAR, DataType, ParamSize,
         DecimalDigits, PtrArray[i], BufferLenArray[i],
         &amp;LenOrIndArray[i]);

   // Prompt the user for the value of the parameter and store it in the memory
   // allocated earlier. For simplicity, this function does not check the value
   // against the information returned by SQLDescribeParam. Instead, the driver does
   // this when the statement is executed.
   GetParamValue(PtrArray[i], BufferLenArray[i], &amp;LenOrIndArray[i]);
   }
}

// Execute the statement.
SQLExecute(hstmt);

// Process the statement further, such as retrieving results (if any) and closing the
// cursor (if any). Code not shown.

// Free the memory allocated for each parameter and the memory allocated for the arrays
// of pointers, buffer lengths, and length/indicator values.
for (i = 0; i &lt; NumParams; i++) free(PtrArray[i]);
free(PtrArray);
free(BufferLenArray);
free(LenOrIndArray);</code>
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
              <para>Binding a buffer to a parameter</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter Function</legacyLink>
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
              <para>Executing a prepared SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preparing a statement for execution</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare Function</legacyLink>
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