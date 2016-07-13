---
title: SQLPutData Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLPutData
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 9a60f004-1477-4c54-a20c-7378e1116713
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLPutData Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: ISO 92 </para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLPutData</legacyBold> allows an application to send data for a parameter or column to the driver at statement execution time. This function can be used to send character or binary data values in parts to a column with a character, binary, or data source–specific data type (for example, parameters of the SQL_LONGVARBINARY or SQL_LONGVARCHAR types). <legacyBold>SQLPutData</legacyBold> supports binding to a Unicode C data type, even if the underlying driver does not support Unicode data.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLPutData</legacyBold>(
      SQLHSTMT     <parameterReference>StatementHandle</parameterReference>,
      SQLPOINTER   <parameterReference>DataPtr</parameterReference>,
      SQLLEN       <parameterReference>StrLen_or_Ind</parameterReference>);</legacySyntax>
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
          <legacyItalic>DataPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to a buffer containing the actual data for the parameter or column. The data must be in the C data type specified in the <legacyItalic>ValueType</legacyItalic> argument of <legacyBold>SQLBindParameter</legacyBold> (for parameter data) or the <legacyItalic>TargetType</legacyItalic> argument of <legacyBold>SQLBindCol</legacyBold> (for column data).</para>
        </definition>
        <definedTerm>
          <legacyItalic>StrLen_or_Ind</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>DataPtr</legacyItalic>. Specifies the amount of data sent in a call to <legacyBold>SQLPutData</legacyBold>. The amount of data can vary with each call for a given parameter or column. <legacyItalic>StrLen_or_Ind</legacyItalic> is ignored unless it meets one of the following conditions: </para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyItalic>StrLen_or_Ind</legacyItalic> is SQL_NTS, SQL_NULL_DATA, or SQL_DEFAULT_PARAM.</para>
            </listItem>
            <listItem>
              <para>The C data type specified in <legacyBold>SQLBindParameter</legacyBold> or <legacyBold>SQLBindCol</legacyBold> is SQL_C_CHAR or SQL_C_BINARY. </para>
            </listItem>
            <listItem>
              <para>The C data type is SQL_C_DEFAULT, and the default C data type for the specified SQL data type is SQL_C_CHAR or SQL_C_BINARY. </para>
            </listItem>
          </list>
          <para>For all other types of C data, if <legacyItalic>StrLen_or_Ind</legacyItalic> is not SQL_NULL_DATA or SQL_DEFAULT_PARAM, the driver assumes that the size of the *<legacyItalic>DataPtr</legacyItalic> buffer is the size of the C data type specified with <legacyItalic>ValueType</legacyItalic> or <legacyItalic>TargetType</legacyItalic> and sends the entire data value. For more information, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink> in Appendix D: Data Types.</para>
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
      <para>When <legacyBold>SQLPutData</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLPutData</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>String or binary data returned for an output parameter resulted in the truncation of nonblank character or non-NULL binary data. If it was a string value, it was right-truncated. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07006</para>
            </TD>
            <TD>
              <para>Restricted data type  attribute violation</para>
            </TD>
            <TD>
              <para>The data value identified by the <legacyItalic>ValueType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold> for the bound parameter could not be converted to the data type identified by the <legacyItalic>ParameterType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07S01</para>
            </TD>
            <TD>
              <para>Invalid use of default parameter</para>
            </TD>
            <TD>
              <para>A parameter value, set with <legacyBold>SQLBindParameter</legacyBold>, was SQL_DEFAULT_PARAM, and the corresponding parameter did not have a default value.</para>
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
              <para>String data, right truncation</para>
            </TD>
            <TD>
              <para>The assignment of a character or binary value to a column resulted in the truncation of nonblank (character) or non-null (binary) characters or bytes. </para>
              <para>The SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold> was "Y", and more data was sent for a long parameter (the data type was SQL_LONGVARCHAR, SQL_LONGVARBINARY, or a long data source–specific data type) than was specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
              <para>The SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold> was "Y", and more data was sent for a long column (the data type was SQL_LONGVARCHAR, SQL_LONGVARBINARY, or a long data source–specific data type) than was specified in the length buffer corresponding to a column in a row of data that was added or updated with <legacyBold>SQLBulkOperations</legacyBold> or updated with <legacyBold>SQLSetPos</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22003</para>
            </TD>
            <TD>
              <para>Numeric value out of range</para>
            </TD>
            <TD>
              <para>The data sent for a bound numeric parameter or column caused the whole (as opposed to fractional) part of the number to be truncated when assigned to the associated table column.</para>
              <para>Returning a numeric value (as numeric or string) for one or more input/output or output parameters would have caused the whole (as opposed to fractional) part of the number to be truncated.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22007</para>
            </TD>
            <TD>
              <para>Invalid datetime format</para>
            </TD>
            <TD>
              <para>The data sent for a parameter or column that was bound to a date, time, or timestamp structure was, respectively, an invalid date, time, or timestamp.</para>
              <para>An input/output or output parameter was bound to a date, time, or timestamp C structure, and a value in the returned parameter was, respectively, an invalid date, time, or timestamp. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22008</para>
            </TD>
            <TD>
              <para>Datetime field overflow</para>
            </TD>
            <TD>
              <para>A datetime expression computed for an input/output or output parameter resulted in a date, time, or timestamp C structure that was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22012</para>
            </TD>
            <TD>
              <para>Division by zero</para>
            </TD>
            <TD>
              <para>An arithmetic expression calculated for an input/output or output parameter resulted in division by zero.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22015</para>
            </TD>
            <TD>
              <para>Interval field overflow</para>
            </TD>
            <TD>
              <para>The data sent for an exact numeric or interval column or parameter to an interval SQL data type caused a loss of significant digits. </para>
              <para>Data was sent for an interval column or parameter with more than one field, was converted to a numeric data type, and had no representation in the numeric data type. </para>
              <para>The data sent for column or parameter data was assigned to an interval SQL type, and there was no representation of the value of the C type in the interval SQL type. </para>
              <para>The data sent for an exact numeric or interval C column or parameter to an interval C type caused a loss of significant digits. </para>
              <para>The data sent for column or parameter data was assigned to an interval C structure, and there was no representation of the data in the interval data structure.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22018</para>
            </TD>
            <TD>
              <para>Invalid character value for cast specification</para>
            </TD>
            <TD>
              <para>The C type was an exact or approximate numeric, a datetime, or an interval data type; the SQL type of the column was a character data type; and the value in the column or parameter was not a valid literal of the bound C type. </para>
              <para>The SQL type was an exact or approximate numeric, a datetime, or an interval data type; the C type was SQL_C_CHAR; and the value in the column or parameter was not a valid literal of the bound SQL type.</para>
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
              <para>HY009</para>
            </TD>
            <TD>
              <para>Invalid use of null pointer</para>
            </TD>
            <TD>
              <para>(DM) The argument <legacyItalic>DataPtr</legacyItalic> was a null pointer, and the argument <legacyItalic>StrLen_or_Ind</legacyItalic> was not 0, SQL_DEFAULT_PARAM, or SQL_NULL_DATA.</para>
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
              <para>(DM) The previous function call was not a call to <legacyBold>SQLPutData</legacyBold> or <legacyBold>SQLParamData</legacyBold>.</para>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the SQLPutData function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
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
              <para>HY019</para>
            </TD>
            <TD>
              <para>Non-character and non-binary data sent in pieces</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLPutData</legacyBold> was called more than once for a parameter or column, and it was not being used to send character C data to a column with a character, binary, or data source–specific data type or to send binary C data to a column with a character, binary, or data source–specific data type.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY020</para>
            </TD>
            <TD>
              <para>Attempt to concatenate a null value</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLPutData</legacyBold> was called more than once since the call that returned SQL_NEED_DATA, and in one of those calls, the <legacyItalic>StrLen_or_Ind</legacyItalic> argument contained SQL_NULL_DATA or SQL_DEFAULT_PARAM.</para>
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
              <para>The argument <legacyItalic>DataPtr</legacyItalic> was not a null pointer, and the argument <legacyItalic>StrLen_or_Ind</legacyItalic> was less than 0 but not equal to SQL_NTS or SQL_NULL_DATA.</para>
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
      <para>If <legacyBold>SQLPutData</legacyBold> is called while sending data for a parameter in an SQL statement, it can return any SQLSTATE that can be returned by the function called to execute the statement (<legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>). If it is called while sending data for a column being updated or added with <legacyBold>SQLBulkOperations</legacyBold> or being updated with <legacyBold>SQLSetPos</legacyBold>, it can return any SQLSTATE that can be returned by <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>.</para>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLPutData</legacyBold> can be called to supply data-at-execution data for two uses: parameter data to be used in a call to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>, or column data to be used when a row is updated or added by a call to <legacyBold>SQLBulkOperations</legacyBold> or is updated by a call to <legacyBold>SQLSetPos</legacyBold>.</para>
      <para>When an application calls <legacyBold>SQLParamData</legacyBold> to determine which data it should send, the driver returns an indicator that the application can use to determine which parameter data to send or where column data can be found. It also returns SQL_NEED_DATA, which is an indicator to the application that it should call <legacyBold>SQLPutData</legacyBold> to send the data. In the <legacyItalic>DataPtr</legacyItalic> argument to <legacyBold>SQLPutData</legacyBold>, the application passes a pointer to the buffer containing the actual data for the parameter or column. </para>
      <para>When the driver returns SQL_SUCCESS for <legacyBold>SQLPutData</legacyBold>, the application calls <legacyBold>SQLParamData</legacyBold> again. <legacyBold>SQLParamData</legacyBold> returns SQL_NEED_DATA if more data needs to be sent, in which case the application calls <legacyBold>SQLPutData</legacyBold> again. It returns SQL_SUCCESS if all data-at-execution data has been sent. The application then calls <legacyBold>SQLParamData</legacyBold> again. If the driver returns SQL_NEED_DATA and another indicator in <legacyItalic>*ValuePtrPtr</legacyItalic>, it requires data for another parameter or column and <legacyBold>SQLPutData</legacyBold> is called again. If the driver returns SQL_SUCCESS, then all data-at-execution data has been sent and the SQL statement can be executed or the <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> call can be processed.</para>
      <para>For more information on how data-at-execution parameter data is passed at statement execution time, see "Passing Parameter Values" in <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink> and <legacyLink xlink:href="ea989084-a8e6-4737-892e-9ec99dd49caf">Sending Long Data</legacyLink>. For more information on how data-at-execution column data is updated or added, see the section "Using SQLSetPos" in <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>, "Performing Bulk Updates Using Bookmarks" in <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations</legacyLink>, and <legacyLink xlink:href="e2fdf842-5e4c-46ca-bb21-4625c3324f28">Long Data and SQLSetPos and SQLBulkOperations</legacyLink>.</para>
      <alert class="note">
        <para>An application can use <legacyBold>SQLPutData</legacyBold> to send data in parts only when sending character C data to a column with a character, binary, or data source–specific data type or when sending binary C data to a column with a character, binary, or data source–specific data type. If <legacyBold>SQLPutData</legacyBold> is called more than once under any other conditions, it returns SQL_ERROR and SQLSTATE HY019 (Non-character and non-binary data sent in pieces).</para>
      </alert>
    </content>
  </section>
  <codeExample>
    <description>
      <content>
        <para>The following sample assumes a data source name called Test. The associated database should have a table that you can create, as follows:</para>
        <code>CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)</code>
      </content>
    </description>
    <code>// SQLPutData.cpp
