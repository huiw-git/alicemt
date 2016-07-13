---
title: Retrieving Output Parameters Using SQLGetData
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a8c298a-2160-491d-a300-d36f45568d9c
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Retrieving Output Parameters Using SQLGetData
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Before ODBC 3.8, an application could only retrieve the output parameters of a query with a bound output buffer. However, it is difficult to allocate a very large buffer when the size of the parameter value is very large (for example, a large image). ODBC 3.8 introduces a new way to retrieve output parameters in parts. An application can now call <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> with a small buffer multiple times to retrieve a large parameter value. This is similar to retrieving large column data.</para>
    <para>To bind an output parameter or input/output parameter to be retrieved in parts, call <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference> with the <parameterReference>InputOutputType</parameterReference> argument set to SQL_PARAM_OUTPUT_STREAM or SQL_PARAM_INPUT_OUTPUT_STREAM. With SQL_PARAM_INPUT_OUTPUT_STREAM, an application can use <unmanagedCodeEntityReference>SQLPutData</unmanagedCodeEntityReference> to input data into the parameter, and then use <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> to retrieve the output parameter. The input data must be in the data-at-execution (DAE) form, using <unmanagedCodeEntityReference>SQLPutData</unmanagedCodeEntityReference> instead of binding it to a preallocated buffer.</para>
    <para>This feature can be used by ODBC 3.8 applications or recompiled ODBC 3.x and ODBC 2.x applications, and these applications must have an ODBC 3.8 driver that supports retrieving output parameters using <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> and ODBC 3.8 Driver Manager. For information about how to enable an older application to use new ODBC features, see <link xlink:href="0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6">Compatibility Matrix</link>. </para>
  </introduction>
  <section>
    <title>Usage Example</title>
    <content>
      <para>For example, consider executing a stored procedure, <languageKeyword>{CALL sp_f(?,?)}</languageKeyword>, where both parameters are bound as SQL_PARAM_OUTPUT_STREAM, and the stored procedure returns no result set (later in this topic you will find a more complex scenario):</para>
      <list class="ordered">
        <listItem>
          <para>For each parameter, call <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference> with <parameterReference>InputOutputType</parameterReference> set to SQL_PARAM_OUTPUT_STREAM and <parameterReference>ParameterValuePtr</parameterReference> set to a token, such as a parameter number, a pointer to data, or a pointer to a structure that the application uses to bind input parameters. This example will use the parameter ordinal as the token.</para>
        </listItem>
        <listItem>
          <para>Execute the query with <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>. SQL_PARAM_DATA_AVAILABLE will be returned, indicating that there are streamed output parameters available for retrieval.</para>
        </listItem>
        <listItem>
          <para>Call <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> to get the parameter that is available for retrieval. <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> will return SQL_PARAM_DATA_AVAILABLE with the token of the first available parameter, which is set in <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference> (step 1). The token is returned in the buffer that the <parameterReference>ValuePtrPtr</parameterReference> points to.</para>
        </listItem>
        <listItem>
          <para>Call <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> with the argument <parameterReference>Col</parameterReference>_or_<parameterReference>Param_Num</parameterReference> set to the parameter ordinal to retrieve the data of the first available parameter. If <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> returns SQL_SUCCESS_WITH_INFO and SQLState 01004 (data truncated), and the type is variable length on both the client and server, there is more data to retrieve from the first available parameter. You can continue to call <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> until it returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO with a different <unmanagedCodeEntityReference>SQLState</unmanagedCodeEntityReference>.</para>
        </listItem>
        <listItem>
          <para>Repeat step 3 and step 4 to retrieve the current parameter.</para>
        </listItem>
        <listItem>
          <para>Call <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> again. If it returns anything except SQL_PARAM_DATA_AVAILABLE, there is no more streamed parameter data to retrieve, and the return code will be the return code of the next statement that is executed.</para>
        </listItem>
        <listItem>
          <para>Call <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> to process the next set of parameters until it returns SQL_NO_DATA. <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> will return SQL_NO_DATA in this example if the statement attribute SQL_ATTR_PARAMSET_SIZE was set to 1. Otherwise, <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> will return SQL_PARAM_DATA_AVAILABLE to indicate that there are streamed output parameters available for the next set of parameters to retrieve.</para>
        </listItem>
      </list>
      <para>Similar to a DAE input parameter, the token used in the argument <parameterReference>ParameterValuePtr</parameterReference> in <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference> (step 1) can be a pointer that points to an application data structure, which contains the ordinal of the parameter and more application-specific information, if necessary.</para>
      <para>The order of the returned streamed output or input/output parameters is driver specific and might not always be the same as the order specified in the query.</para>
      <para>If the application does not call <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> in step 4, the parameter value is discarded. Similarly, if the application calls <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> before all of a parameter value has been read by <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference>, the remainder of the value is discarded, and the application can process the next parameter.</para>
      <para>If the application calls <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> before all streamed output parameters are processed (<unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> does still return SQL_PARAM_DATA_AVAILABLE), all remaining parameters are discarded. Similarly, if the application calls <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> before all of a parameter value has been read by <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference>, the remainder of the value and all remaining parameters are discarded, and the application can continue to process the next parameter set.</para>
      <para>Note that an application can specify the C data type in both <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference>. The C data type specified with <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> overrides the C data type specified in <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference>, unless the C data type specified in <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> is SQL_APD_TYPE.</para>
      <para>Although a streamed output parameter is more useful when the data type of the output parameter is of type BLOB, this functionality can also be used with any data type. The data types supported by streamed output parameters are specified in the driver.</para>
      <para>If there are SQL_PARAM_INPUT_OUTPUT_STREAM parameters to be processed, <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference> will return SQL_NEED_DATA first. An application can call <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLPutData</unmanagedCodeEntityReference> to send DAE parameter data. When all DAE input parameters are processed, <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> returns SQL_PARAM_DATA_AVAILABLE to indicate streamed output parameters are available. </para>
      <para>When there are streamed output parameters and bound output parameters to be processed, the driver determines the order for processing output parameters. So, if an output parameter is bound to a buffer (the <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference> parameter <parameterReference>InputOutputType</parameterReference> is set to SQL_PARAM_INPUT_OUTPUT or SQL_PARAM_OUTPUT), the buffer may not be populated until <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO. An application should read a bound buffer only after <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO that is after all streamed output parameters are processed.</para>
      <para>The data source can return a warning and result set, in addition to the streamed output parameter. In general, warnings and result sets are processed separately from a streamed output parameter by calling <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference>. Process warnings and the result set before processing the streamed output parameter.</para>
      <para>The following table describes different scenarios of a single command sent to the server, and how the application should work.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Scenario</para>
            </TD>
            <TD>
              <para>Return value from SQLExecute or SQLExecDirect</para>
            </TD>
            <TD>
              <para>What to do next</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Data only includes streamed output parameters</para>
            </TD>
            <TD>
              <para>SQL_PARAM_DATA_AVAILABLE</para>
            </TD>
            <TD>
              <para>Use <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> to retrieve streamed output parameters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Data includes a result set and streamed output parameters</para>
            </TD>
            <TD>
              <para>SQL_SUCCESS</para>
            </TD>
            <TD>
              <para>Retrieve the result set with <unmanagedCodeEntityReference>SQLBindCol</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference>.</para>
              <para>Call <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> to start processing streamed output parameters. It should return SQL_PARAM_DATA_AVAILABLE.</para>
              <para>Use <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> to retrieve streamed output parameters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Data includes a warning message and streamed output parameters</para>
            </TD>
            <TD>
              <para>SQL_SUCCESS_WITH_INFO</para>
            </TD>
            <TD>
              <para>Use <unmanagedCodeEntityReference>SQLGetDiagRec</unmanagedCodeEntityReference> and<unmanagedCodeEntityReference> SQLGetDiagField</unmanagedCodeEntityReference> to process warning messages.</para>
              <para>Call <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> to start processing streamed output parameters. It should return SQL_PARAM_DATA_AVAILABLE.</para>
              <para>Use <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> and<unmanagedCodeEntityReference> SQLGetData</unmanagedCodeEntityReference> to retrieve streamed output parameters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Data includes a warning message, result set and streamed output parameters</para>
            </TD>
            <TD>
              <para>SQL_SUCCESS_WITH_INFO</para>
            </TD>
            <TD>
              <para>Use <unmanagedCodeEntityReference>SQLGetDiagRec</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLGetDiagField</unmanagedCodeEntityReference> to process warning messages. Then call <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> to start processing the result set.</para>
              <para>Retrieve a result set with <unmanagedCodeEntityReference>SQLBindCol</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference>.</para>
              <para>Call <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> to start processing streamed output parameters. <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> should return SQL_PARAM_DATA_AVAILABLE.</para>
              <para>Use <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> to retrieve streamed output parameters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Query with DAE input parameters, for example, a streamed input/output (DAE) parameter</para>
            </TD>
            <TD>
              <para>SQL NEED_DATA</para>
            </TD>
            <TD>
              <para>Call <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLPutData</unmanagedCodeEntityReference> to send DAE input parameter data.</para>
              <para>After all DAE input parameters are processed, <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> can return any return code that <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference> can return. The cases in this table can then be applied.</para>
              <para>If the return code is SQL_PARAM_DATA_AVAILABLE, streamed output parameters are available. An application must call <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> again to retrieve the token for the streamed output parameter, as described in the first row of this table.</para>
              <para>If the return code is SQL_SUCCESS, either there is a result set to process or the processing is complete.</para>
              <para>If the return code is SQL_SUCCESS_WITH_INFO, there are warning messages to process.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>After <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>,<unmanagedCodeEntityReference> SQLExecDirect</unmanagedCodeEntityReference>, or<unmanagedCodeEntityReference> SQLMoreResults</unmanagedCodeEntityReference> returns SQL_PARAM_DATA_AVAILABLE, a function sequence error will result if an application calls a function that is not in the following list:</para>
      <list class="bullet">
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLAllocHandle</unmanagedCodeEntityReference> / <unmanagedCodeEntityReference>SQLAllocHandleStd</unmanagedCodeEntityReference></para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLDataSources</unmanagedCodeEntityReference> /<unmanagedCodeEntityReference> SQLDrivers</unmanagedCodeEntityReference></para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetInfo</unmanagedCodeEntityReference> / <unmanagedCodeEntityReference>SQLGetFunctions</unmanagedCodeEntityReference></para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetConnectAttr</unmanagedCodeEntityReference> / <unmanagedCodeEntityReference>SQLGetEnvAttr</unmanagedCodeEntityReference> /<unmanagedCodeEntityReference> SQLGetDescField</unmanagedCodeEntityReference> /<unmanagedCodeEntityReference> SQLGetDescRec</unmanagedCodeEntityReference></para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLNumParams</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLDescribeParam</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLNativeSql</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetDiagField</unmanagedCodeEntityReference> / <unmanagedCodeEntityReference>SQLGetDiagRec</unmanagedCodeEntityReference></para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> (with statement handle)</para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLFreeStmt</unmanagedCodeEntityReference> (with Option = SQL_CLOSE, SQL_DROP or SQL_UNBIND)</para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLCloseCursor</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLFreeHandle</unmanagedCodeEntityReference> (with HandleType = SQL_HANDLE_STMT)</para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetStmtAttr</unmanagedCodeEntityReference>
          </para>
        </listItem>
      </list>
      <para>Applications can still use <unmanagedCodeEntityReference>SQLSetDescField</unmanagedCodeEntityReference> or<unmanagedCodeEntityReference> SQLSetDescRec</unmanagedCodeEntityReference> to set the binding information. Field mapping will not be changed. However, fields inside the descriptor might return new values. For example, SQL_DESC_PARAMETER_TYPE might return SQL_PARAM_INPUT_OUTPUT_STREAM or SQL_PARAM_OUTPUT_STREAM.</para>
    </content>
  </section>
  <section>
    <title>Usage Scenario: Retrieve an Image in Parts from a Result Set</title>
    <content>
      <para>
        <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> can be used to get data in parts when a stored procedure returns a result set that contains one row of metadata about an image and the image is returned in a large output parameter.</para>
      <code>// CREATE PROCEDURE SP_TestOutputPara
