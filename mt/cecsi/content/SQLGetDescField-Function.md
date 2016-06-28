---
title: SQLGetDescField Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLGetDescField
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: f09ff660-1e4a-4370-be85-90d4da0487d3
translation.priority.ht: 
  - en-gb
---
# SQLGetDescField Function
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
          <legacyBold>SQLGetDescField</legacyBold> returns the current setting or value of a single field of a descriptor record.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetDescField</legacyBold>(
     SQLHDESC        <parameterReference>DescriptorHandle</parameterReference>,
     SQLSMALLINT     <parameterReference>RecNumber</parameterReference>,
     SQLSMALLINT     <parameterReference>FieldIdentifier</parameterReference>,
     SQLPOINTER      <parameterReference>ValuePtr</parameterReference>,
     SQLINTEGER      <parameterReference>BufferLength</parameterReference>,
     SQLINTEGER *    <parameterReference>StringLengthPtr</parameterReference>);</legacySyntax>
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
          <para>[Input] Indicates the descriptor record from which the application seeks information. Descriptor records are numbered from 0, with record number 0 being the bookmark record. If the <legacyItalic>FieldIdentifier</legacyItalic> argument indicates a header field, <legacyItalic>RecNumber</legacyItalic> is ignored. If <legacyItalic>RecNumber</legacyItalic> is less than or equal to SQL_DESC_COUNT but the row does not contain data for a column or parameter, a call to <legacyBold>SQLGetDescField</legacyBold> will return the default values of the fields. (For more information, see "Initialization of Descriptor Fields" in <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.)</para>
        </definition>
        <definedTerm>
          <legacyItalic>FieldIdentifier</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Indicates the field of the descriptor whose value is to be returned. For more information, see the "<legacyItalic>FieldIdentifier</legacyItalic> Argument" section in <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the descriptor information. The data type depends on the value of <legacyItalic>FieldIdentifier</legacyItalic>.</para>
          <para>If <legacyItalic>ValuePtr</legacyItalic> is integer type, applications should use a buffer of SQLULEN and initialize the value to 0 before calling this function as some drivers may only write the lower 32-bit or 16-bit of a buffer and leave the higher-order bit unchanged.</para>
          <para>If <legacyItalic>ValuePtr</legacyItalic> is NULL, <legacyItalic>StringLengthPtr</legacyItalic> will still return the total number of bytes (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>ValuePtr</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>FieldIdentifier</legacyItalic> is an ODBC-defined field and<legacyItalic> ValuePtr</legacyItalic> points to a character string or a binary buffer, this argument should be the length of *<legacyItalic>ValuePtr</legacyItalic>. If <legacyItalic>FieldIdentifier</legacyItalic> is an ODBC-defined field and *<legacyItalic>ValuePtr</legacyItalic> is an integer, <legacyItalic>BufferLength</legacyItalic> is ignored. If the value in <legacyItalic>*ValuePtr</legacyItalic> is of a Unicode data type (when calling <legacyBold>SQLGetDescFieldW</legacyBold>), the <legacyItalic>BufferLength</legacyItalic> argument must be an even number.</para>
          <para>If <legacyItalic>FieldIdentifier</legacyItalic> is a driver-defined field, the application indicates the nature of the field to the Driver Manager by setting the <legacyItalic>BufferLength</legacyItalic> argument. <legacyItalic>BufferLength</legacyItalic> can have the following values:</para>
        </definition>
      </definitionTable>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>*ValuePtr</legacyItalic> is a pointer to a character string, then <legacyItalic>BufferLength</legacyItalic> is the length of the string or SQL_NTS.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>*ValuePtr</legacyItalic> is a pointer to a binary buffer, then the application places the result of the SQL_LEN_BINARY_ATTR(<legacyItalic>length</legacyItalic>) macro in <legacyItalic>BufferLength</legacyItalic>. This places a negative value in <legacyItalic>BufferLength</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>*ValuePtr</legacyItalic> is a pointer to a value other than a character string or binary string, then <legacyItalic>BufferLength</legacyItalic> should have the value SQL_IS_POINTER. </para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>*ValuePtr</legacyItalic> is contains a fixed-length data type, then <legacyItalic>BufferLength</legacyItalic> is either SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT, or SQL_IS_USMALLINT, as appropriate.</para>
        </listItem>
      </list>
      <definitionTable>
        <definedTerm>
          <legacyItalic>StringLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to the buffer in which to return the total number of bytes (excluding the number of bytes required for the null-termination character) available to return in *<legacyItalic>ValuePtr</legacyItalic>.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA, or SQL_INVALID_HANDLE.</para>
      <para>SQL_NO_DATA is returned if <legacyItalic>RecNumber</legacyItalic> is greater than the current number of descriptor records.</para>
      <para>SQL_NO_DATA is returned if <legacyItalic>DescriptorHandle</legacyItalic> is an IRD handle and the statement is in the prepared or executed state but there was no open cursor associated with it.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLGetDescField</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLGetDescField</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The buffer *<legacyItalic>ValuePtr</legacyItalic> was not large enough to return the entire descriptor field, so the field was truncated. The length of the untruncated descriptor field is returned in *<legacyItalic>StringLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>(DM) The <legacyItalic>RecNumber</legacyItalic> argument was equal to 0, the SQL_ATTR_USE_BOOKMARK statement attribute was SQL_UB_OFF, and the <legacyItalic>DescriptorHandle</legacyItalic> argument was an IRD handle. (This error can be returned for an explicitly allocated descriptor only if the descriptor is associated with a statement handle.)</para>
              <para>The <legacyItalic>FieldIdentifier</legacyItalic> argument was a record field, the <legacyItalic>RecNumber</legacyItalic> argument was 0, and the <legacyItalic>DescriptorHandle</legacyItalic> argument was an IPD handle.</para>
              <para>The <legacyItalic>RecNumber</legacyItalic> argument was less than 0.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>*MessageText</legacyItalic> buffer describes the error and its cause. </para>
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
                <legacyItalic>DescriptorHandle</legacyItalic> was associated with a <legacyItalic>StatementHandle</legacyItalic> as an IRD, and the associated statement handle had not been prepared or executed.</para>
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
              <para>(DM) <legacyItalic>DescriptorHandle</legacyItalic> was associated with a <legacyItalic>StatementHandle</legacyItalic> for which an asynchronously executing function (not this one) was called and was still executing when this function was called.</para>
              <para>(DM) <legacyItalic>DescriptorHandle</legacyItalic> was associated with a <legacyItalic>StatementHandle</legacyItalic> for which <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>DescriptorHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLGetDescField</unmanagedCodeEntityReference> function was called.</para>
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
              <para>The SQL_DESC_TYPE and SQL_DESC_DATETIME_INTERVAL_CODE fields do not form a valid ODBC SQL type, a valid driver-specific SQL type (for IPDs), or a valid ODBC C type (for APDs or ARDs).</para>
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
              <para>(DM) <legacyItalic>*ValuePtr</legacyItalic> was a character string, and <legacyItalic>BufferLength</legacyItalic> was less than zero.</para>
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
              <para>
                <legacyItalic>FieldIdentifier</legacyItalic> was not an ODBC-defined field and was not an implementation-defined value.</para>
              <para>
                <legacyItalic>FieldIdentifier</legacyItalic> was undefined for the <legacyItalic>DescriptorHandle</legacyItalic>.</para>
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
              <para>(DM) For more information about the suspended state, see <link xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</link>.</para>
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
      <para>An application can call <legacyBold>SQLGetDescField</legacyBold> to return the value of a single field of a descriptor record. A call to <legacyBold>SQLGetDescField</legacyBold> can return the setting of any field in any descriptor type, including header fields, record fields, and bookmark fields. An application can obtain the settings of multiple fields in the same or different descriptors, in arbitrary order, by making repeated calls to <legacyBold>SQLGetDescField</legacyBold>. <legacyBold>SQLGetDescField</legacyBold> can also be called to return driver-defined descriptor fields.</para>
      <para>For performance reasons, an application should not call <legacyBold>SQLGetDescField</legacyBold> for an IRD before executing a statement.</para>
      <para>The settings of multiple fields that describe the name, data type, and storage of column or parameter data can also be retrieved in a single call to <legacyBold>SQLGetDescRec</legacyBold>. <legacyBold>SQLGetStmtAttr</legacyBold> can be called to return the setting of a single field in the descriptor header that is also a statement attribute. <legacyBold>SQLColAttribute</legacyBold>, <legacyBold>SQLDescribeCol</legacyBold>, and <legacyBold>SQLDescribeParam</legacyBold> return record or bookmark fields.</para>
      <para>When an application calls <legacyBold>SQLGetDescField</legacyBold> to retrieve the value of a field that is undefined for a particular descriptor type, the function returns SQL_SUCCESS but the value returned for the field is undefined. For example, calling <legacyBold>SQLGetDescField</legacyBold> for the SQL_DESC_NAME or SQL_DESC_NULLABLE field of an APD or ARD will return SQL_SUCCESS but an undefined value for the field.</para>
      <para>When an application calls <legacyBold>SQLGetDescField</legacyBold> to retrieve the value of a field that is defined for a particular descriptor type but that has no default value and has not been set yet, the function returns SQL_SUCCESS but the value returned for the field is undefined. For more information on the initialization of descriptor fields and descriptions of the fields, see "Initialization of Descriptor Fields" in <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>. For more information on descriptors, see <legacyLink xlink:href="ef2cbb93-cd00-40f8-b1d2-5f5723a991aa">Descriptors</legacyLink>.</para>
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
                <legacyLink xlink:href="325e0907-8e87-44e8-a111-f39e636a9cbc">SQLGetDescRec Function</legacyLink>
              </para>
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
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>