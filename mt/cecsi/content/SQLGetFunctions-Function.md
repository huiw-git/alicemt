---
title: SQLGetFunctions Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLGetFunctions
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
translation.priority.ht: 
  - en-gb
---
# SQLGetFunctions Function
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
          <legacyBold>SQLGetFunctions</legacyBold> returns information about whether a driver supports a specific ODBC function. This function is implemented in the Driver Manager; it can also be implemented in drivers. If a driver implements <legacyBold>SQLGetFunctions</legacyBold>, the Driver Manager calls the function in the driver. Otherwise, it executes the function itself.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetFunctions</legacyBold>(
     SQLHDBC           <parameterReference>ConnectionHandle</parameterReference>,
     SQLUSMALLINT      <parameterReference>FunctionId</parameterReference>,
     SQLUSMALLINT *    <parameterReference>SupportedPtr</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>ConnectionHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Connection handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FunctionId</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A <legacyBold>#define</legacyBold> value that identifies the ODBC function of interest; <languageKeyword>SQL_API_ODBC3_ALL_FUNCTIONS or</languageKeyword> <languageKeyword>SQL_API_ALL_FUNCTIONS</languageKeyword>. <languageKeyword>SQL_API_ODBC3_ALL_FUNCTIONS</languageKeyword> is used by an ODBC 3<legacyItalic>.x</legacyItalic> application to determine support of ODBC 3<legacyItalic>.x</legacyItalic> and earlier functions. <languageKeyword>SQL_API_ALL_FUNCTIONS</languageKeyword> is used by an ODBC 2<legacyItalic>.x</legacyItalic> application to determine support of ODBC 2<legacyItalic>.x</legacyItalic> and earlier functions.</para>
          <para>For a list of <legacyBold>#define</legacyBold> values that identify ODBC functions, see the tables in "Comments." </para>
        </definition>
        <definedTerm>
          <legacyItalic>SupportedPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output]  If <legacyItalic>FunctionId</legacyItalic> identifies a single ODBC function, <legacyItalic>SupportedPtr</legacyItalic> points to a single SQLUSMALLINT value that is SQL_TRUE if the specified function is supported by the driver, and SQL_FALSE if it is not supported.</para>
          <para>If <legacyItalic>FunctionId</legacyItalic> is SQL_API_ODBC3_ALL_FUNCTIONS, <legacyItalic>SupportedPtr</legacyItalic> points to a SQLSMALLINT array with a number of elements equal to SQL_API_ODBC3_ALL_FUNCTIONS_SIZE. This array is treated by the Driver Manager as a 4,000-bit bitmap that can be used to determine whether an ODBC 3<legacyItalic>.x</legacyItalic> or earlier function is supported. The SQL_FUNC_EXISTS macro is called to determine function support. (See "Comments.") An ODBC 3<legacyItalic>.x</legacyItalic> application can call <legacyBold>SQLGetFunctions</legacyBold> with SQL_API_ODBC3_ALL_FUNCTIONS against either an ODBC 3<legacyItalic>.x</legacyItalic> or ODBC 2<legacyItalic>.x</legacyItalic> driver.   </para>
          <para>If <legacyItalic>FunctionId</legacyItalic> is SQL_API_ALL_FUNCTIONS, <legacyItalic>SupportedPtr</legacyItalic> points to an SQLUSMALLINT array of 100 elements. The array is indexed by <legacyBold>#define</legacyBold> values used by <legacyItalic>FunctionId</legacyItalic> to identify each ODBC function; some elements of the array are unused and reserved for future use. An element is SQL_TRUE if it identifies an ODBC 2<legacyItalic>.x</legacyItalic> or earlier function supported by the driver. It is SQL_FALSE if it identifies an ODBC function not supported by the driver or does not identify an ODBC function.   </para>
          <para>The arrays returned in *<legacyItalic>SupportedPtr </legacyItalic>use zero-based indexing. </para>
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
      <para>When <legacyBold>SQLGetFunctions</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>ConnectionHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLGetFunctions</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>(DM) <legacyBold>SQLGetFunctions</legacyBold> was called before <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLBrowseConnect</legacyBold>, or <legacyBold>SQLDriverConnect</legacyBold>.</para>
              <para>(DM) <legacyBold>SQLBrowseConnect</legacyBold> was called for the <legacyItalic>ConnectionHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before <legacyBold>SQLBrowseConnect</legacyBold> returned SQL_SUCCESS_WITH_INFO or SQL_SUCCESS.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or<unmanagedCodeEntityReference> SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>ConnectionHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
              <para>HY095</para>
            </TD>
            <TD>
              <para>Function type out of range</para>
            </TD>
            <TD>
              <para>(DM) An invalid <legacyItalic>FunctionId</legacyItalic> value was specified.</para>
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
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLGetFunctions</legacyBold> always returns that <legacyBold>SQLGetFunctions</legacyBold>, <legacyBold>SQLDataSources</legacyBold>, and <legacyBold>SQLDrivers</legacyBold> are supported. It does this because these functions are implemented in the Driver Manager. The Driver Manager will map an ANSI function to the corresponding Unicode function if the Unicode function exists and will map a Unicode function to the corresponding ANSI function if the ANSI function exists. For information about how applications use <legacyBold>SQLGetFunctions</legacyBold>, see <legacyLink xlink:href="2c470e54-0600-4b2b-b1f3-9885cb28a01a">Interface Conformance Levels</legacyLink>.</para>
      <para>The following is a list of valid values for <legacyItalic>FunctionId</legacyItalic> for functions that conform to the ISO 92 standards–compliance level:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_API_SQLALLOCHANDLE</para>
            </TD>
            <TD>
              <para>SQL_API_SQLGETDESCFIELD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLBINDCOL</para>
            </TD>
            <TD>
              <para>SQL_API_SQLGETDESCREC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLCANCEL</para>
            </TD>
            <TD>
              <para>SQL_API_SQLGETDIAGFIELD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLCLOSECURSOR</para>
            </TD>
            <TD>
              <para>SQL_API_SQLGETDIAGREC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLCOLATTRIBUTE</para>
            </TD>
            <TD>
              <para>SQL_API_SQLGETENVATTR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLCONNECT</para>
            </TD>
            <TD>
              <para>SQL_API_SQLGETFUNCTIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLCOPYDESC</para>
            </TD>
            <TD>
              <para>SQL_API_SQLGETINFO</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLDATASOURCES</para>
            </TD>
            <TD>
              <para>SQL_API_SQLGETSTMTATTR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLDESCRIBECOL</para>
            </TD>
            <TD>
              <para>SQL_API_SQLGETTYPEINFO</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLDISCONNECT</para>
            </TD>
            <TD>
              <para>SQL_API_SQLNUMRESULTCOLS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLDRIVERS</para>
            </TD>
            <TD>
              <para>SQL_API_SQLPARAMDATA</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLENDTRAN</para>
            </TD>
            <TD>
              <para>SQL_API_SQLPREPARE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLEXECDIRECT</para>
            </TD>
            <TD>
              <para>SQL_API_SQLPUTDATA</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLEXECUTE</para>
            </TD>
            <TD>
              <para>SQL_API_SQLROWCOUNT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLFETCH</para>
            </TD>
            <TD>
              <para>SQL_API_SQLSETCONNECTATTR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLFETCHSCROLL</para>
            </TD>
            <TD>
              <para>SQL_API_SQLSETCURSORNAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLFREEHANDLE</para>
            </TD>
            <TD>
              <para>SQL_API_SQLSETDESCFIELD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLFREESTMT</para>
            </TD>
            <TD>
              <para>SQL_API_SQLSETDESCREC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLGETCONNECTATTR</para>
            </TD>
            <TD>
              <para>SQL_API_SQLSETENVATTR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLGETCURSORNAME</para>
            </TD>
            <TD>
              <para>SQL_API_SQLSETSTMTATTR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLGETDATA</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The following is a list of valid values for <legacyItalic>FunctionId</legacyItalic> for functions conforming to the Open Group standards–compliance level:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_API_SQLCOLUMNS</para>
            </TD>
            <TD>
              <para>SQL_API_SQLSTATISTICS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLSPECIALCOLUMNS</para>
            </TD>
            <TD>
              <para>SQL_API_SQLTABLES</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The following is a list of valid values for <legacyItalic>FunctionId</legacyItalic> for functions conforming to the ODBC standards–compliance level.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_API_SQLBINDPARAMETER</para>
            </TD>
            <TD>
              <para>SQL_API_SQLNATIVESQL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLBROWSECONNECT</para>
            </TD>
            <TD>
              <para>SQL_API_SQLNUMPARAMS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLBULKOPERATIONS[1]</para>
            </TD>
            <TD>
              <para>SQL_API_SQLPRIMARYKEYS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLCOLUMNPRIVILEGES</para>
            </TD>
            <TD>
              <para>SQL_API_SQLPROCEDURECOLUMNS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLDESCRIBEPARAM</para>
            </TD>
            <TD>
              <para>SQL_API_SQLPROCEDURES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLDRIVERCONNECT</para>
            </TD>
            <TD>
              <para>SQL_API_SQLSETPOS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLFOREIGNKEYS</para>
            </TD>
            <TD>
              <para>SQL_API_SQLTABLEPRIVILEGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_API_SQLMORERESULTS</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   When working with an ODBC 2<legacyItalic>.x</legacyItalic> driver, <legacyBold>SQLBulkOperations</legacyBold> will be returned as supported only if both of the following are true: the ODBC 2<legacyItalic>.x</legacyItalic> driver supports <legacyBold>SQLSetPos</legacyBold>, and the information type SQL_POS_OPERATIONS returns the SQL_POS_ADD bit as set.</para>
      <para>The following is a list of valid values for <parameterReference>FunctionId</parameterReference> for functions introduced in ODBC 3.8 or later:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_API_SQLCANCELHANDLE [2]</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[2]   <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> will be returned as supported only if the driver supports both <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference> and<unmanagedCodeEntityReference> SQLCancelHandle</unmanagedCodeEntityReference>. If <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference> is supported but <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> is not, the application can still call <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> on a statement handle, because it will be mapped to <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference>.</para>
    </content>
  </section>
  <section>
    <title>SQL_FUNC_EXISTS Macro</title>
    <content>
      <para>The SQL_FUNC_EXISTS(<legacyItalic>SupportedPtr</legacyItalic>, <legacyItalic>FunctionID</legacyItalic>) macro is used to determine support of ODBC 3<legacyItalic>.x</legacyItalic> or earlier functions after <legacyBold>SQLGetFunctions</legacyBold> has been called with a <legacyItalic>FunctionId</legacyItalic> argument of SQL_API_ODBC3_ALL_FUNCTIONS. The application calls SQL_FUNC_EXISTS with the <legacyItalic>SupportedPtr</legacyItalic> argument set to the <legacyItalic>SupportedPtr </legacyItalic>passed in<legacyItalic> SQLGetFunctions</legacyItalic>, and with the <legacyItalic>FunctionID</legacyItalic> argument set to the <legacyBold>#define</legacyBold> for the function. SQL_FUNC_EXISTS returns SQL_TRUE if the function is supported, and SQL_FALSE otherwise.</para>
      <alert class="note">
        <para>When working with an ODBC 2<legacyItalic>.x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager will return SQL_TRUE for <legacyBold>SQLAllocHandle</legacyBold> and <legacyBold>SQLFreeHandle</legacyBold> because <legacyBold>SQLAllocHandle</legacyBold> is mapped to <legacyBold>SQLAllocEnv</legacyBold>, <legacyBold>SQLAllocConnect</legacyBold>, or <legacyBold>SQLAllocStmt</legacyBold>, and because <legacyBold>SQLFreeHandle</legacyBold> is mapped to <legacyBold>SQLFreeEnv</legacyBold>, <legacyBold>SQLFreeConnect</legacyBold>, or <legacyBold>SQLFreeStmt</legacyBold>. <legacyBold>SQLAllocHandle</legacyBold> or <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> argument of SQL_HANDLE_DESC is not supported, however, even though SQL_TRUE is returned for the functions, because there is no ODBC 2<legacyItalic>.x</legacyItalic> function to map to in this case.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>The following three examples show how an application uses <legacyBold>SQLGetFunctions</legacyBold> to determine if a driver supports <legacyBold>SQLTables</legacyBold>, <legacyBold>SQLColumns</legacyBold>, and <legacyBold>SQLStatistics</legacyBold>. If the driver does not support these functions, the application disconnects from the driver. The first example calls <legacyBold>SQLGetFunctions</legacyBold> once for each function.</para>
      <code>SQLUSMALLINT TablesExists, ColumnsExists, StatisticsExists;
