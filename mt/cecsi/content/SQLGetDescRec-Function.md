---
title: SQLGetDescRec Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLGetDescRec
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 325e0907-8e87-44e8-a111-f39e636a9cbc
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetDescRec Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.0 Standards Compliance: ISO 92 </para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLGetDescRec</legacyBold> returns the current settings or values of multiple fields of a descriptor record. The fields returned describe the name, data type, and storage of column or parameter data.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetDescRec</legacyBold>(
      SQLHDESC        <parameterReference>DescriptorHandle</parameterReference>,
      SQLSMALLINT     <parameterReference>RecNumber</parameterReference>,
      SQLCHAR *       <parameterReference>Name</parameterReference>,
      SQLSMALLINT     <parameterReference>BufferLength</parameterReference>,
      SQLSMALLINT *   <parameterReference>StringLengthPtr</parameterReference>,
      SQLSMALLINT *   <parameterReference>TypePtr</parameterReference>,
      SQLSMALLINT *   <parameterReference>SubTypePtr</parameterReference>,
      SQLLEN *        <parameterReference>LengthPtr</parameterReference>,
      SQLSMALLINT *   <parameterReference>PrecisionPtr</parameterReference>,
      SQLSMALLINT *   <parameterReference>ScalePtr</parameterReference>,
      SQLSMALLINT *   <parameterReference>NullablePtr</parameterReference>);</legacySyntax>
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
          <para>[Input] Indicates the descriptor record from which the application seeks information. Descriptor records are numbered from 1, with record number 0 being the bookmark record. The <legacyItalic>RecNumber</legacyItalic> argument must be less than or equal to the value of SQL_DESC_COUNT. If <legacyItalic>RecNumber</legacyItalic> is less than or equal to SQL_DESC_COUNT but the row does not contain data for a column or parameter, a call to <legacyBold>SQLGetDescRec</legacyBold> will return the default values of the fields. (For more information, see "Initialization of Descriptor Fields" in <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.)</para>
        </definition>
        <definedTerm>
          <legacyItalic>Name</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the SQL_DESC_NAME field for the descriptor record.</para>
          <para>If <legacyItalic>Name</legacyItalic> is NULL, <legacyItalic>StringLengthPtr</legacyItalic> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>Name</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>Name</legacyItalic> buffer, in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the number of characters of data available to return in the *<legacyItalic>Name</legacyItalic> buffer, excluding the null-termination character. If the number of characters was greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the data in *<legacyItalic>Name</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character, and is null-terminated by the driver.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TypePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the value of the SQL_DESC_TYPE field for the descriptor record.</para>
        </definition>
        <definedTerm>
          <legacyItalic>SubTypePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] For records whose type is SQL_DATETIME or SQL_INTERVAL, this is a pointer to a buffer in which to return the value of the SQL_DESC_DATETIME_INTERVAL_CODE field.</para>
        </definition>
        <definedTerm>
          <legacyItalic>LengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the value of the SQL_DESC_OCTET_LENGTH field for the descriptor record.</para>
        </definition>
        <definedTerm>
          <legacyItalic>PrecisionPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the value of the SQL_DESC_PRECISION field for the descriptor record.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ScalePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the value of the SQL_DESC_SCALE field for the descriptor record.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NullablePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the value of the SQL_DESC_NULLABLE field for the descriptor record.</para>
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
      <para>When <legacyBold>SQLGetDescRec</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DESC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>DescriptorHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLGetDescRec</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The buffer *<legacyItalic>Name</legacyItalic> was not large enough to return the entire descriptor field. Therefore, the field was truncated. The length of the untruncated descriptor field is returned in *<legacyItalic>StringLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>The <legacyItalic>FieldIdentifier</legacyItalic> argument was a record field, the <legacyItalic>RecNumber</legacyItalic> argument was set to 0, and the <legacyItalic>DescriptorHandle</legacyItalic> argument was an IPD handle.</para>
              <para>(DM) The <legacyItalic>RecNumber</legacyItalic> argument was set to 0, and the SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_OFF, and the <legacyItalic>DescriptorHandle</legacyItalic> argument was an IRD handle.</para>
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
              <para>The driver was unable to allocate the memory that is required to support execution or completion of the function.</para>
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
                <legacyItalic>DescriptorHandle</legacyItalic> was associated with an IRD, and the associated statement handle was not in the prepared or executed state.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <parameterReference>DescriptorHandle</parameterReference>. This asynchronous function was still executing when <unmanagedCodeEntityReference>SQLGetDescRec</unmanagedCodeEntityReference> was called.</para>
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
              <para>(DM) The driver associated with <legacyItalic>DescriptorHandle</legacyItalic> does not support the function.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>An application can call <legacyBold>SQLGetDescRec</legacyBold> to retrieve the values of the following descriptor fields for a single column or parameter:  </para>
      <list class="bullet">
        <listItem>
          <para>SQL_DESC_NAME</para>
        </listItem>
        <listItem>
          <para>SQL_DESC_TYPE</para>
        </listItem>
        <listItem>
          <para>SQL_DESC_DATETIME_INTERVAL_CODE (for records whose type is SQL_DATETIME or SQL_INTERVAL)</para>
        </listItem>
        <listItem>
          <para>SQL_DESC_OCTET_LENGTH</para>
        </listItem>
        <listItem>
          <para>SQL_DESC_PRECISION</para>
        </listItem>
        <listItem>
          <para>SQL_DESC_SCALE</para>
        </listItem>
        <listItem>
          <para>SQL_DESC_NULLABLE</para>
        </listItem>
      </list>
      <para>
        <legacyBold>SQLGetDescRec</legacyBold> does not retrieve the values for header fields.</para>
      <para>An application can prevent the return of a field's setting by setting the argument that corresponds to the field to a null pointer.</para>
      <para>When an application calls <legacyBold>SQLGetDescRec</legacyBold> to retrieve the value of a field that is undefined for a particular descriptor type, the function returns SQL_SUCCESS but the value returned for the field is undefined. For example, calling <legacyBold>SQLGetDescRec</legacyBold> for the SQL_DESC_NAME or SQL_DESC_NULLABLE field of an APD or ARD will return SQL_SUCCESS but an undefined value for the field.</para>
      <para>When an application calls <legacyBold>SQLGetDescRec</legacyBold> to retrieve the value of a field that is defined for a particular descriptor type but that has no default value and has not been set yet, the function returns SQL_SUCCESS but the value returned for the field is undefined. For more information, see "Initialization of Descriptor Fields" in <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.</para>
      <para>The values of fields can also be retrieved individually by a call to <legacyBold>SQLGetDescField</legacyBold>. For a description of the fields in a descriptor header or record, see <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>. For more information about descriptors, see <legacyLink xlink:href="ef2cbb93-cd00-40f8-b1d2-5f5723a991aa">Descriptors</legacyLink>.</para>
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
              <para>Binding a column</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Binding a parameter</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Getting a descriptor field</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="f09ff660-1e4a-4370-be85-90d4da0487d3">SQLGetDescField Function</legacyLink>
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