//      @ID_of_picture   as int,
//      @Picture         as varbinary(max) out
// AS
//     output the image data through streamed output parameter
// GO
BOOL displayPicture(SQLUINTEGER idOfPicture, SQLHSTMT hstmt) {
   SQLLEN      lengthOfPicture;    // The actual length of the picture.
   BYTE        smallBuffer[100];   // A very small buffer.
   SQLRETURN   retcode, retcode2;

   // Bind the first parameter (input parameter)
   SQLBindParameter(
         hstmt,
         1,                         // The first parameter. 
         SQL_PARAM_INPUT,           // Input parameter: The ID_of_picture.
         SQL_C_ULONG,               // The C Data Type.
         SQL_INTEGER,               // The SQL Data Type.
         0,                         // ColumnSize is ignored for integer.
         0,                         // DecimalDigits is ignored for integer.
         &amp;idOfPicture,              // The Address of the buffer for the input parameter.
         0,                         // BufferLength is ignored for integer.
         NULL);                     // This is ignored for integer.

   // Bind the streamed output parameter.
   SQLBindParameter(
         hstmt, 
         2,                         // The second parameter.
         SQL_PARAM_OUTPUT_STREAM,   // A streamed output parameter. 
         SQL_C_BINARY,              // The C Data Type.  
         SQL_VARBINARY,             // The SQL Data Type.
         0,                         // ColumnSize: The maximum size of varbinary(max).
         0,                         // DecimalDigits is ignored for binary type.
         (SQLPOINTER)2,             // ParameterValuePtr: An application-defined
                                    // token (this will be returned from SQLParamData).
                                    // In this example, we used the ordinal 
                                    // of the parameter.
         0,                         // BufferLength is ignored for streamed output parameters.
         &amp;lengthOfPicture);         // StrLen_or_IndPtr: The status variable returned. 

   retcode = SQLPrepare(hstmt, L"{call SP_TestOutputPara(?, ?)}", SQL_NTS);
   if ( retcode == SQL_ERROR )
      return FALSE;

   retcode = SQLExecute(hstmt);
   if ( retcode == SQL_ERROR )
      return FALSE;

   // Assume that the retrieved picture exists.  Use SQLBindCol or SQLGetData to retrieve the result-set.

   // Process the result set and move to the streamed output parameters.
   retcode = SQLMoreResults( hstmt );

   // SQLGetData retrieves and displays the picture in parts.
   // The streamed output parameter is available.
   while (retcode == SQL_PARAM_DATA_AVAILABLE) {
      SQLPOINTER token;   // Output by SQLParamData.
      SQLLEN cbLeft;      // #bytes remained
      retcode = SQLParamData(hstmt, &amp;token);   // returned token is 2 (according to the binding)
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {
         // A do-while loop retrieves the picture in parts.
         do {
            retcode2 = SQLGetData( 
               hstmt, 
               (UWORD) token,          // the value of the token is the ordinal. 
               SQL_C_BINARY,           // The C-type.
               smallBuffer,            // A small buffer. 
               sizeof(smallBuffer),    // The size of the buffer.
               &amp;cbLeft);               // How much data we can get.
         }
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );
      }
   }

   return TRUE;
}</code>
    </content>
  </section>
  <section>
    <title>Usage Scenario: Send and Receive a Large Object as a Streamed Input/Output Parameter</title>
    <content>
      <para>
        <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> can be used to get and send data in parts when a stored procedure passes a large object as an input/output parameter, streaming the value to and from the database. You do not have to store all of the data in memory.</para>
      <code>// CREATE PROCEDURE SP_TestInOut
