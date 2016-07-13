---
title: SQLSetCursorName Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLSetCursorName
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 4e055946-12d4-4589-9891-41617a50f34e
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetCursorName Function
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
          <legacyBold>SQLSetCursorName</legacyBold> associates a cursor name with an active statement. If an application does not call <legacyBold>SQLSetCursorName</legacyBold>, the driver generates cursor names as needed for SQL statement processing.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLSetCursorName</legacyBold>(
     SQLHSTMT      <parameterReference>StatementHandle</parameterReference>,
     SQLCHAR *     <parameterReference>CursorName</parameterReference>,
     SQLSMALLINT   <parameterReference>NameLength</parameterReference>);</legacySyntax>
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
          <legacyItalic>CursorName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Cursor name. For efficient processing, the cursor name should not include any leading or trailing spaces in the cursor name, and if the cursor name includes a delimited identifier, the delimiter should be positioned as the first character in the cursor name.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of *<legacyItalic>CursorName</legacyItalic>.</para>
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
      <para>When <legacyBold>SQLSetCursorName</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLSetCursorName</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The cursor name exceeded the maximum limit, so only the maximum allowable number of characters was used.</para>
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
              <para>The statement corresponding to <legacyItalic>StatementHandle</legacyItalic> was already in an executed or cursor-positioned state.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>34000</para>
            </TD>
            <TD>
              <para>Invalid cursor name</para>
            </TD>
            <TD>
              <para>The cursor name specified in *<legacyItalic>CursorName</legacyItalic> was invalid because it exceeded the maximum length as defined by the driver, or it started with "SQLCUR" or "SQL_CUR."</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>3C000</para>
            </TD>
            <TD>
              <para>Duplicate cursor name</para>
            </TD>
            <TD>
              <para>The cursor name specified in *<legacyItalic>CursorName</legacyItalic> already exists.</para>
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
              <para>(DM) The argument <legacyItalic>CursorName</legacyItalic> was a null pointer.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This aynchronous function was still executing when the <unmanagedCodeEntityReference>SQLSetCursorName</unmanagedCodeEntityReference> function was called.</para>
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
              <para>HY090</para>
            </TD>
            <TD>
              <para>Invalid string or buffer length</para>
            </TD>
            <TD>
              <para>(DM) The argument <legacyItalic>NameLength</legacyItalic> was less than 0 but not equal to SQL_NTS.</para>
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
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>Cursor names are used only in positioned update and delete statements (for example, <legacyBold>UPDATE</legacyBold> <legacyItalic>table-name</legacyItalic> ...<legacyBold>WHERE CURRENT OF</legacyBold> <legacyItalic>cursor-name</legacyItalic>). For more information, see <legacyLink xlink:href="0eafba50-02c7-46ca-a439-ef3307b935dc">Positioned Update and Delete Statements</legacyLink>. If the application does not call <legacyBold>SQLSetCursorName</legacyBold> to define a cursor name, on execution of a query statement the driver generates a name that begins with the letters SQL_CUR and does not exceed 18 characters in length.</para>
      <para>All cursor names within the connection must be unique. The maximum length of a cursor name is defined by the driver. For maximum interoperability, it is recommended that applications limit cursor names to no more than 18 characters. In ODBC 3<legacyItalic>.x</legacyItalic>, if a cursor name is a quoted identifier, it is treated in a case-sensitive manner and it can contain characters that the syntax of SQL would not permit or would treat specially, such as blanks or reserved keywords. If a cursor name must be treated in a case-sensitive manner, it must be passed as a quoted identifier.</para>
      <para>A cursor name that is set either explicitly or implicitly remains set until the statement with which it is associated is dropped, using <legacyBold>SQLFreeHandle</legacyBold>. <legacyBold>SQLSetCursorName</legacyBold> can be called to rename a cursor on a statement as long as the cursor is in an allocated or prepared state.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>In the following example, an application uses <legacyBold>SQLSetCursorName</legacyBold> to set a cursor name for a statement. It then uses that statement to retrieve results from the CUSTOMERS table. Finally, it performs a positioned update to change the phone number of John Smith. Note that the application uses different statement handles for the <legacyBold>SELECT</legacyBold> and <legacyBold>UPDATE</legacyBold> statements.</para>
      <para>For another code example, see <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>.</para>
      <code>#define NAME_LEN 50
#define PHONE_LEN 10

SQLHSTMT     hstmtSelect,
SQLHSTMT     hstmtUpdate;
SQLRETURN    retcode;
SQLHDBC      hdbc;
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];
SQLINTEGER   cbName, cbPhone;

/* Allocate the statements and set the cursor name. */

SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmtSelect);
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmtUpdate);
SQLSetCursorName(hstmtSelect, "C1", SQL_NTS);

/* SELECT the result set and bind its columns to local buffers. */

SQLExecDirect(hstmtSelect,
      "SELECT NAME, PHONE FROM CUSTOMERS",
      SQL_NTS);
SQLBindCol(hstmtSelect, 1, SQL_C_CHAR, szName, NAME_LEN, &amp;cbName);
SQLBindCol(hstmtSelect, 2, SQL_C_CHAR, szPhone, PHONE_LEN, &amp;cbPhone);

/* Read through the result set until the cursor is */
/* positioned on the row for John Smith. */

do
 retcode = SQLFetch(hstmtSelect);
while ((retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) &amp;&amp;
   (strcmp(szName, "Smith, John") != 0));

/* Perform a positioned update of John Smith's name. */

if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
   SQLExecDirect(hstmtUpdate,
   "UPDATE EMPLOYEE SET PHONE=\"2064890154\" WHERE CURRENT OF C1",
   SQL_NTS);
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
              <para>Returning a cursor name</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e6e92199-7bb6-447c-8987-049a4c6ce05d">SQLGetCursorName Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting cursor scrolling options</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="2a825ba7-7942-4c23-bcdb-c80dc12f8c86">SQLSetScrollOptions Function</legacyLink>
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