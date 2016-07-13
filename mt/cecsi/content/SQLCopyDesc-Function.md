---
title: SQLCopyDesc Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLCopyDesc
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLCopyDesc Function
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
          <legacyBold>SQLCopyDesc</legacyBold> copies descriptor information from one descriptor handle to another.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLCopyDesc</legacyBold>(
     SQLHDESC     <parameterReference>SourceDescHandle</parameterReference>,
     SQLHDESC     <parameterReference>TargetDescHandle</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>SourceDescHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Source descriptor handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TargetDescHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Target descriptor handle. The <legacyItalic>TargetDescHandle</legacyItalic> argument can be a handle to an application descriptor or an IPD. <legacyItalic>TargetDescHandle</legacyItalic> cannot be set to a handle to an IRD, or<legacyBold> SQLCopyDesc</legacyBold> will return SQLSTATE HY016 (Cannot modify an implementation row descriptor).</para>
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
      <para>When <legacyBold>SQLCopyDesc</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DESC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>TargetDescHandle</legacyItalic>. If an invalid <legacyItalic>SourceDescHandle</legacyItalic> was passed in the call, SQL_INVALID_HANDLE will be returned but no SQLSTATE will be returned. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLCopyDesc</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
      <para>When an error is returned, the call to <legacyBold>SQLCopyDesc</legacyBold> is immediately aborted, and the contents of the fields in the <legacyItalic>TargetDescHandle</legacyItalic> descriptor are undefined.</para>
      <para>Because <legacyBold>SQLCopyDesc</legacyBold> may be implemented by calling <legacyBold>SQLGetDescField</legacyBold> and <legacyBold>SQLSetDescField</legacyBold>, <legacyBold>SQLCopyDesc</legacyBold> may return SQLSTATEs returned by <legacyBold>SQLGetDescField</legacyBold> or <legacyBold>SQLSetDescField</legacyBold>.</para>
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
              <para>Memory allocation error</para>
            </TD>
            <TD>
              <para>The driver was unable to allocate the memory required to support execution or completion of the function.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY007</para>
            </TD>
            <TD>
              <para>Associated statement is not prepared</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>SourceDescHandle</legacyItalic> was associated with an IRD, and the associated statement handle was not in the prepared or executed state.</para>
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
              <para>(DM) The descriptor handle in <legacyItalic>SourceDescHandle</legacyItalic> or <legacyItalic>TargetDescHandle</legacyItalic> was associated with a <legacyItalic>StatementHandle</legacyItalic> for which an asynchronously executing function (not this one) was called and was still executing when this function was called.</para>
              <para>(DM) The descriptor handle in <legacyItalic>SourceDescHandle</legacyItalic> or <legacyItalic>TargetDescHandle</legacyItalic> was associated with a <legacyItalic>StatementHandle</legacyItalic> for which <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <parameterReference>SourceDescHandle</parameterReference> or <parameterReference>TargetDescHandle</parameterReference>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLCopyDesc</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for one of the statement handles associated with the <parameterReference>SourceDescHandle</parameterReference> or <parameterReference>TargetDescHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
              <para>
                <legacyItalic>TargetDescHandle</legacyItalic> was associated with an IRD.</para>
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
              <para>The descriptor information checked during a consistency check was not consistent. For more information, see "Consistency Checks" in <legacyBold>SQLSetDescField</legacyBold>.</para>
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
              <para>The call to <legacyBold>SQLCopyDesc</legacyBold> prompted a call to <legacyBold>SQLSetDescField</legacyBold>, but <legacyItalic>*ValuePtr</legacyItalic> was not valid for the <legacyItalic>FieldIdentifier</legacyItalic> argument on <legacyItalic>TargetDescHandle</legacyItalic>.</para>
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
              <para>(DM) The driver associated with the <legacyItalic>SourceDescHandle</legacyItalic> or <legacyItalic>TargetDescHandle</legacyItalic> does not support the function.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>A call to <legacyBold>SQLCopyDesc</legacyBold> copies the fields of the source descriptor handle to the target descriptor handle. Fields can be copied only to an application descriptor or an IPD, but not to an IRD. Fields can be copied from either an application or an implementation descriptor. </para>
      <para>Fields can be copied from an IRD only if the statement handle is in the prepared or executed state; otherwise, the function returns SQLSTATE HY007 (Associated statement is not prepared). </para>
      <para>Fields can be copied from an IPD whether or not a statement has been prepared. If an SQL statement with dynamic parameters has been prepared and automatic population of the IPD is supported and enabled, then the IPD is populated by the driver. When <legacyBold>SQLCopyDesc</legacyBold> is called with the IPD as the <legacyItalic>SourceDescHandle</legacyItalic>, the populated fields are copied. If the IPD is not populated by the driver, the contents of the fields originally in the IPD are copied.</para>
      <para>All fields of the descriptor, except SQL_DESC_ALLOC_TYPE (which specifies whether the descriptor handle was automatically or explicitly allocated), are copied, whether or not the field is defined for the destination descriptor. Copied fields overwrite the existing fields.</para>
      <para>The driver copies all descriptor fields if the <legacyItalic>SourceDescHandle</legacyItalic> and <legacyItalic>TargetDescHandle</legacyItalic> arguments are associated with the same driver, even if the drivers are on two different connections or environments. If the <legacyItalic>SourceDescHandle</legacyItalic> and <legacyItalic>TargetDescHandle</legacyItalic> arguments are associated with different drivers, the Driver Manager copies ODBC-defined fields, but does not copy driver-defined fields or fields that are not defined by ODBC for the type of descriptor.</para>
      <para>The call to<legacyBold> SQLCopyDesc</legacyBold> is aborted immediately if an error occurs. </para>
      <para>When the SQL_DESC_DATA_PTR field is copied, a consistency check is performed on the target descriptor. If the consistency check fails, SQLSTATE HY021 (Inconsistent descriptor information) is returned and the call to <legacyBold>SQLCopyDesc</legacyBold> is immediately aborted. For more information on consistency checks, see "Consistency Checks" in <legacyLink xlink:href="bf55256c-7eb7-4e3f-97ef-b0fee09ba829">SQLSetDescRec Function</legacyLink>.</para>
      <para>Descriptor handles can be copied across connections even if the connections are under different environments. If the Driver Manager detects that the source and the destination descriptor handles do not belong to the same connection and the two connections belong to separate drivers, it implements <legacyBold>SQLCopyDesc</legacyBold> by performing a field-by-field copy using <legacyBold>SQLGetDescField</legacyBold> and <legacyBold>SQLSetDescField</legacyBold>.</para>
      <para>When <legacyBold>SQLCopyDesc</legacyBold> is called with a <legacyItalic>SourceDescHandle</legacyItalic> on one driver and a <legacyItalic>TargetDescHandle</legacyItalic> on another driver, the error queue of the <legacyItalic>SourceDescHandle</legacyItalic> is cleared. This occurs because <legacyBold>SQLCopyDesc</legacyBold> in this case is implemented by calls to <legacyBold>SQLGetDescField</legacyBold> and <legacyBold>SQLSetDescField</legacyBold>.</para>
      <alert class="note">
        <para>An application might be able to associate an explicitly allocated descriptor handle with a <legacyItalic>StatementHandle</legacyItalic>, rather than calling <legacyBold>SQLCopyDesc</legacyBold> to copy fields from one descriptor to another. An explicitly allocated descriptor can be associated with another <legacyItalic>StatementHandle</legacyItalic> on the same <legacyItalic>ConnectionHandle</legacyItalic> by setting the SQL_ATTR_APP_ROW_DESC or SQL_ATTR_APP_PARAM_DESC statement attribute to the handle of the explicitly allocated descriptor. When this is done, <legacyBold>SQLCopyDesc</legacyBold> does not have to be called to copy descriptor field values from one descriptor to another. A descriptor handle cannot be associated with a <legacyItalic>StatementHandle</legacyItalic> on another <legacyItalic>ConnectionHandle</legacyItalic>, however; to use the same descriptor field values on <legacyItalic>StatementHandles</legacyItalic> on different <legacyItalic>ConnectionHandles</legacyItalic>, <legacyBold>SQLCopyDesc</legacyBold> has to be called.</para>
      </alert>
      <para>For a description of the fields in a descriptor header or record, see <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField Function</legacyLink>. For more information on descriptors, see <legacyLink xlink:href="ef2cbb93-cd00-40f8-b1d2-5f5723a991aa">Descriptors</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Copying Rows Between Tables</title>
    <content>
      <para>An application may copy data from one table to another without copying the data at the application level. To do this, the application binds the same data buffers and descriptor information to a statement that fetches the data and the statement that inserts the data into a copy. This can be accomplished either by sharing an application descriptor (binding an explicitly allocated descriptor as both the ARD to one statement and the APD in another) or by using <legacyBold>SQLCopyDesc</legacyBold> to copy the bindings between the ARD and the APD of the two statements. If the statements are on different connections, <legacyBold>SQLCopyDesc</legacyBold> must be used. In addition, <legacyBold>SQLCopyDesc</legacyBold> has to be called to copy the bindings between the IRD and the IPD of the two statements. When copying across statements on the same connection, the SQL_ACTIVE_STATEMENTS information type returned by the driver for a call to <legacyBold>SQLGetInfo</legacyBold> must be greater than 1 for this operation to succeed. (This is not the case when copying across connections.)</para>
    </content>
    <sections>
      <section>
        <title>Code Example</title>
        <content>
          <para>In the following example, descriptor operations are used to copy the fields of the PartsSource table into the PartsCopy table. The contents of the PartsSource table are fetched into rowset buffers in <legacyItalic>hstmt0</legacyItalic>. These values are used as parameters of an INSERT statement on <legacyItalic>hstmt1</legacyItalic> to populate the columns of the PartsCopy table. To do so, the fields of the IRD of <legacyItalic>hstmt0</legacyItalic> are copied to the fields of the IPD of <legacyItalic>hstmt1</legacyItalic>, and the fields of the ARD of <legacyItalic>hstmt0</legacyItalic> are copied to the fields of the APD of <legacyItalic>hstmt1</legacyItalic>. Use <legacyBold>SQLSetDescField</legacyBold> to set the IPD’s SQL_DESC_PARAMETER_TYPE attribute to SQL_PARAM_INPUT when you copy IRD fields from a statement with output parameters to IPD fields that need to be input parameters.</para>
          <code>#define ROWS 100
#define DESC_LEN 50
#define SQL_SUCCEEDED(rc) (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO)

// Template for a row
typedef struct {
   SQLINTEGER   sPartID;
   SQLINTEGER   cbPartID;
   SQLUCHAR     szDescription[DESC_LENGTH];
   SQLINTEGER   cbDescription;
   REAL         sPrice;
   SQLINTEGER   cbPrice;
} PartsSource;

PartsSource    rget[ROWS];          // rowset buffer
SQLUSMALLINT   sts_ptr[ROWS];       // status pointer
SQLHSTMT       hstmt0, hstmt1;
SQLHDESC       hArd0, hIrd0, hApd1, hIpd1;

// ARD and IRD of hstmt0
SQLGetStmtAttr(hstmt0, SQL_ATTR_APP_ROW_DESC, &amp;hArd0, 0, NULL);
SQLGetStmtAttr(hstmt0, SQL_ATTR_IMP_ROW_DESC, &amp;hIrd0, 0, NULL);

// APD and IPD of hstmt1
SQLGetStmtAttr(hstmt1, SQL_ATTR_APP_PARAM_DESC, &amp;hApd1, 0, NULL);
SQLGetStmtAttr(hstmt1, SQL_ATTR_IMP_PARAM_DESC, &amp;hIpd1, 0, NULL);

// Use row-wise binding on hstmt0 to fetch rows
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER) sizeof(PartsSource), 0);