RETCODE retcodeTables, retcodeColumns, retcodeStatistics

retcodeTables = SQLGetFunctions(hdbc, SQL_API_SQLTABLES, &amp;TablesExists);
retcodeColumns = SQLGetFunctions(hdbc, SQL_API_SQLCOLUMNS, &amp;ColumnsExists);
retcodeStatistics = SQLGetFunctions(hdbc, SQL_API_SQLSTATISTICS, &amp;StatisticsExists);

// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.
if (retcodeTables == SQL_SUCCESS &amp;&amp; TablesExists == SQL_TRUE &amp;&amp; 
retcodeColumns == SQL_SUCCESS &amp;&amp; ColumnsExists == SQL_TRUE &amp;&amp; 
retcodeStatistics == SQL_SUCCESS &amp;&amp; StatisticsExists == SQL_TRUE) 
{


   // Continue with application

}

SQLDisconnect(hdbc);</code>
      <para>In the second example, an ODBC 3.x application calls <legacyBold>SQLGetFunctions</legacyBold> and passes it an array in which <legacyBold>SQLGetFunctions</legacyBold> returns information about all ODBC 3.x and earlier functions.</para>
      <code>RETCODE retcodeTables, retcodeColumns, retcodeStatistics
SQLUSMALLINT fExists[SQL_API_ODBC3_ALL_FUNCTIONS_SIZE];

