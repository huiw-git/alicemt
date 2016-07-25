---
title: "SQLBindParameter Function"
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
  - SQLBindParameter
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 38349d4b-be03-46f9-9d6a-e50dd144e225
caps.latest.revision: 51
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLBindParameter Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 2.0 Standards Compliance: ODBC  </para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLBindParameter</legacyBold> binds a buffer to a parameter marker in an SQL statement. <legacyBold>SQLBindParameter</legacyBold> supports binding to a Unicode C data type, even if the underlying driver does not support Unicode data.</para>
        <alert class="note">
          <para>This function replaces the ODBC 1.0 function <legacyBold>SQLSetParam</legacyBold>. For more information, see "Comments."</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLBindParameter</legacyBold>(
      SQLHSTMT        <parameterReference>StatementHandle</parameterReference>,
      SQLUSMALLINT    <parameterReference>ParameterNumber</parameterReference>,
      SQLSMALLINT     <parameterReference>InputOutputType</parameterReference>,
      SQLSMALLINT     <parameterReference>ValueType</parameterReference>,
      SQLSMALLINT     <parameterReference>ParameterType</parameterReference>,
      SQLULEN         <parameterReference>ColumnSize</parameterReference>,
      SQLSMALLINT     <parameterReference>DecimalDigits</parameterReference>,
      SQLPOINTER      <parameterReference>ParameterValuePtr</parameterReference>,
      SQLLEN          <parameterReference>BufferLength</parameterReference>,
      SQLLEN *        <parameterReference>StrLen_or_IndPtr</parameterReference>);</legacySyntax>
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
          <legacyItalic>ParameterNumber</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Parameter number, ordered sequentially in increasing parameter order, starting at 1.</para>
        </definition>
        <definedTerm>
          <legacyItalic>InputOutputType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The type of the parameter. For more information, see "<legacyItalic>InputOutputType</legacyItalic> Argument" in "Comments."</para>
        </definition>
        <definedTerm>
          <legacyItalic>ValueType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The C data type of the parameter. For more information, see "<legacyItalic>ValueType</legacyItalic> Argument" in "Comments."</para>
        </definition>
        <definedTerm>
          <legacyItalic>ParameterType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The SQL data type of the parameter. For more information, see "<legacyItalic>ParameterType</legacyItalic> Argument" in "Comments."</para>
        </definition>
        <definedTerm>
          <legacyItalic>ColumnSize</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The size of the column or expression of the corresponding parameter marker. For more information, see "<legacyItalic>ColumnSize</legacyItalic> Argument" in "Comments."</para>
          <para>If your application will run on a 64-bit Windows operating system, see <link xlink:href="ed9851ce-44ee-4c8e-b626-1d0b52da30fe">ODBC 64-Bit Information</link>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DecimalDigits</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The decimal digits of the column or expression of the corresponding parameter marker. For more information about column size, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ParameterValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Deferred Input] A pointer to a buffer for the parameter's data. For more information, see "<legacyItalic>ParameterValuePtr</legacyItalic> Argument" in "Comments."</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input/Output] Length of the <legacyItalic>ParameterValuePtr</legacyItalic> buffer in bytes. For more information, see "<legacyItalic>BufferLength</legacyItalic> Argument" in "Comments."</para>
          <para>See <link xlink:href="ed9851ce-44ee-4c8e-b626-1d0b52da30fe">ODBC 64-Bit Information</link>, if your application will run on a 64-bit operating system.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StrLen_or_IndPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Deferred Input] A pointer to a buffer for the parameter's length. For more information, see "<legacyItalic>StrLen_or_IndPtr</legacyItalic> Argument" in "Comments."</para>
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
      <para>When <legacyBold>SQLBindParameter</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLBindParameter</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The data type identified by the <legacyItalic>ValueType</legacyItalic> argument cannot be converted to the data type identified by the <legacyItalic>ParameterType</legacyItalic> argument. Notice that this error may be returned by <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or <legacyBold>SQLPutData</legacyBold> at execution time, instead of by <legacyBold>SQLBindParameter</legacyBold>.</para>
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
              <para>(DM) The value specified for the argument <legacyItalic>ParameterNumber</legacyItalic> was less than 1.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the *<legacyItalic>MessageText</legacyItalic> buffer describes the error and its cause. </para>
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
              <para>The value specified by the argument <legacyItalic>ValueType</legacyItalic> was not a valid C data type or SQL_C_DEFAULT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY004</para>
            </TD>
            <TD>
              <para>Invalid SQL data type</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>ParameterType</legacyItalic> was neither a valid ODBC SQL data type identifier nor a driver-specific SQL data type identifier supported by the driver.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY009</para>
            </TD>
            <TD>
              <para>Invalid argument value</para>
            </TD>
            <TD>
              <para>(DM) The argument <legacyItalic>ParameterValuePtr</legacyItalic> was a null pointer, the argument <legacyItalic>StrLen_or_IndPtr</legacyItalic> was a null pointer, and the argument <legacyItalic>InputOutputType</legacyItalic> was not SQL_PARAM_OUTPUT.</para>
              <para>(DM) SQL_PARAM_OUTPUT, where the argument <legacyItalic>ParameterValuePtr</legacyItalic> was a null pointer, the C type was char or binary, and the BufferLength (<legacyItalic>cbValueMax</legacyItalic>) was greater than 0.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence  error</para>
            </TD>
            <TD>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference> was called.</para>
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
              <para>HY021</para>
            </TD>
            <TD>
              <para>Inconsistent descriptor information</para>
            </TD>
            <TD>
              <para>The descriptor information checked during a consistency check was not consistent. (See the "Consistency Checks" section in <legacyBold>SQLSetDescField</legacyBold>.)</para>
              <para>The value specified for the argument <legacyItalic>DecimalDigits</legacyItalic> was outside the range of values supported by the data source for a column of the SQL data type specified by the <legacyItalic>ParameterType</legacyItalic> argument.</para>
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
              <para>(DM) The value in <legacyItalic>BufferLength</legacyItalic> was less than 0. (See the description of the SQL_DESC_DATA_PTR field in <legacyBold>SQLSetDescField</legacyBold>.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY104</para>
            </TD>
            <TD>
              <para>Invalid precision or scale value</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>ColumnSize</legacyItalic> or <legacyItalic>DecimalDigits</legacyItalic> was outside the range of values supported by the data source for a column of the SQL data type specified by the <legacyItalic>ParameterType</legacyItalic> argument.</para>
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
              <para>(DM) The value specified for the argument <legacyItalic>InputOutputType</legacyItalic> was invalid. (See "Comments.") </para>
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
              <para>The driver or data source does not support the conversion specified by the combination of the value specified for the argument <legacyItalic>ValueType</legacyItalic> and the driver-specific value specified for the argument <legacyItalic>ParameterType</legacyItalic>.</para>
              <para>The value specified for the argument <legacyItalic>ParameterType</legacyItalic> was a valid ODBC SQL data type identifier for the version of ODBC supported by the driver but was not supported by the driver or data source.</para>
              <para>The driver supports only ODBC 2.<legacyItalic>x</legacyItalic> and the argument <legacyItalic>ValueType</legacyItalic> was one of the following:</para>
              <para>SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT </para>
              <para>and all the interval C data types listed in <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink> in Appendix D: Data Types.</para>
              <para>The driver only supports ODBC versions prior to 3.50, and the argument <legacyItalic>ValueType</legacyItalic> was SQL_C_GUID.</para>
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
      <para>An application calls <legacyBold>SQLBindParameter</legacyBold> to bind each parameter marker in an SQL statement. Bindings remain in effect until the application calls <legacyBold>SQLBindParameter</legacyBold> again, calls <legacyBold>SQLFreeStmt</legacyBold> with the SQL_RESET_PARAMS option, or calls <legacyBold>SQLSetDescField</legacyBold> to set the SQL_DESC_COUNT header field of the APD to 0.</para>
      <para>For more information about parameters, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>. For more information about parameter data types and parameter markers, see <legacyLink xlink:href="fd7e99d8-d26a-408c-9733-6ffccde99f75">Parameter Data Types</legacyLink> and <legacyLink xlink:href="07213d04-cd31-45fd-a8c8-2e16e09eeaf4">Parameter Markers</legacyLink> in Appendix C: SQL Grammar.</para>
    </content>
  </section>
  <section>
    <title>ParameterNumber Argument</title>
    <content>
      <para>If <legacyItalic>ParameterNumber</legacyItalic> in the call to <legacyBold>SQLBindParameter</legacyBold> is greater than the value of SQL_DESC_COUNT, <legacyBold>SQLSetDescField</legacyBold> is called to increase the value of SQL_DESC_COUNT to <legacyItalic>ParameterNumber</legacyItalic>.</para>
    </content>
  </section>
  <section>
    <title>InputOutputType Argument</title>
    <content>
      <para>The <legacyItalic>InputOutputType</legacyItalic> argument specifies the type of the parameter. This argument sets the SQL_DESC_PARAMETER_TYPE field of the IPD. All parameters in SQL statements that do not call procedures, such as <legacyBold>INSERT</legacyBold> statements, are <legacyItalic>input</legacyItalic> <legacyItalic>parameters</legacyItalic>. Parameters in procedure calls can be input, input/output, or output parameters. (An application calls <legacyBold>SQLProcedureColumns</legacyBold> to determine the type of a parameter in a procedure call; parameters whose type cannot be determined are assumed to be input parameters.)</para>
      <para>The <legacyItalic>InputOutputType</legacyItalic> argument is one of the following values:  </para>
      <list class="bullet">
        <listItem>
          <para>SQL_PARAM_INPUT. The parameter marks a parameter in an SQL statement that does not call a procedure, such as an <legacyBold>INSERT</legacyBold> statement, or it marks an input parameter in a procedure. For example, the parameters in <legacyBold>INSERT INTO Employee VALUES (?, ?, ?)</legacyBold> are input parameters, whereas the parameters in <legacyBold>{call AddEmp(?, ?, ?)}</legacyBold> can be, but are not necessarily, input parameters. </para>
          <para>When the statement is executed, the driver sends data for the parameter to the data source; the *<legacyItalic>ParameterValuePtr</legacyItalic> buffer must contain a valid input value, or the *<legacyItalic>StrLen_or_IndPtr</legacyItalic> buffer must contain SQL_NULL_DATA, SQL_DATA_AT_EXEC, or the result of the SQL_LEN_DATA_AT_EXEC macro.  </para>
          <para>If an application cannot determine the type of a parameter in a procedure call, it sets <legacyItalic>InputOutputType</legacyItalic> to SQL_PARAM_INPUT; if the data source returns a value for the parameter, the driver discards it. </para>
        </listItem>
        <listItem>
          <para>SQL_PARAM_INPUT_OUTPUT. The parameter marks an input/output parameter in a procedure. For example, the parameter in <legacyBold>{call GetEmpDept(?)}</legacyBold> is an input/output parameter that accepts an employee's name and returns the name of the employee's department. </para>
          <para>When the statement is executed, the driver sends data for the parameter to the data source; the *<legacyItalic>ParameterValuePtr</legacyItalic> buffer must contain a valid input value, or the *<legacyItalic>StrLen_or_IndPtr</legacyItalic> buffer must contain SQL_NULL_DATA, SQL_DATA_AT_EXEC, or the result of the SQL_LEN_DATA_AT_EXEC macro. After the statement is executed, the driver returns data for the parameter to the application; if the data source does not return a value for an input/output parameter, the driver sets the *<legacyItalic>StrLen_or_IndPtr</legacyItalic> buffer to SQL_NULL_DATA.  </para>
          <alert class="note">
            <para>When an ODBC 1.0 application calls <legacyBold>SQLSetParam</legacyBold> in an ODBC 2.0 driver, the Driver Manager converts this to a call to <legacyBold>SQLBindParameter</legacyBold> in which the <legacyItalic>InputOutputType</legacyItalic> argument is set to SQL_PARAM_INPUT_OUTPUT.</para>
          </alert>
        </listItem>
        <listItem>
          <para>SQL_PARAM_OUTPUT. The parameter marks the return value of a procedure or an output parameter in a procedure; in either case, these are known as <legacyItalic>output parameters</legacyItalic>. For example, the parameter in <legacyBold>{?=call GetNextEmpID}</legacyBold> is an output parameter that returns the next employee ID. </para>
          <para>After the statement is executed, the driver returns data for the parameter to the application, unless the <legacyItalic>ParameterValuePtr</legacyItalic> and <legacyItalic>StrLen_or_IndPtr</legacyItalic> arguments are both null pointers, in which case the driver discards the output value. If the data source does not return a value for an output parameter, the driver sets the *<legacyItalic>StrLen_or_IndPtr</legacyItalic> buffer to SQL_NULL_DATA.</para>
        </listItem>
        <listItem>
          <para>SQL_PARAM_INPUT_OUTPUT_STREAM. Indicates that an input/output parameter should be streamed. <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> can read parameter values in parts. <legacyItalic>BufferLength</legacyItalic> is ignored because the buffer length will be determined at the call of <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference>. The value of the <parameterReference>StrLen_or_IndPtr</parameterReference> buffer must contain SQL_NULL_DATA, SQL_DEFAULT_PARAM, SQL_DATA_AT_EXEC, or the result of the SQL_LEN_DATA_AT_EXEC macro. A parameter must be bound as a data-at-execution (DAE) parameter at input if it will be streamed at output. <parameterReference>ParameterValuePtr</parameterReference> can be any non-null pointer value that will be returned by <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> as the user-defined token whose value was passed with <parameterReference>ParameterValuePtr</parameterReference> for both input and output. For more information, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.</para>
        </listItem>
        <listItem>
          <para>SQL_PARAM_OUTPUT_STREAM. Same as SQL_PARAM_INPUT_OUTPUT_STREAM, for an output parameter. *<parameterReference>StrLen_or_IndPtr</parameterReference> is ignored at input.</para>
        </listItem>
      </list>
      <para>The following table lists different combinations of <legacyItalic>InputOutputType</legacyItalic> and *<legacyItalic>StrLen_or_IndPtr</legacyItalic>:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>InputOutputType</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>*<legacyItalic>StrLen_or_IndPtr</legacyItalic></para>
            </TD>
            <TD>
              <para>Outcome</para>
            </TD>
            <TD>
              <para>Remark on ParameterValuePtr</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_PARAM_INPUT</para>
            </TD>
            <TD>
              <para>SQL_LEN_DATA_AT_EXEC(<parameterReference>len</parameterReference>) or SQL_DATA_AT_EXEC</para>
            </TD>
            <TD>
              <para>Input in parts</para>
            </TD>
            <TD>
              <para>
                <parameterReference>ParameterValuePtr</parameterReference> can be any pointer value that will be returned by <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> as the user-defined token whose value was passed with <legacyItalic>ParameterValuePtr</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_PARAM_INPUT</para>
            </TD>
            <TD>
              <para>Not SQL_LEN_DATA_AT_EXEC(<parameterReference>len</parameterReference>) or SQL_DATA_AT_EXEC</para>
            </TD>
            <TD>
              <para>Input bound buffer</para>
            </TD>
            <TD>
              <para>
                <parameterReference>ParameterValuePtr</parameterReference> is the address of the input buffer.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_PARAM_OUTPUT</para>
            </TD>
            <TD>
              <para>Ignored at input.</para>
            </TD>
            <TD>
              <para>Output bound buffer</para>
            </TD>
            <TD>
              <para>
                <parameterReference>ParameterValuePtr</parameterReference> is the address of the output buffer.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_PARAM_OUTPUT_STREAM</para>
            </TD>
            <TD>
              <para>Ignored at input.</para>
            </TD>
            <TD>
              <para>Streamed output</para>
            </TD>
            <TD>
              <para>
                <parameterReference>ParameterValuePtr</parameterReference> can be any pointer value, which will be returned by <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> as the user-defined token whose value was passed with <legacyItalic>ParameterValuePtr</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_PARAM_INPUT_OUTPUT</para>
            </TD>
            <TD>
              <para>SQL_LEN_DATA_AT_EXEC(<parameterReference>len</parameterReference>) or SQL_DATA_AT_EXEC</para>
            </TD>
            <TD>
              <para>Input in parts and output bound buffer</para>
            </TD>
            <TD>
              <para>
                <parameterReference>ParameterValuePtr</parameterReference> is the address of the output buffer, which will also be returned by <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> as the user-defined token whose value was passed with <legacyItalic>ParameterValuePtr</legacyItalic>. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_PARAM_INPUT_OUTPUT</para>
            </TD>
            <TD>
              <para>Not SQL_LEN_DATA_AT_EXEC(<parameterReference>len</parameterReference>) or SQL_DATA_AT_EXEC</para>
            </TD>
            <TD>
              <para>Input bound buffer and output bound buffer</para>
            </TD>
            <TD>
              <para>
                <parameterReference>ParameterValuePtr</parameterReference> is the address of the shared input/output buffer.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_PARAM_INPUT_OUTPUT_STREAM </para>
            </TD>
            <TD>
              <para>SQL_LEN_DATA_AT_EXEC(<parameterReference>len</parameterReference>) or SQL_DATA_AT_EXEC</para>
            </TD>
            <TD>
              <para>Input in parts and streamed output</para>
            </TD>
            <TD>
              <para>
                <parameterReference>ParameterValuePtr</parameterReference> can be any non-null pointer value, which will be returned by <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> as the user-defined token whose value was passed with <legacyItalic>ParameterValuePtr</legacyItalic> for both input and output.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para> The driver must decide which SQL types are allowed when an application binds an output or input-output parameter as streamed. The driver manager will not generate an error for an invalid SQL type.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>ValueType Argument</title>
    <content>
      <para>The <legacyItalic>ValueType</legacyItalic> argument specifies the C data type of the parameter. This argument sets the SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE, and SQL_DESC_DATETIME_INTERVAL_CODE fields of the APD. This must be one of the values in the <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink> section of Appendix D: Data Types.</para>
      <para>If the <legacyItalic>ValueType</legacyItalic> argument is one of the interval data types, the SQL_DESC_TYPE field of the <legacyItalic>ParameterNumber</legacyItalic> record of the APD is set to SQL_INTERVAL, the SQL_DESC_CONCISE_TYPE field of the APD is set to the concise interval data type, and the SQL_DESC_DATETIME_INTERVAL_CODE field of the <legacyItalic>ParameterNumber</legacyItalic> record is set to a subcode for the specific interval data type. (See <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>.) The default interval leading precision (2) and default interval seconds precision (6), as set in the SQL_DESC_DATETIME_INTERVAL_PRECISION and SQL_DESC_PRECISION fields of the APD, respectively, are used for the data. If either default precision is not appropriate, the application should explicitly set the descriptor field by a call to <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>.</para>
      <para>If the <legacyItalic>ValueType</legacyItalic> argument is one of the datetime data types, the SQL_DESC_TYPE field of the <legacyItalic>ParameterNumber</legacyItalic> record of the APD is set to SQL_DATETIME, the SQL_DESC_CONCISE_TYPE field of the <legacyItalic>ParameterNumber</legacyItalic> record of the APD is set to the concise datetime C data type, and the SQL_DESC_DATETIME_INTERVAL_CODE field of the <legacyItalic>ParameterNumber</legacyItalic> record is set to a subcode for the specific datetime data type. (See <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>.)</para>
      <para>If the <legacyItalic>ValueType</legacyItalic> argument is an SQL_C_NUMERIC data type, the default precision (which is driver-defined) and the default scale (0), as set in the SQL_DESC_PRECISION and SQL_DESC_SCALE fields of the APD, are used for the data. If the default precision or scale is not appropriate, the application should explicitly set the descriptor field by a call to <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>.</para>
      <para>SQL_C_DEFAULT specifies that the parameter value be transferred from the default C data type for the SQL data type specified with <legacyItalic>ParameterType</legacyItalic>.</para>
      <para>You can also specify an extended C data type. For more information, see <link xlink:href="c91bef31-3794-4736-966a-d50997b2233c">C Data Types in ODBC</link>.</para>
      <para>For more information, see <legacyLink xlink:href="229140ae-af8f-4ec8-9ccf-1e92360e0bac">Default C Data Types</legacyLink>, <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>, and <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink> in Appendix D: Data Types.</para>
    </content>
  </section>
  <section>
    <title>ParameterType Argument</title>
    <content>
      <para>This must be one of the values listed in the <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink> section of Appendix D: Data Types, or it must be a driver-specific value. This argument sets the SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE, and SQL_DESC_DATETIME_INTERVAL_CODE fields of the IPD. </para>
      <para>If the <legacyItalic>ParameterType</legacyItalic> argument is one of the datetime identifiers, the SQL_DESC_TYPE field of the IPD is set to SQL_DATETIME, the SQL_DESC_CONCISE_TYPE field of the IPD is set to the concise datetime SQL data type, and the SQL_DESC_DATETIME_INTERVAL_CODE field is set to the appropriate datetime subcode value.</para>
      <para>If <legacyItalic>ParameterType</legacyItalic> is one of the interval identifiers, the SQL_DESC_TYPE field of the IPD is set to SQL_INTERVAL, the SQL_DESC_CONCISE_TYPE field of the IPD is set to the concise SQL interval data type, and the SQL_DESC_DATETIME_INTERVAL_CODE field of the IPD is set to the appropriate interval subcode. The SQL_DESC_DATETIME_INTERVAL_PRECISION field of the IPD is set to the interval leading precision, and the SQL_DESC_PRECISION field is set to the interval seconds precision, if applicable. If the default value of SQL_DESC_DATETIME_INTERVAL_PRECISION or SQL_DESC_PRECISION is not appropriate, the application should explicitly set it by calling <legacyBold>SQLSetDescField</legacyBold>. For more information about any of these fields, see <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.</para>
      <para>If the <legacyItalic>ValueType</legacyItalic> argument is a SQL_NUMERIC data type, the default precision (which is driver-defined) and the default scale (0), as set in the SQL_DESC_PRECISION and SQL_DESC_SCALE fields of the IPD, are used for the data. If the default precision or scale is not appropriate, the application should explicitly set the descriptor field by a call to <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>.</para>
      <para>For information about how data is converted, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink> and <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink> in Appendix D: Data Types.</para>
    </content>
  </section>
  <section>
    <title>ColumnSize Argument</title>
    <content>
      <para>The <legacyItalic>ColumnSize </legacyItalic>argument specifies the size of the column or expression that corresponds to the parameter marker, the length of that data, or both. This argument sets different fields of the IPD, depending on the SQL data type (the <legacyItalic>ParameterType</legacyItalic> argument). The following rules apply to this mapping:  </para>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>ParameterType</legacyItalic> is SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY, or one of the concise SQL datetime or interval data types, the SQL_DESC_LENGTH field of the IPD is set to the value of <legacyItalic>ColumnSize</legacyItalic>. (For more information, see the <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> section in Appendix D: Data Types.)</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>ParameterType</legacyItalic> is SQL_DECIMAL, SQL_NUMERIC, SQL_FLOAT, SQL_REAL, or SQL_DOUBLE, the SQL_DESC_PRECISION field of the IPD is set to the value of <legacyItalic>ColumnSize</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>For other data types, the <legacyItalic>ColumnSize </legacyItalic>argument is ignored.</para>
        </listItem>
      </list>
      <para>For more information, see "Passing Parameter Values" and SQL_DATA_AT_EXEC in "<legacyItalic>StrLen_or_IndPtr</legacyItalic> Argument."</para>
    </content>
  </section>
  <section>
    <title>DecimalDigits Argument</title>
    <content>
      <para>If <legacyItalic>ParameterType</legacyItalic> is SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP, SQL_INTERVAL_SECOND, SQL_INTERVAL_DAY_TO_SECOND, SQL_INTERVAL_HOUR_TO_SECOND, or SQL_INTERVAL_MINUTE_TO_SECOND, the SQL_DESC_PRECISION field of the IPD is set to <legacyItalic>DecimalDigits</legacyItalic>. If <legacyItalic>ParameterType</legacyItalic> is SQL_NUMERIC or SQL_DECIMAL, the SQL_DESC_SCALE field of the IPD is set to <legacyItalic>DecimalDigits</legacyItalic>. For all other data types, the <legacyItalic>DecimalDigits</legacyItalic> argument is ignored.</para>
    </content>
  </section>
  <section>
    <title>ParameterValuePtr Argument</title>
    <content>
      <para>The <legacyItalic>ParameterValuePtr</legacyItalic> argument points to a buffer that, when <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> is called, contains the actual data for the parameter. The data must be in the form specified by the <legacyItalic>ValueType</legacyItalic> argument. This argument sets the SQL_DESC_DATA_PTR field of the APD. An application can set the <legacyItalic>ParameterValuePtr</legacyItalic> argument to a null pointer, as long as <legacyItalic>*StrLen_or_IndPtr</legacyItalic> is SQL_NULL_DATA or SQL_DATA_AT_EXEC. (This applies only to input or input/output parameters.)</para>
      <para>If *<legacyItalic>StrLen_or_IndPtr</legacyItalic> is the result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro or SQL_DATA_AT_EXEC, then <legacyItalic>ParameterValuePtr</legacyItalic> is an application-defined pointer value that is associated with the parameter. It is returned to the application through <legacyBold>SQLParamData</legacyBold>. For example, <legacyItalic>ParameterValuePtr</legacyItalic> might be a non-zero token such as a parameter number, a pointer to data, or a pointer to a structure that the application used to bind input parameters. However, note that if the parameter is an input/output parameter, <legacyItalic>ParameterValuePtr</legacyItalic> must be a pointer to a buffer where the output value will be stored. If the value in the SQL_ATTR_PARAMSET_SIZE statement attribute is greater than 1, the application can use the value pointed to by the SQL_ATTR_PARAMS_PROCESSED_PTR statement attribute together with the <legacyItalic>ParameterValuePtr</legacyItalic> argument. For example, <legacyItalic>ParameterValuePtr</legacyItalic> might point to an array of values and the application might use the value pointed to by SQL_ATTR_PARAMS_PROCESSED_PTR to retrieve the correct value from the array. For more information, see "Passing Parameter Values" later in this section.</para>
      <para>If the <legacyItalic>InputOutputType</legacyItalic> argument is SQL_PARAM_INPUT_OUTPUT or SQL_PARAM_OUTPUT, <legacyItalic>ParameterValuePtr</legacyItalic> points to a buffer in which the driver returns the output value. If the procedure returns one or more result sets, the *<legacyItalic>ParameterValuePtr</legacyItalic> buffer is not guaranteed to be set until all result sets/row counts have been processed. If the buffer is not set until processing is complete, the output parameters and return values are unavailable until <legacyBold>SQLMoreResults</legacyBold> returns SQL_NO_DATA. Calling <legacyBold>SQLCloseCursor</legacyBold> or <legacyBold>SQLFreeStmt</legacyBold> with an Option of SQL_CLOSE will cause these values to be discarded.</para>
      <para>If the value in the SQL_ATTR_PARAMSET_SIZE statement attribute is greater than 1, <legacyItalic>ParameterValuePtr</legacyItalic> points to an array. A single SQL statement processes the complete array of input values for an input or input/output parameter and returns an array of output values for an input/output or output parameter.</para>
    </content>
  </section>
  <section>
    <title>BufferLength Argument</title>
    <content>
      <para>For character and binary C data, the <legacyItalic>BufferLength</legacyItalic> argument specifies the length of the *<legacyItalic>ParameterValuePtr</legacyItalic> buffer (if it is a single element) or the length of an element in the *<legacyItalic>ParameterValuePtr</legacyItalic> array (if the value in the SQL_ATTR_PARAMSET_SIZE statement attribute is greater than 1). This argument sets the SQL_DESC_OCTET_LENGTH record field of the APD. If the application specifies multiple values, <legacyItalic>BufferLength</legacyItalic> is used to determine the location of values in the *<legacyItalic>ParameterValuePtr</legacyItalic> array, both on input and on output. For input/output and output parameters, it is used to determine whether to truncate character and binary C data on output:  </para>
      <list class="bullet">
        <listItem>
          <para>For character C data, if the number of bytes available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the data in *<legacyItalic>ParameterValuePtr</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> less the length of a null-termination character and is null-terminated by the driver.</para>
        </listItem>
        <listItem>
          <para>For binary C data, if the number of bytes available to return is greater than <legacyItalic>BufferLength</legacyItalic>, the data in *<legacyItalic>ParameterValuePtr</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> bytes.</para>
        </listItem>
      </list>
      <para>For all other types of C data, the <legacyItalic>BufferLength</legacyItalic> argument is ignored. The length of the *<legacyItalic>ParameterValuePtr</legacyItalic> buffer (if it is a single element) or the length of an element in the *<legacyItalic>ParameterValuePtr</legacyItalic> array (if the application calls <legacyBold>SQLSetStmtAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> argument of SQL_ATTR_PARAMSET_SIZE to specify multiple values for each parameter) is assumed to be the length of the C data type.</para>
      <para>For streamed output or streamed input/output parameters, the <parameterReference>BufferLength</parameterReference> argument is ignored because the buffer length is specified in <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference>.</para>
      <alert class="note">
        <para>When an ODBC 1.0 application calls <legacyBold>SQLSetParam</legacyBold> in an ODBC 3.<legacyItalic>x</legacyItalic> driver, the Driver Manager converts this to a call to <legacyBold>SQLBindParameter</legacyBold> in which the <legacyItalic>BufferLength</legacyItalic> argument is always SQL_SETPARAM_VALUE_MAX. Because the Driver Manager returns an error if an ODBC 3.<legacyItalic>x</legacyItalic> application sets <legacyItalic>BufferLength</legacyItalic> to SQL_SETPARAM_VALUE_MAX, an ODBC 3.<legacyItalic>x</legacyItalic> driver can use this to determine when it is called by an ODBC 1.0 application.</para>
      </alert>
      <alert class="note">
        <para>In <legacyBold>SQLSetParam</legacyBold>, the way in which an application specifies the length of the *<legacyItalic>ParameterValuePtr</legacyItalic> buffer so that the driver can return character or binary data, and the way in which an application sends an array of character or binary parameter values to the driver, are driver-defined.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>StrLen_or_IndPtr Argument</title>
    <content>
      <para>The <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument points to a buffer that, when <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> is called, contains one of the following. (This argument sets the SQL_DESC_OCTET_LENGTH_PTR and SQL_DESC_INDICATOR_PTR record fields of the application parameter pointers.)  </para>
      <list class="bullet">
        <listItem>
          <para>The length of the parameter value stored in *<legacyItalic>ParameterValuePtr</legacyItalic>. This is ignored except for character or binary C data.</para>
        </listItem>
        <listItem>
          <para>SQL_NTS. The parameter value is a null-terminated string.</para>
        </listItem>
        <listItem>
          <para>SQL_NULL_DATA. The parameter value is NULL.</para>
        </listItem>
        <listItem>
          <para>SQL_DEFAULT_PARAM. A procedure is to use the default value of a parameter, instead of a value retrieved from the application. This value is valid only in a procedure called in ODBC canonical syntax, and then only if the <legacyItalic>InputOutputType</legacyItalic> argument is SQL_PARAM_INPUT, SQL_PARAM_INPUT_OUTPUT, or SQL_PARAM_INPUT_OUTPUT_STREAM. When *<legacyItalic>StrLen_or_IndPtr</legacyItalic> is SQL_DEFAULT_PARAM, the <legacyItalic>ValueType</legacyItalic>, <legacyItalic>ParameterType</legacyItalic>, <legacyItalic>ColumnSize</legacyItalic>, <legacyItalic>DecimalDigits</legacyItalic>, <legacyItalic>BufferLength</legacyItalic>, and <legacyItalic>ParameterValuePtr</legacyItalic> arguments are ignored for input parameters and are used only to define the output parameter value for input/output parameters.</para>
        </listItem>
        <listItem>
          <para>The result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro. The data for the parameter will be sent with <legacyBold>SQLPutData</legacyBold>. If the <legacyItalic>ParameterType</legacyItalic> argument is SQL_LONGVARBINARY, SQL_LONGVARCHAR, or a long, data source–specific data type, and the driver returns "Y" for the SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold>, <legacyItalic>length</legacyItalic> is the number of bytes of data to be sent for the parameter; otherwise, <legacyItalic>length</legacyItalic> must be a nonnegative value and is ignored. For more information, see "Passing Parameter Values," later in this section. </para>
          <para>For example, to specify that 10,000 bytes of data will be sent with <legacyBold>SQLPutData</legacyBold> in one or more calls, for an SQL_LONGVARCHAR parameter, an application sets *<legacyItalic>StrLen_or_IndPtr</legacyItalic> to SQL_LEN_DATA_AT_EXEC(10000). </para>
        </listItem>
        <listItem>
          <para>SQL_DATA_AT_EXEC. The data for the parameter will be sent with <legacyBold>SQLPutData</legacyBold>. This value is used by ODBC 1.0 applications when they call ODBC 3.<legacyItalic>x</legacyItalic> drivers. For more information, see "Passing Parameter Values," later in this section.</para>
        </listItem>
      </list>
      <para>If <legacyItalic>StrLen_or_IndPtr</legacyItalic> is a null pointer, the driver assumes that all input parameter values are non-NULL and that character and binary data is null-terminated. If <legacyItalic>InputOutputType</legacyItalic> is SQL_PARAM_OUTPUT or SQL_PARAM_OUTPUT_STREAM and <legacyItalic>ParameterValuePtr</legacyItalic> and <legacyItalic>StrLen_or_IndPtr</legacyItalic> are both null pointers, the driver discards the output value.</para>
      <alert class="note">
        <para>Application developers are strongly discouraged from specifying a null pointer for <legacyItalic>StrLen_or_IndPtr</legacyItalic> when the data type of the parameter is SQL_C_BINARY. To make sure that a driver does not unexpectedly truncate SQL_C_BINARY data, <legacyItalic>StrLen_or_IndPtr</legacyItalic> should contain a pointer to a valid length value.</para>
      </alert>
      <para>If the <legacyItalic>InputOutputType</legacyItalic> argument is SQL_PARAM_INPUT_OUTPUT, SQL_PARAM_OUTPUT, SQL_PARAM_INPUT_OUTPUT_STREAM, or SQL_PARAM_OUTPUT_STREAM, <legacyItalic>StrLen_or_IndPtr</legacyItalic> points to a buffer in which the driver returns SQL_NULL_DATA, the number of bytes available to return in *<legacyItalic>ParameterValuePtr</legacyItalic> (excluding the null-termination byte of character data), or SQL_NO_TOTAL (if the number of bytes available to return cannot be determined). If the procedure returns one or more result sets, the *<legacyItalic>StrLen_or_IndPtr</legacyItalic> buffer is not guaranteed to be set until all results have been fetched.</para>
      <para>If the value in the SQL_ATTR_PARAMSET_SIZE statement attribute is greater than 1, <legacyItalic>StrLen_or_IndPtr</legacyItalic> points to an array of SQLLEN values. These can be any of the values listed earlier in this section and are processed with a single SQL statement.</para>
    </content>
  </section>
  <section>
    <title>Passing Parameter Values</title>
    <content>
      <para>An application can pass the value for a parameter either in the *<legacyItalic>ParameterValuePtr</legacyItalic> buffer or with one or more calls to <legacyBold>SQLPutData</legacyBold>. Parameters whose data is passed with <legacyBold>SQLPutData</legacyBold> are known as <legacyItalic>data-at-execution</legacyItalic> parameters. These are typically used to send data for SQL_LONGVARBINARY and SQL_LONGVARCHAR parameters, and can be mixed with other parameters.</para>
      <para>To pass parameter values, an application performs the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>Calls <legacyBold>SQLBindParameter</legacyBold> for each parameter to bind buffers for the parameter's value (<legacyItalic>ParameterValuePtr</legacyItalic> argument) and length/indicator (<legacyItalic>StrLen_or_IndPtr</legacyItalic> argument). For data-at-execution parameters, <legacyItalic>ParameterValuePtr</legacyItalic> is an application-defined pointer value such as a parameter number or a pointer to data. The value will be returned later and can be used to identify the parameter.</para>
        </listItem>
        <listItem>
          <para>Places values for input and input/output parameters in the *<legacyItalic>ParameterValuePtr</legacyItalic> and *<legacyItalic>StrLen_or_IndPtr</legacyItalic> buffers: </para>
          <list class="bullet">
            <listItem>
              <para>For normal parameters, the application places the parameter value in the *<legacyItalic>ParameterValuePtr</legacyItalic> buffer and the length of that value in the *<legacyItalic>StrLen_or_IndPtr</legacyItalic> buffer. For more information, see <legacyLink xlink:href="13e5da79-b60c-48d0-b467-773f481ef2a4">Setting Parameter Values</legacyLink>.</para>
            </listItem>
            <listItem>
              <para>For data-at-execution parameters, the application puts the result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro (when calling an ODBC 2.0 driver) in the *<legacyItalic>StrLen_or_IndPtr</legacyItalic> buffer.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> to execute the SQL statement. </para>
          <list class="bullet">
            <listItem>
              <para>If there are no data-at-execution parameters, the process is complete.</para>
            </listItem>
            <listItem>
              <para>If there are any data-at-execution parameters, the function returns SQL_NEED_DATA.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLParamData</legacyBold> to retrieve the application-defined value specified in the <legacyItalic>ParameterValuePtr</legacyItalic> argument of <legacyBold>SQLBindParameter</legacyBold> for the first data-at-execution parameter to be processed. <legacyBold>SQLParamData</legacyBold> returns SQL_NEED_DATA. </para>
          <alert class="note">
            <para>Although data-at-execution parameters resemble data-at-execution columns, the value returned by <legacyBold>SQLParamData</legacyBold> is different for each. Data-at-execution parameters are parameters in an SQL statement for which data will be sent with <legacyBold>SQLPutData</legacyBold> when the statement is executed with <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold>. They are bound with <legacyBold>SQLBindParameter</legacyBold>. The value returned by <legacyBold>SQLParamData</legacyBold> is a pointer value passed to <legacyBold>SQLBindParameter</legacyBold> in the <legacyItalic>ParameterValuePtr</legacyItalic> argument. Data-at-execution columns are columns in a rowset for which data will be sent with <legacyBold>SQLPutData</legacyBold> when a row is updated or added with <legacyBold>SQLBulkOperations</legacyBold> or updated with <legacyBold>SQLSetPos</legacyBold>. They are bound with <legacyBold>SQLBindCol</legacyBold>. The value returned by <legacyBold>SQLParamData</legacyBold> is the address of the row in the *<legacyItalic>TargetValuePtr</legacyItalic> buffer (set by a call to <legacyBold>SQLBindCol</legacyBold>) that is being processed.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLPutData</legacyBold> one or more times to send data for the parameter. More than one call is needed if the data value is larger than the *<legacyItalic>ParameterValuePtr</legacyItalic> buffer specified in <legacyBold>SQLPutData</legacyBold>; multiple calls to <legacyBold>SQLPutData</legacyBold> for the same parameter are allowed only when sending character C data to a column with a character, binary, or data source–specific data type or when sending binary C data to a column with a character, binary, or data source–specific data type.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLParamData</legacyBold> again to signal that all data has been sent for the parameter. </para>
          <list class="bullet">
            <listItem>
              <para>If there are more data-at-execution parameters, <legacyBold>SQLParamData</legacyBold> returns SQL_NEED_DATA and the application-defined value for the next data-at-execution parameter to be processed. The application repeats steps 4 and 5.</para>
            </listItem>
            <listItem>
              <para>If there are no more data-at-execution parameters, the process is complete. If the statement was successfully executed, <legacyBold>SQLParamData</legacyBold> returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO; if the execution failed, it returns SQL_ERROR. At this point, <legacyBold>SQLParamData</legacyBold> can return any SQLSTATE that can be returned by the function that is used to execute the statement (<legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold>). </para>
              <para>Output values for any input/output or output parameters are available in the *<legacyItalic>ParameterValuePtr</legacyItalic> and *<legacyItalic>StrLen_or_IndPtr</legacyItalic> buffers after the application retrieves all result sets generated by the statement. </para>
            </listItem>
          </list>
        </listItem>
      </list>
      <para>Calling <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> puts the statement in an SQL_NEED_DATA state. At this point, the application can call only <legacyBold>SQLCancel</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, <legacyBold>SQLGetDiagRec</legacyBold>, <legacyBold>SQLGetFunctions</legacyBold>, <legacyBold>SQLParamData</legacyBold>, or <legacyBold>SQLPutData </legacyBold>with the statement or the <legacyItalic>connection handle</legacyItalic> associated with the statement. If it calls any other function with the statement or the connection associated with the statement, the function returns SQLSTATE HY010 (Function sequence error). The statement leaves the SQL_NEED_DATA state when <legacyBold>SQLParamData</legacyBold> or <legacyBold>SQLPutData</legacyBold> returns an error, <legacyBold>SQLParamData</legacyBold> returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, or the statement is canceled.</para>
      <para>If the application calls <legacyBold>SQLCancel</legacyBold> while the driver still needs data for data-at-execution parameters, the driver cancels statement execution; the application can then call <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> again.</para>
    </content>
  </section>
  <section>
    <title>Retrieving Streamed Output Parameters</title>
    <content>
      <para>When an application sets <legacyItalic>InputOutputType</legacyItalic> to SQL_PARAM_INPUT_OUTPUT_STREAM or SQL_PARAM_OUTPUT_STREAM, the output parameter value must be retrieved by one or more calls to <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference>. When the driver has a streamed output parameter value to return to the application, it will return SQL_PARAM_DATA_AVAILABLE in response to a call to the following functions: <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, and <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>. An application calls <legacyBold>SQLParamData</legacyBold> to determine which parameter value is available.</para>
      <para>For more information about SQL_PARAM_DATA_AVAILABLE and streamed output parameters, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.</para>
    </content>
  </section>
  <section>
    <title>Using Arrays of Parameters</title>
    <content>
      <para>When an application prepares a statement with parameter markers and passes in an array of parameters, there are two different ways this can be executed. One way is for the driver to rely on the array-processing capabilities of the back end, in which case the whole statement with the array of parameters is treated as one atomic unit. Oracle is an example of a data source that supports array processing capabilities. Another way to implement this feature is for the driver to generate a batch of SQL statements, one SQL statement for each set of parameters in the parameter array, and execute the batch. Arrays of parameters cannot be used with an <legacyBold>UPDATE WHERE CURRENT OF</legacyBold> statement.</para>
      <para>When an array of parameters is processed, individual result sets/row counts (one for each parameter set) can be available or result sets/rows counts can be rolled up into one. The SQL_PARAM_ARRAY_ROW_COUNTS option in <legacyBold>SQLGetInfo</legacyBold> indicates whether row counts are available for each set of parameters (SQL_PARC_BATCH) or only one row count is available (SQL_PARC_NO_BATCH). </para>
      <para>The SQL_PARAM_ARRAY_SELECTS option in <legacyBold>SQLGetInfo</legacyBold> indicates whether a result set is available for each set of parameters (SQL_PAS_BATCH) or only one result set is available (SQL_PAS_NO_BATCH). If the driver does not allow a result set–generating statement to be executed with an array of parameters, SQL_PARAM_ARRAY_SELECTS returns SQL_PAS_NO_SELECT. </para>
      <para>For more information, see <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo Function</legacyLink>.</para>
      <para>To support arrays of parameters, the SQL_ATTR_PARAMSET_SIZE statement attribute is set to specify the number of values for each parameter. If the field is greater than 1, the SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR fields of the APD must point to arrays. The cardinality of each array is equal to the value of SQL_ATTR_PARAMSET_SIZE.</para>
      <para>The SQL_DESC_ROWS_PROCESSED_PTR field of the APD points to a buffer that contains the number of sets of parameters that have been processed, including error sets. As each set of parameters is processed, the driver stores a new value in the buffer. No number will be returned if this is a null pointer. When arrays of parameters are used, the value pointed to by the SQL_DESC_ROWS_PROCESSED_PTR field of the APD is populated even if SQL_ERROR is returned by the setting function. If SQL_NEED_DATA is returned, the value pointed to by the SQL_DESC_ROWS_PROCESSED_PTR field of the APD is set to the set of parameters that is being processed.</para>
      <para>What occurs when an array of parameters is bound and an <legacyBold>UPDATE WHERE CURRENT OF</legacyBold> statement is executed is driver-defined.</para>
    </content>
  </section>
  <section>
    <title>Column-Wise Parameter Binding</title>
    <content>
      <para>In column-wise binding, the application binds separate parameter and length/indicator arrays to each parameter.</para>
      <para>To use column-wise binding, the application first sets the SQL_ATTR_PARAM_BIND_TYPE statement attribute to SQL_PARAM_BIND_BY_COLUMN. (This is the default.) For each column to be bound, the application performs the following steps:  </para>
      <list class="ordered">
        <listItem>
          <para>Allocates a parameter buffer array.</para>
        </listItem>
        <listItem>
          <para>Allocates an array of length/indicator buffers. </para>
          <alert class="note">
            <para>If the application writes directly to descriptors when column-wise binding is used, separate arrays can be used for length and indicator data.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBindParameter</legacyBold> with the following arguments: </para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyItalic>ValueType</legacyItalic> is the C type of a single element in the parameter buffer array.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>ParameterType</legacyItalic> is the SQL type of the parameter.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>ParameterValuePtr</legacyItalic> is the address of the parameter buffer array.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>BufferLength</legacyItalic> is the size of a single element in the parameter buffer array. The <legacyItalic>BufferLength</legacyItalic> argument is ignored when the data is fixed-length data.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>StrLen_or_IndPtr</legacyItalic> is the address of the length/indicator array.</para>
            </listItem>
          </list>
        </listItem>
      </list>
      <para>For more information about how this information is used, see "ParameterValuePtr Argument" in "Comments," later in this section. For more information about column-wise binding of parameters, see <legacyLink xlink:href="037afe23-052d-4f3a-8aa7-45302b199ad0">Binding Arrays of Parameters</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Row-Wise Parameter Binding</title>
    <content>
      <para>In row-wise binding, the application defines a structure that contains parameter and length/indicator buffers for each parameter to be bound.</para>
      <para>To use row-wise binding, the application performs the following steps:  </para>
      <list class="ordered">
        <listItem>
          <para>Defines a structure to hold a single set of parameters (including both parameter and length/indicator buffers) and allocates an array of these structures. </para>
          <alert class="note">
            <para>If the application writes directly to descriptors when row-wise binding is used, separate fields can be used for length and indicator data.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Sets the SQL_ATTR_PARAM_BIND_TYPE statement attribute to the size of the structure that contains a single set of parameters or to the size of an instance of a buffer into which the parameters will be bound. The length must include space for all the bound parameters, and any padding of the structure or buffer, to make sure that when the address of a bound parameter is incremented with the specified length, the result will point to the beginning of the same parameter in the next row. When you use the <legacyItalic>sizeof</legacyItalic> operator in ANSI C, this behavior is guaranteed.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBindParameter</legacyBold> with the following arguments for each parameter to be bound: </para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyItalic>ValueType</legacyItalic> is the type of the parameter buffer member to be bound to the column.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>ParameterType</legacyItalic> is the SQL type of the parameter.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>ParameterValuePtr</legacyItalic> is the address of the parameter buffer member in the first array element.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>BufferLength</legacyItalic> is the size of the parameter buffer member.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>StrLen_or_IndPtr</legacyItalic> is the address of the length/indicator member to be bound.</para>
            </listItem>
          </list>
        </listItem>
      </list>
      <para>For more information about how this information is used, see "<legacyItalic>ParameterValuePtr</legacyItalic> Argument," later in this section. For more information about row-wise binding of parameters, see the <legacyLink xlink:href="037afe23-052d-4f3a-8aa7-45302b199ad0">Binding Arrays of Parameters</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Error Information</title>
    <content>
      <para>If a driver does not implement parameter arrays as batches (the SQL_PARAM_ARRAY_ROW_COUNTS option is equal to SQL_PARC_NO_BATCH), error situations are handled as if one statement were executed. If the driver does implement parameter arrays as batches, an application can use the SQL_DESC_ARRAY_STATUS_PTR header field of the IPD to determine which parameter of an SQL statement or which parameter in an array of parameters caused <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold> to return an error. This field contains status information for each row of parameter values. If the field indicates that an error has occurred, fields in the diagnostic data structure will indicate the row and parameter number of the parameter that failed. The number of elements in the array will be defined by the SQL_DESC_ARRAY_SIZE header field in the APD, which can be set by the SQL_ATTR_PARAMSET_SIZE statement attribute. </para>
      <alert class="note">
        <para>The SQL_DESC_ARRAY_STATUS_PTR header field in the APD is used to ignore parameters. For more information about ignoring parameters, see the next section, "Ignoring a Set of Parameters."</para>
      </alert>
      <para>When <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> returns SQL_ERROR, the elements in the array pointed to by the SQL_DESC_ARRAY_STATUS_PTR field in the IPD will contain SQL_PARAM_ERROR, SQL_PARAM_SUCCESS, SQL_PARAM_SUCCESS_WITH_INFO, SQL_PARAM_UNUSED, or SQL_PARAM_DIAG_UNAVAILABLE. </para>
      <para>For each element in this array, the diagnostic data structure contains one or more status records. The SQL_DIAG_ROW_NUMBER field of the structure indicates the row number of the parameter values that caused the error. If it is possible to determine the particular parameter in a row of parameters that caused the error, the parameter number will be entered in the SQL_DIAG_COLUMN_NUMBER field.</para>
      <para>SQL_PARAM_UNUSED is entered when a parameter has not been used because an error occurred in an earlier parameter that forced <legacyBold>SQLExecute </legacyBold>or <legacyBold>SQLExecDirect </legacyBold>to abort. For example, if there are 50 parameters and an error occurred while executing the fortieth set of parameters that caused <legacyBold>SQLExecute </legacyBold>or <legacyBold>SQLExecDirect </legacyBold>to abort, then SQL_PARAM_UNUSED is entered in the status array for parameters 41 through 50.</para>
      <para>SQL_PARAM_DIAG_UNAVAILABLE is entered when the driver treats arrays of parameters as a monolithic unit, so it does not generate this individual parameter level of error information.</para>
      <para>Some errors in the processing of a single set of parameters cause processing of the subsequent sets of parameters in the array to stop. Other errors do not affect the processing of subsequent parameters. Which errors will stop processing is driver-defined. If processing is not stopped, all parameters in the array are processed, SQL_SUCCESS_WITH_INFO is returned as a result of the error, and the buffer defined by SQL_ATTR_PARAMS_PROCESSED_PTR is set to the total number of sets of parameters processed (as defined by the SQL_ATTR_PARAMSET_SIZE statement attribute), which includes error sets.</para>
      <alert class="caution">
        <para>ODBC behavior when an error occurs in the processing of an array of parameters is different in ODBC 3.<legacyItalic>x</legacyItalic> than it was in ODBC 2.<legacyItalic>x</legacyItalic>. In ODBC 2.<legacyItalic>x</legacyItalic>, the function returned SQL_ERROR and processing ceased. The buffer pointed to by the <legacyItalic>pirow</legacyItalic> argument of <legacyBold>SQLParamOptions</legacyBold> contained the number of the error row. In ODBC 3.<legacyItalic>x</legacyItalic>, the function returns SQL_SUCCESS_WITH_INFO and processing may either stop or continue. If it continues, the buffer specified by SQL_ATTR_PARAMS_PROCESSED_PTR will be set to the value of all parameters processed, including those that resulted in an error. This change in behavior may cause problems for existing applications.</para>
      </alert>
      <para>When <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> returns before completing the processing of all parameter sets in a parameter array, such as when SQL_ERROR or SQL_NEED_DATA is returned, the status array contains statuses for those parameters that have already been processed. The location pointed to by the SQL_DESC_ROWS_PROCESSED_PTR field in the IPD contains the row number in the parameter array that caused the SQL_ERROR or SQL_NEED_DATA error code. When an array of parameters is sent to a SELECT statement, the availability of status array values is driver-defined; they may be available after the statement has been executed or as result sets are fetched.</para>
    </content>
  </section>
  <section>
    <title>Ignoring a Set of Parameters</title>
    <content>
      <para>The SQL_DESC_ARRAY_STATUS_PTR field of the APD (as set by the SQL_ATTR_PARAM_STATUS_PTR statement attribute) can be used to indicate that a set of bound parameters in an SQL statement should be ignored. To direct the driver to ignore one or more sets of parameters during execution, an application should follow these steps:  </para>
      <list class="ordered">
        <listItem>
          <para>Call <legacyBold>SQLSetDescField</legacyBold> to set the SQL_DESC_ARRAY_STATUS_PTR header field of the APD to point to an array of SQLUSMALLINT values to contain status information. This field can also be set by calling <legacyBold>SQLSetStmtAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> of SQL_ATTR_PARAM_OPERATION_PTR, which allows an application to set the field without obtaining a descriptor handle.</para>
        </listItem>
        <listItem>
          <para>Set each element of the array defined by the SQL_DESC_ARRAY_STATUS_PTR field of the APD to one of two values: </para>
          <list class="bullet">
            <listItem>
              <para>SQL_PARAM_IGNORE, to indicate that the row is excluded from statement execution.</para>
            </listItem>
            <listItem>
              <para>SQL_PARAM_PROCEED, to indicate that the row is included in statement execution.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>Call <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold> to execute the prepared statement.</para>
        </listItem>
      </list>
      <para>The following rules apply to the array defined by the SQL_DESC_ARRAY_STATUS_PTR field of the APD:  </para>
      <list class="bullet">
        <listItem>
          <para>The pointer is set to null by default.</para>
        </listItem>
        <listItem>
          <para>If the pointer is null, all sets of parameters are used, as if all elements were set to SQL_ROW_PROCEED.</para>
        </listItem>
        <listItem>
          <para>Setting an element to SQL_PARAM_PROCEED does not guarantee that the operation will use that particular set of parameters.</para>
        </listItem>
        <listItem>
          <para>SQL_PARAM_PROCEED is defined as 0 in the header file.</para>
        </listItem>
      </list>
      <para>An application can set the SQL_DESC_ARRAY_STATUS_PTR field in the APD to point to the same array as that pointed to by the SQL_DESC_ARRAY_STATUS_PTR field in the IRD. This is useful when binding parameters to row data. Parameters can then be ignored according to the status of the row data. In addition to SQL_PARAM_IGNORE, the following codes cause a parameter in an SQL statement to be ignored: SQL_ROW_DELETED, SQL_ROW_UPDATED, and SQL_ROW_ERROR. In addition to SQL_PARAM_PROCEED, the following codes cause an SQL statement to proceed: SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO, and SQL_ROW_ADDED.</para>
    </content>
  </section>
  <section>
    <title>Rebinding Parameters</title>
    <content>
      <para>An application can perform either of two operations to change a binding:  </para>
      <list class="bullet">
        <listItem>
          <para>Call <legacyBold>SQLBindParameter</legacyBold> to specify a new binding for a column that is already bound. The driver overwrites the old binding with the new one.</para>
        </listItem>
        <listItem>
          <para>Specify an offset to be added to the buffer address that was specified by the binding call to <legacyBold>SQLBindParameter</legacyBold>. For more information, see the next section, "Rebinding with Offsets."</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Rebinding with Offsets</title>
    <content>
      <para>Rebinding of parameters is especially useful when an application has a buffer area setup that can contain many parameters but a call to <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold> uses only a few of the parameters. The remaining space in the buffer area can be used for the next set of parameters by modifying the existing binding by an offset.</para>
      <para>The SQL_DESC_BIND_OFFSET_PTR header field in the APD points to the binding offset. If the field is non-null, the driver dereferences the pointer and, if none of the values in the SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR fields is a null pointer, adds the dereferenced value to those fields in the descriptor records at execution time. The new pointer values are used when the SQL statements are executed. The offset remains valid after rebinding. Because SQL_DESC_BIND_OFFSET_PTR is a pointer to the offset rather than the offset itself, an application can change the offset directly, without having to call <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink> or <legacyLink xlink:href="bf55256c-7eb7-4e3f-97ef-b0fee09ba829">SQLSetDescRec</legacyLink> to change the descriptor field. The pointer is set to null by default. The SQL_DESC_BIND_OFFSET_PTR field of the ARD can be set by a call to <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink> or by a call to <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink>with an <legacyItalic>fAttribute</legacyItalic> of SQL_ATTR_PARAM_BIND_OFFSET_PTR.</para>
      <para>The binding offset is always added directly to the values in the SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR fields. If the offset is changed to a different value, the new value is still added directly to the value in each descriptor field. The new offset is not added to the sum of the field value and any earlier offsets.</para>
    </content>
  </section>
  <section>
    <title>Descriptors</title>
    <content>
      <para>How a parameter is bound is determined by fields of the APDs and IPDs. The arguments in <legacyBold>SQLBindParameter</legacyBold> are used to set those descriptor fields. The fields can also be set by the <legacyBold>SQLSetDescField</legacyBold> functions, although <legacyBold>SQLBindParameter</legacyBold> is more efficient to use because the application does not have to obtain a descriptor handle to call <legacyBold>SQLBindParameter</legacyBold>. </para>
      <alert class="caution">
        <para>Calling <legacyBold>SQLBindParameter</legacyBold> for one statement can affect other statements. This occurs when the ARD associated with the statement is explicitly allocated and is also associated with other statements. Because <legacyBold>SQLBindParameter</legacyBold> modifies the fields of the APD, the modifications apply to all statements with which this descriptor is associated. If this is not the required behavior, the application should dissociate this descriptor from the other statements before it calls <legacyBold>SQLBindParameter</legacyBold>.</para>
      </alert>
      <para>Conceptually, <legacyBold>SQLBindParameter</legacyBold> performs the following steps in sequence:  </para>
      <list class="ordered">
        <listItem>
          <para>Calls <legacyLink xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr</legacyLink> to obtain the APD handle.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyLink xlink:href="f09ff660-1e4a-4370-be85-90d4da0487d3">SQLGetDescField</legacyLink> to get the APD's SQL_DESC_COUNT field, and if the value of the <legacyItalic>ColumnNumber</legacyItalic> argument exceeds the value of SQL_DESC_COUNT, calls <legacyBold>SQLSetDescField</legacyBold> to increase the value of SQL_DESC_COUNT to <legacyItalic>ColumnNumber</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink> multiple times to assign values to the following fields of the APD: </para>
          <list class="bullet">
            <listItem>
              <para>Sets SQL_DESC_TYPE and SQL_DESC_CONCISE_TYPE to the value of <legacyItalic>ValueType</legacyItalic>, except that if <legacyItalic>ValueType</legacyItalic> is one of the concise identifiers of a datetime or interval subtype, it sets SQL_DESC_TYPE to SQL_DATETIME or SQL_INTERVAL, respectively, sets SQL_DESC_CONCISE_TYPE to the concise identifier, and sets SQL_DESC_DATETIME_INTERVAL_CODE to the corresponding datetime or interval subcode.</para>
            </listItem>
            <listItem>
              <para>Sets the SQL_DESC_OCTET_LENGTH field to the value of <legacyItalic>BufferLength</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>Sets the SQL_DESC_DATA_PTR field to the value of <legacyItalic>ParameterValue</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>Sets the SQL_DESC_OCTET_LENGTH_PTR field to the value of <legacyItalic>StrLen_or_Ind</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>Sets the SQL_DESC_INDICATOR_PTR field also to the value of <legacyItalic>StrLen_or_Ind</legacyItalic>.</para>
            </listItem>
          </list>
          <para>The <legacyItalic>StrLen_or_Ind</legacyItalic> parameter specifies both the indicator information and the length for the parameter value. </para>
        </listItem>
        <listItem>
          <para>Calls <legacyLink xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr</legacyLink> to obtain the IPD handle.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyLink xlink:href="f09ff660-1e4a-4370-be85-90d4da0487d3">SQLGetDescField</legacyLink> to get the IPD's SQL_DESC_COUNT field, and if the value of the <legacyItalic>ColumnNumber</legacyItalic> argument exceeds the value of SQL_DESC_COUNT, calls <legacyBold>SQLSetDescField</legacyBold> to increase the value of SQL_DESC_COUNT to <legacyItalic>ColumnNumber</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink> multiple times to assign values to the following fields of the IPD: </para>
          <list class="bullet">
            <listItem>
              <para>Sets SQL_DESC_TYPE and SQL_DESC_CONCISE_TYPE to the value of <legacyItalic>ParameterType</legacyItalic>, except that if <legacyItalic>ParameterType</legacyItalic> is one of the concise identifiers of a datetime or interval subtype, it sets SQL_DESC_TYPE to SQL_DATETIME or SQL_INTERVAL, respectively, sets SQL_DESC_CONCISE_TYPE to the concise identifier, and sets SQL_DESC_DATETIME_INTERVAL_CODE to the corresponding datetime or interval subcode.</para>
            </listItem>
            <listItem>
              <para>Sets one or more of SQL_DESC_LENGTH, SQL_DESC_PRECISION, and SQL_DESC_DATETIME_INTERVAL_PRECISION, as appropriate for <legacyItalic>ParameterType</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>Sets SQL_DESC_SCALE to the value of <legacyItalic>DecimalDigits</legacyItalic>.</para>
            </listItem>
          </list>
        </listItem>
      </list>
      <para>If the call to <legacyBold>SQLBindParameter</legacyBold> fails, the content of the descriptor fields that it would have set in the APD are undefined, and the SQL_DESC_COUNT field of the APD is unchanged. In addition, the SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE, and SQL_DESC_TYPE fields of the appropriate record in the IPD are undefined and the SQL_DESC_COUNT field of the IPD is unchanged.</para>
    </content>
  </section>
  <section>
    <title>Conversion of Calls to and from SQLSetParam</title>
    <content>
      <para>When an ODBC 1.0 application calls <legacyBold>SQLSetParam</legacyBold> in an ODBC 3.<legacyItalic>x</legacyItalic> driver, the ODBC 3.<legacyItalic>x</legacyItalic> Driver Manager maps the call as shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Call by ODBC 1.0 application</para>
            </TD>
            <TD>
              <para>Call to ODBC 3.<legacyItalic>x</legacyItalic> driver</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQLSetParam(      StatementHandle,      ParameterNumber,      ValueType,      ParameterType,      LengthPrecision,      ParameterScale,      ParameterValuePtr,      StrLen_or_IndPtr);</para>
            </TD>
            <TD>
              <para>SQLBindParameter(      StatementHandle,      ParameterNumber,      SQL_PARAM_INPUT_OUTPUT,      ValueType,      ParameterType,      <legacyItalic>ColumnSize</legacyItalic>,      <legacyItalic>DecimalDigits</legacyItalic>,      ParameterValuePtr,      SQL_SETPARAM_VALUE_MAX,      StrLen_or_IndPtr);</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>In the following example, an application prepares an SQL statement to insert data into the ORDERS table. For each parameter in the statement, the application calls <legacyBold>SQLBindParameter</legacyBold> to specify the ODBC C data type and the SQL data type of the parameter, and to bind a buffer to each parameter. For each row of data, the application assigns data values to each parameter and calls <legacyBold>SQLExecute</legacyBold> to execute the statement.</para>
      <para>The following sample assumes that you have an ODBC data source on your computer called Northwind that is associated with the Northwind database.</para>
      <para>For more code examples, see <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations Function</legacyLink>, <legacyLink xlink:href="d0d9ef10-2fd4-44a5-9334-649f186f4ba0">SQLProcedures Function</legacyLink>, <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData Function</legacyLink>, and <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</legacyLink>.</para>
      <code>// SQLBindParameter_Function.cpp
// compile with: ODBC32.lib
#include &lt;windows.h&gt;
#include &lt;sqltypes.h&gt;
#include &lt;sqlext.h&gt;

#define EMPLOYEE_ID_LEN 10

SQLHENV henv = NULL;
SQLHDBC hdbc = NULL;
SQLRETURN retcode;
SQLHSTMT hstmt = NULL;
SQLSMALLINT sCustID;

SQLCHAR szEmployeeID[EMPLOYEE_ID_LEN];
SQL_DATE_STRUCT dsOrderDate;
SQLINTEGER cbCustID = 0, cbOrderDate = 0, cbEmployeeID = SQL_NTS;

int main() {
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0); 

   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc); 
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);

   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt);

   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, EMPLOYEE_ID_LEN, 0, szEmployeeID, 0, &amp;cbEmployeeID);
   retcode = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &amp;sCustID, 0, &amp;cbCustID);
   retcode = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TIMESTAMP, sizeof(dsOrderDate), 0, &amp;dsOrderDate, 0, &amp;cbOrderDate);

   retcode = SQLPrepare(hstmt, (SQLCHAR*)"INSERT INTO Orders(CustomerID, EmployeeID, OrderDate) VALUES (?, ?, ?)", SQL_NTS);

   strcpy_s((char*)szEmployeeID, _countof(szEmployeeID), "BERGS");
   sCustID = 5;
   dsOrderDate.year = 2006;
   dsOrderDate.month = 3;
   dsOrderDate.day = 17;

   retcode = SQLExecute(hstmt);
}</code>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>In the following example, an application executes a SQL Server stored procedure using a named parameter.</para>
      <code>// SQLBindParameter_Function_2.cpp