// Set rowset size for hstmt0
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);

// Execute a select statement
SQLExecDirect(hstmt0, "SELECT PARTID, DESCRIPTION, PRICE FROM PARTS ORDER BY 3, 1, 2"",
               SQL_NTS);

// Bind
SQLBindCol(hstmt0, 1, SQL_C_SLONG, rget[0].sPartID, 0, 
   &amp;rget[0].cbPartID);
SQLBindCol(hstmt0, 2, SQL_C_CHAR, &amp;rget[0].szDescription, DESC_LEN, 
   &amp;rget[0].cbDescription);
SQLBindCol(hstmt0, 3, SQL_C_FLOAT, rget[0].sPrice, 
   0, &amp;rget[0].cbPrice);

// Perform parameter bindings on hstmt1. 
SQLCopyDesc(hArd0, hApd1);
SQLCopyDesc(hIrd0, hIpd1);

// Set the array status pointer of IRD
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_STATUS_PTR, sts_ptr, SQL_IS_POINTER);

// Set the ARRAY_STATUS_PTR field of APD to be the same
// as that in IRD.
SQLSetStmtAttr(hstmt1, SQL_ATTR_PARAM_OPERATION_PTR, sts_ptr, SQL_IS_POINTER);

// Set the hIpd1 records as input parameters
rc = SQLSetDescField(hIpd1, 1, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);
rc = SQLSetDescField(hIpd1, 2, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);
rc = SQLSetDescField(hIpd1, 3, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);

// Prepare an insert statement on hstmt1. PartsCopy is a copy of
// PartsSource
SQLPrepare(hstmt1, "INSERT INTO PARTS_COPY VALUES (?, ?, ?)", SQL_NTS);

// In a loop, fetch a rowset, and copy the fetched rowset to PARTS_COPY

rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);
while (SQL_SUCCEEDED(rc)) {

   // After the call to SQLFetchScroll, the status array has row 
   // statuses. This array is used as input status in the APD
   // and hence determines which elements of the rowset buffer
   // are inserted.
   SQLExecute(hstmt1);

   rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);
} // while</code>
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
                  <para>Getting multiple descriptor fields</para>
                </TD>
                <TD>
                  <para>
                    <legacyLink xlink:href="325e0907-8e87-44e8-a111-f39e636a9cbc">SQLGetDescRec Function</legacyLink> </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Setting a single descriptor field</para>
                </TD>
                <TD>
                  <para>
                    <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField Function</legacyLink>
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
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>