//       @picture as varbinary(max) out
// AS
//    output the image data through output parameter 
// go

BOOL displaySimilarPicture(BYTE* image, ULONG lengthOfImage, SQLHSTMT hstmt) {
   BYTE smallBuffer[100];   // A very small buffer.
   SQLRETURN retcode, retcode2;
   SQLLEN statusOfPicture;

   // First bind the parameters, before preparing the statement that binds the output streamed parameter.
   SQLBindParameter(
      hstmt, 
      1,                                 // The first parameter.
      SQL_PARAM_INPUT_OUTPUT_STREAM,     // I/O-streamed parameter: The Picture.
      SQL_C_BINARY,                      // The C Data Type.
      SQL_VARBINARY,                     // The SQL Data Type.
      0,                                 // ColumnSize: The maximum size of varbinary(max).
      0,                                 // DecimalDigits is ignored. 
      (SQLPOINTER)1,                     // An application defined token. 
      0,                                 // BufferLength is ignored for streamed I/O parameters.
      &amp;statusOfPicture);                 // The status variable.
   
   statusOfPicture = SQL_DATA_AT_EXEC;   // Input data in parts (DAE parameter at input).

   retcode = SQLPrepare(hstmt, L"{call SP_TestInOut(?) }", SQL_NTS);
   if ( retcode == SQL_ERROR )
      return FALSE;

   // Execute the statement.
   retcode = SQLExecute(hstmt);
   if ( retcode == SQL_ERROR )
      return FALSE;
   
   if ( retcode == SQL_NEED_DATA ) {
      // Use SQLParamData to loop through DAE input parameters.  For
      // each, use SQLPutData to send the data to database in parts.

      // This example uses an I/O parameter with streamed output.
      // Therefore, the last call to SQLParamData should return
      // SQL_PARAM_DATA_AVAILABLE to indicate the end of the input phrase 
      // and report that a streamed output parameter is available.

      // Assume retcode is set to the return value of the last call to
      // SQLParamData, which is equal to SQL_PARAM_DATA_AVAILABLE.
   }

   // Start processing the streamed output parameters.
   while ( retcode == SQL_PARAM_DATA_AVAILABLE ) {
      SQLPOINTER token;   // Output by SQLParamData.
      SQLLEN cbLeft;     // #bytes remained
      retcode = SQLParamData(hstmt, &amp;token);
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {
         do {
            retcode2 = SQLGetData( 
               hstmt, 
               (UWORD) token,          // the value of the token is the ordinal. 
               SQL_C_BINARY,           // The C-type.
               smallBuffer,            // A small buffer. 
               sizeof(smallBuffer),    // The size of the buffer.
               &amp;cbLeft);               // How much data we can get.
         }
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );
      }
   } 

   return TRUE;
}</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</link>
</relatedTopics>
</developerConceptualDocument>