// compile with: odbc32.lib user32.lib
#include &lt;stdio.h&gt;
#include &lt;windows.h&gt;
#include &lt;sqlext.h&gt;
#include &lt;odbcss.h&gt;

#define TEXTSIZE  12000
#define MAXBUFLEN 256

SQLHENV henv = SQL_NULL_HENV;
SQLHDBC hdbc1 = SQL_NULL_HDBC;     
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;

void Cleanup() {
   if (hstmt1 != SQL_NULL_HSTMT)
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);

   if (hdbc1 != SQL_NULL_HDBC) {
      SQLDisconnect(hdbc1);
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);
   }

   if (henv != SQL_NULL_HENV)
      SQLFreeHandle(SQL_HANDLE_ENV, henv);
}

int main() {
   RETCODE retcode;

   // SQLBindParameter variables.
   SQLLEN cbTextSize, lbytes;

   // SQLParamData variable.
   PTR pParmID;

   // SQLPutData variables.
   UCHAR  Data[] = 
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
      "abcdefghijklmnopqrstuvwxyz";

   SDWORD cbBatch = (SDWORD)sizeof(Data) - 1;

   // Allocate the ODBC environment and save handle.
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &amp;henv);
   if ( (retcode != SQL_SUCCESS_WITH_INFO) &amp;&amp; (retcode != SQL_SUCCESS)) {
      printf("SQLAllocHandle(Env) Failed\n\n");
      Cleanup();
      return(9);
   }

   // Notify ODBC that this is an ODBC 3.0 app.
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);
   if ( (retcode != SQL_SUCCESS_WITH_INFO) &amp;&amp; (retcode != SQL_SUCCESS)) {
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");
      Cleanup();
      return(9);    
   }

   // Allocate ODBC connection handle and connect.
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc1);
   if ( (retcode != SQL_SUCCESS_WITH_INFO) &amp;&amp; (retcode != SQL_SUCCESS)) {
      printf("SQLAllocHandle(hdbc1) Failed\n\n");
      Cleanup();
      return(9);
   }

   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication. 
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);
   if ( (retcode != SQL_SUCCESS) &amp;&amp; (retcode != SQL_SUCCESS_WITH_INFO) ) {
      printf("SQLConnect() Failed\n\n");
      Cleanup();
      return(9);
   }

   // Allocate statement handle.
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &amp;hstmt1);
   if ( (retcode != SQL_SUCCESS) &amp;&amp; (retcode != SQL_SUCCESS_WITH_INFO) ) {
      printf("SQLAllocHandle(hstmt1) Failed\n\n");
      Cleanup();
      return(9);
   }

   // Set parameters based on total data to send.
   lbytes = (SDWORD)TEXTSIZE;
   cbTextSize = SQL_LEN_DATA_AT_EXEC(lbytes);

   // Bind the parameter marker.
   retcode = SQLBindParameter (hstmt1,           // hstmt
                               1,                // ipar
                               SQL_PARAM_INPUT,  // fParamType
                               SQL_C_CHAR,       // fCType
                               SQL_LONGVARCHAR,  // FSqlType
                               lbytes,           // cbColDef
                               0,                // ibScale
                               (VOID *)1,        // rgbValue
                               0,                // cbValueMax
                               &amp;cbTextSize);     // pcbValue

   if ( (retcode != SQL_SUCCESS) &amp;&amp; (retcode != SQL_SUCCESS_WITH_INFO) ) {
      printf("SQLBindParameter Failed\n\n");
      Cleanup();
      return(9);
   }

   // Execute the command.
   retcode = 
      SQLExecDirect(hstmt1, (UCHAR*)"INSERT INTO emp4 VALUES('Paul Borm', 46,'1950-11-12 00:00:00', ?)", SQL_NTS);
   if ( (retcode != SQL_SUCCESS) &amp;&amp; (retcode != SQL_NEED_DATA) &amp;&amp; (retcode != SQL_SUCCESS_WITH_INFO) ) {
      printf("SQLExecDirect Failed\n\n");
      Cleanup();
      return(9);
   }

   // Check to see if NEED_DATA; if yes, use SQLPutData.
   retcode = SQLParamData(hstmt1, &amp;pParmID);
   if (retcode == SQL_NEED_DATA) {
      while (lbytes &gt; cbBatch) {
         SQLPutData(hstmt1, Data, cbBatch);
         lbytes -= cbBatch;
      }
      // Put final batch.
      retcode = SQLPutData(hstmt1, Data, lbytes); 
   }

   if ( (retcode != SQL_SUCCESS) &amp;&amp; (retcode != SQL_SUCCESS_WITH_INFO) ) {
      printf("SQLParamData Failed\n\n");
      Cleanup();
      return(9);
   }

   // Make final SQLParamData call.
   retcode = SQLParamData(hstmt1, &amp;pParmID);
   if ( (retcode != SQL_SUCCESS) &amp;&amp; (retcode != SQL_SUCCESS_WITH_INFO) ) {
      printf("Final SQLParamData Failed\n\n");
      Cleanup();
      return(9);
   }

   // Clean up.
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);
   SQLDisconnect(hdbc1);
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);
   SQLFreeHandle(SQL_HANDLE_ENV, henv);
}</code>
  </codeExample>
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
                <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter Function</legacyLink>  </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Canceling statement processing</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel Function</legacyLink>  </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing an SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect Function</legacyLink>  </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing a prepared SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute Function</legacyLink>  </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the next parameter to send data for</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="68fe010d-9539-4e5b-a260-c8d32423b1db">SQLParamData Function</legacyLink>  </para>
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