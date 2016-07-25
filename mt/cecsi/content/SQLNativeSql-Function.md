---
title: "SQLNativeSql Function"
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
  - SQLNativeSql
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: b8efc247-27ab-4a00-92b6-1400785783fe
caps.latest.revision: 23
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLNativeSql Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: ODBC</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLNativeSql</legacyBold> returns the SQL string as modified by the driver. <legacyBold>SQLNativeSql</legacyBold> does not execute the SQL statement.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLNativeSql</legacyBold>(
     SQLHDBC        <parameterReference>ConnectionHandle</parameterReference>,
     SQLCHAR *      <parameterReference>InStatementText</parameterReference>,
     SQLINTEGER     <parameterReference>TextLength1</parameterReference>,
     SQLCHAR *      <parameterReference>OutStatementText</parameterReference>,
     SQLINTEGER     <parameterReference>BufferLength</parameterReference>,
     SQLINTEGER *   <parameterReference>TextLength2Ptr</parameterReference>);</legacySyntax>
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
          <legacyItalic>InStatementText</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] SQL text string to be translated.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TextLength1</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of *<legacyItalic>InStatementText</legacyItalic> text string.</para>
        </definition>
        <definedTerm>
          <legacyItalic>OutStatementText</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the translated SQL string.</para>
          <para>If <legacyItalic>OutStatementText</legacyItalic> is NULL, <legacyItalic>TextLength2Ptr</legacyItalic> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>OutStatementText</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Number of characters in the *<legacyItalic>OutStatementText</legacyItalic> buffer. If the value returned in <legacyItalic>*InStatementText</legacyItalic> is a Unicode string (when calling <legacyBold>SQLNativeSqlW</legacyBold>), the <legacyItalic>BufferLength</legacyItalic> argument must be an even number. </para>
        </definition>
        <definedTerm>
          <legacyItalic>TextLength2Ptr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of characters (excluding null-termination) available to return in *<legacyItalic>OutStatementText</legacyItalic>. If the number of characters available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the translated SQL string in *<legacyItalic>OutStatementText</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character.</para>
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
      <para>When <legacyBold>SQLNativeSql</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>ConnectionHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLNativeSql </legacyBold>and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The buffer *<legacyItalic>OutStatementText</legacyItalic> was not large enough to return the entire SQL string, so the SQL string was truncated. The length of the untruncated SQL string is returned in *<legacyItalic>TextLength2Ptr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>08003</para>
            </TD>
            <TD>
              <para>Connection not open</para>
            </TD>
            <TD>
              <para>The <legacyItalic>ConnectionHandle</legacyItalic> was not in a connected state.</para>
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
              <para>22007</para>
            </TD>
            <TD>
              <para>Invalid datetime format</para>
            </TD>
            <TD>
              <para>*<legacyItalic>InStatementText</legacyItalic> contained an escape clause with an invalid date, time, or timestamp value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>Invalid cursor state</para>
            </TD>
            <TD>
              <para>The cursor referred to in the statement was positioned before the start of the result set or after the end of the result set. This error may not be returned by a driver having a native DBMS cursor implementation.</para>
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
              <para>HY009</para>
            </TD>
            <TD>
              <para>Invalid use of null pointer</para>
            </TD>
            <TD>
              <para>(DM) *<legacyItalic>InStatementText</legacyItalic> was a null pointer.</para>
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
              <para>(DM) An asynchronously executing function was called for the <parameterReference>ConnectionHandle</parameterReference> and was still executing when this function was called.</para>
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
              <para>(DM) The argument <legacyItalic>TextLength1</legacyItalic> was less than 0, but not equal to SQL_NTS. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>(DM) The argument <legacyItalic>BufferLength</legacyItalic> was less than 0 and the argument <legacyItalic>OutStatementText</legacyItalic> was not a null pointer.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY109</para>
            </TD>
            <TD>
              <para>Invalid cursor position</para>
            </TD>
            <TD>
              <para>The current row of the cursor had been deleted or had not been fetched. This error may not be returned by a driver having a native DBMS cursor implementation.</para>
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
              <para>(DM) The driver associated with the <legacyItalic>ConnectionHandle</legacyItalic> does not support the function.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>The following are examples of what <legacyBold>SQLNativeSql</legacyBold> might return for the following input SQL string containing the scalar function CONVERT. Assume that the column empid is of type INTEGER in the data source:</para>
      <code>SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee</code>
      <para>A driver for Microsoft SQL Server might return the following translated SQL string:</para>
      <code>SELECT convert (smallint, empid) FROM employee</code>
      <para>A driver for ORACLE Server might return the following translated SQL string:</para>
      <code>SELECT to_number (empid) FROM employee</code>
      <para>A driver for Ingres might return the following translated SQL string:</para>
      <code>SELECT int2 (empid) FROM employee</code>
      <para>For more information, see <legacyLink xlink:href="dd00a535-b136-494f-913b-410838e3de7e">Direct Execution</legacyLink> and <legacyLink xlink:href="f08c8a98-31ee-48b2-9dbf-6f31c2166dbb">Prepared Execution</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Related Functions</title>
    <content>
      <para>None.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>