// compile with: ODBC32.lib
// sample assumes the following stored procedure:
// use northwind
// DROP PROCEDURE SQLBindParameter
// GO
// 
// CREATE PROCEDURE SQLBindParameter @quote int
// AS
// delete from orders where OrderID &gt;= @quote
// GO
#include &lt;windows.h&gt;
#include &lt;sqltypes.h&gt;
#include &lt;sqlext.h&gt;

SQLHDESC hIpd = NULL;
SQLHENV henv = NULL;
SQLHDBC hdbc = NULL;
SQLRETURN retcode;
SQLHSTMT hstmt = NULL;
SQLCHAR szQuote[50] = "100084";
SQLINTEGER cbValue = SQL_NTS;

int main() {
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0); 

   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc); 
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);

   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt);

   retcode = SQLPrepare(hstmt, (SQLCHAR*)"{call SQLBindParameter(?)}", SQL_NTS);
   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 50, 0, szQuote, 0, &amp;cbValue);
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &amp;hIpd, 0, 0);
   retcode = SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);

   retcode = SQLExecute(hstmt);
}</code>
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
              <para>Returning information about a parameter in  a statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="1f5b63c4-2f3e-44da-b155-876405302281">SQLDescribeParam Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing an SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect Function</legacyLink>
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
              <para>Releasing parameter buffers on the statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the number of statement  parameters</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="dbf2da44-253b-4094-bd6b-29bafc23c7a3">SQLNumParams Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the next parameter to send data  for</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="68fe010d-9539-4e5b-a260-c8d32423b1db">SQLParamData Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Specifying multiple parameter values</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ee08e987-0243-4060-ab21-64da11fe444f">SQLParamOptions Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Sending parameter data at execution time</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData Function</legacyLink>
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
<link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>