retcode = SQLGetFunctions(hdbc, SQL_API_ODBC3_ALL_FUNCTIONS, fExists);

// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.
if (reccode == SQL_SUCCESS &amp;&amp; 
SQL_FUNC_EXISTS(fExists, SQL_API_SQLTABLES) == SQL_TRUE &amp;&amp;
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLCOLUMNS) == SQL_TRUE &amp;&amp;
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLSTATISTICS) == SQL_TRUE) 
{

   // Continue with application

}


SQLDisconnect(hdbc);</code>
      <para>The third example is an ODBC 2.x application calls <unmanagedCodeEntityReference>SQLGetFunctions</unmanagedCodeEntityReference> and passes it an array of 100 elements in which <unmanagedCodeEntityReference>SQLGetFunctions</unmanagedCodeEntityReference> returns information about all ODBC 2.x and earlier functions. </para>
      <code>#define FUNCTIONS 100

RETCODE retcodeTables, retcodeColumns, retcodeStatistics
SQLUSMALLINT fExists[FUNCTIONS];

retcode = SQLGetFunctions(hdbc, SQL_API_ALL_FUNCTIONS, fExists);

/* SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver. */
if (retcode == SQL_SUCCESS &amp;&amp; 
fExists[SQL_API_SQLTABLES] == SQL_TRUE &amp;&amp;
   fExists[SQL_API_SQLCOLUMNS] == SQL_TRUE &amp;&amp;
   fExists[SQL_API_SQLSTATISTICS] == SQL_TRUE) 
{

   /* Continue with application */

}

SQLDisconnect(hdbc);</code>
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
              <para>Returning the setting of a connection attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning information about a driver or data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the setting of a statement attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr Function</legacyLink>
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