---
title: SQLSetDescRec Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLSetDescRec
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
translation.priority.ht: 
  - en-gb
---
# SQLSetDescRec Function
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
        <para>The <legacyBold>SQLSetDescRec</legacyBold> function sets multiple descriptor fields that affect the data type and buffer bound to a column or parameter data. </para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLSetDescRec</legacyBold>(
      SQLHDESC      <parameterReference>DescriptorHandle</parameterReference>,
      SQLSMALLINT   <parameterReference>RecNumber</parameterReference>,
      SQLSMALLINT   <parameterReference>Type</parameterReference>,
      SQLSMALLINT   <parameterReference>SubType</parameterReference>,
      SQLLEN        <parameterReference>Length</parameterReference>,
      SQLSMALLINT   <parameterReference>Precision</parameterReference>,
      SQLSMALLINT   <parameterReference>Scale</parameterReference>,
      SQLPOINTER    <parameterReference>DataPtr</parameterReference>,
      SQLLEN *      <parameterReference>StringLengthPtr</parameterReference>,
      SQLLEN *      <parameterReference>IndicatorPtr</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>DescriptorHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Descriptor handle. This must not be an IRD handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>RecNumber</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Indicates the descriptor record that contains the fields to be set. Descriptor records are numbered from 0, with record number 0 being the bookmark record. This argument must be equal to or greater than 0. If <legacyItalic>RecNumber</legacyItalic> is greater than the value of SQL_DESC_COUNT, SQL_DESC_COUNTis changed to the value of <legacyItalic>RecNumber</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Type</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The value to which to set the SQL_DESC_TYPE field for the descriptor record.</para>
        </definition>
        <definedTerm>
          <legacyItalic>SubType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] For records whose type is SQL_DATETIME or SQL_INTERVAL, this is the value to which to set the SQL_DESC_DATETIME_INTERVAL_CODE field.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Length</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The value to which to set the SQL_DESC_OCTET_LENGTH field for the descriptor record.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Precision</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The value to which to set the SQL_DESC_PRECISION field for the descriptor record.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Scale</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The value to which to set the SQL_DESC_SCALE field for the descriptor record.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DataPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Deferred Input or Output] The value to which to set the SQL_DESC_DATA_PTR field for the descriptor record. <legacyItalic>DataPtr</legacyItalic> can be set to a null pointer.</para>
          <para>The <legacyItalic>DataPtr</legacyItalic> argument can be set to a null pointer to set the SQL_DESC_DATA_PTR field to a null pointer. If the handle in the <legacyItalic>DescriptorHandle</legacyItalic> argument is associated with an ARD, this unbinds the column. </para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Deferred Input or Output] The value to which to set the SQL_DESC_OCTET_LENGTH_PTR field for the descriptor record. <legacyItalic>StringLengthPtr</legacyItalic> can be set to a null pointer to set the SQL_DESC_OCTET_LENGTH_PTR field to a null pointer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>IndicatorPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Deferred Input or Output] The value to which to set the SQL_DESC_INDICATOR_PTR field for the descriptor record. <legacyItalic>IndicatorPtr</legacyItalic> can be set to a null pointer to set the SQL_DESC_INDICATOR_PTR field to a null pointer.</para>
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
      <para>When <legacyBold>SQLSetDescRec </legacyBold>returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DESC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>DescriptorHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLSetDescRec</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The <legacyItalic>RecNumber</legacyItalic> argument was set to 0, and the <legacyItalic>DescriptorHandle</legacyItalic> referred to an IPD handle.</para>
              <para>The <legacyItalic>RecNumber</legacyItalic> argument was less than 0. </para>
              <para>The <legacyItalic>RecNumber</legacyItalic> argument was greater than the maximum number of columns or parameters that the data source can support, and the <legacyItalic>DescriptorHandle</legacyItalic> argument was an APD, IPD, or ARD. </para>
              <para>The <legacyItalic>RecNumber</legacyItalic> argument was equal to 0, and the <legacyItalic>DescriptorHandle</legacyItalic> argument referred to an implicitly allocated APD. (This error does not occur with an explicitly allocated application descriptor because it is not known whether an explicitly allocated application descriptor is an APD or ARD until execute time.)</para>
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
              <para>(DM) The <legacyItalic>DescriptorHandle</legacyItalic> was associated with a <legacyItalic>StatementHandle</legacyItalic> for which an asynchronously executing function (not this one) was called and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> with which the <legacyItalic>DescriptorHandle</legacyItalic> was associated and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <parameterReference>DescriptorHandle</parameterReference>. This aynchronous function was still executing when the <unmanagedCodeEntityReference>SQLSetDescRec</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for one of the statement handles associated with the <parameterReference>DescriptorHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
              <para>The <legacyItalic>DescriptorHandle</legacyItalic> argument was associated with an IRD.</para>
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
              <para>The <legacyItalic>Type</legacyItalic> field, or any other field associated with the SQL_DESC_TYPE field in the descriptor, was not valid or consistent. </para>
              <para>Descriptor information checked during a consistency check was not consistent. (See "Consistency Checks," later in this section.)</para>
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
              <para>(DM) The driver was an ODBC 2<legacyItalic>.x</legacyItalic> driver, the descriptor was an ARD, the <legacyItalic>ColumnNumber</legacyItalic> argument was set to 0, and the value specified for the argument <legacyItalic>BufferLength</legacyItalic> was not equal to 4.</para>
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
      <para>An application can call <legacyBold>SQLSetDescRec</legacyBold> to set the following fields for a single column or parameter:  </para>
      <list class="bullet">
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
          <para>SQL_DESC_DATA_PTR</para>
        </listItem>
        <listItem>
          <para>SQL_DESC_OCTET_LENGTH_PTR</para>
        </listItem>
        <listItem>
          <para>SQL_DESC_INDICATOR_PTR</para>
        </listItem>
      </list>
      <alert class="note">
        <para>If a call to <legacyBold>SQLSetDescRec</legacyBold> fails, the contents of the descriptor record identified by the <legacyItalic>RecNumber</legacyItalic> argument are undefined.</para>
      </alert>
      <para>When binding a column or parameter, <legacyBold>SQLSetDescRec</legacyBold> allows you to change multiple fields affecting the binding without calling <legacyBold>SQLBindCol </legacyBold>or <legacyBold>SQLBindParameter</legacyBold> or making multiple calls to <legacyBold>SQLSetDescField</legacyBold>. <legacyBold>SQLSetDescRec</legacyBold> can set fields on a descriptor not currently associated with a statement. Note that <legacyBold>SQLBindParameter</legacyBold> sets more fields than <legacyBold>SQLSetDescRec</legacyBold>, can set fields on both an APD and an IPD in one call, and does not require a descriptor handle.</para>
      <alert class="note">
        <para>The statement attribute SQL_ATTR_USE_BOOKMARKS should always be set before calling <legacyBold>SQLSetDescRec</legacyBold> with a <legacyItalic>RecNumber</legacyItalic> argument of 0 to set bookmark fields. While this is not mandatory, it is strongly recommended.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Consistency Checks</title>
    <content>
      <para>A consistency check is performed by the driver automatically whenever an application sets the SQL_DESC_DATA_PTR field of an APD, ARD, or IPD. If any of the fields is inconsistent with other fields, <legacyBold>SQLSetDescRec</legacyBold> will return SQLSTATE HY021 (Inconsistent descriptor information).</para>
      <para>Whenever an application sets the SQL_DESC_DATA_PTR field of an APD, ARD, or IPD, the driver checks that the value of the SQL_DESC_TYPE field and the values applicable to that SQL_DESC_TYPE field are valid and consistent. This check is always performed when <legacyBold>SQLBindParameter</legacyBold> or <legacyBold>SQLBindCol</legacyBold> is called or when <legacyBold>SQLSetDescRec</legacyBold> is called for an APD, ARD, or IPD. This consistency check includes the following checks on descriptor fields:  </para>
      <list class="bullet">
        <listItem>
          <para>The SQL_DESC_TYPE field must be one of the valid ODBC C or SQL types or a driver-specific SQL type. The SQL_DESC_CONCISE_TYPE field must be one of the valid ODBC C or SQL types or a driver-specific C or SQL type, including the concise datetime and interval types.</para>
        </listItem>
        <listItem>
          <para>If the SQL_DESC_TYPE record field is SQL_DATETIME or SQL_INTERVAL, the SQL_DESC_DATETIME_INTERVAL_CODE field must be one of the valid datetime or interval codes. (See the description of the SQL_DESC_DATETIME_INTERVAL_CODE field in <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.)</para>
        </listItem>
        <listItem>
          <para>If the SQL_DESC_TYPE field indicates a numeric type, the SQL_DESC_PRECISION and SQL_DESC_SCALE fields are verified to be valid.</para>
        </listItem>
        <listItem>
          <para>If the SQL_DESC_CONCISE_TYPE field is a time or timestamp data type, an interval type with a seconds component, or one of the interval data types with a time component, the SQL_DESC_PRECISION field is verified to be a valid seconds precision.</para>
        </listItem>
        <listItem>
          <para>If the SQL_DESC_CONCISE_TYPE is an interval data type, the SQL_DESC_DATETIME_INTERVAL_PRECISION field is verified to be a valid interval leading precision value.</para>
        </listItem>
      </list>
      <para>The SQL_DESC_DATA_PTR field of an IPD is not normally set; however, an application can do so to force a consistency check of IPD fields. A consistency check cannot be performed on an IRD. The value that the SQL_DESC_DATA_PTR field of the IPD is set to is not actually stored and cannot be retrieved by a call to <legacyBold>SQLGetDescField</legacyBold> or <legacyBold>SQLGetDescRec</legacyBold>; the setting is made only to force the consistency check.</para>
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
              <para>Getting a single descriptor field</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="f09ff660-1e4a-4370-be85-90d4da0487d3">SQLGetDescField Function</legacyLink>
              </para>
            </TD>
          </tr>
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
              <para>Setting single descriptor fields</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField Function</legacyLink>
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