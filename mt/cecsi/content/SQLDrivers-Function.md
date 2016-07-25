---
title: "SQLDrivers Function"
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
  - SQLDrivers
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa
caps.latest.revision: 22
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLDrivers Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 2.0 Standards Compliance: ODBC</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLDrivers</legacyBold> lists driver descriptions and driver attribute keywords. This function is implemented only by the Driver Manager.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLDrivers</legacyBold>(
     SQLHENV         <parameterReference>EnvironmentHandle</parameterReference>,
     SQLUSMALLINT    <parameterReference>Direction</parameterReference>,
     SQLCHAR *       <parameterReference>DriverDescription</parameterReference>,
     SQLSMALLINT     <parameterReference>BufferLength1</parameterReference>,
     SQLSMALLINT *   <parameterReference>DescriptionLengthPtr</parameterReference>,
     SQLCHAR *       <parameterReference>DriverAttributes</parameterReference>,
     SQLSMALLINT     <parameterReference>BufferLength2</parameterReference>,
     SQLSMALLINT *   <parameterReference>AttributesLengthPtr</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>EnvironmentHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Environment handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Direction</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Determines whether the Driver Manager fetches the next driver description in the list (SQL_FETCH_NEXT) or whether the search starts from the beginning of the list (SQL_FETCH_FIRST).</para>
        </definition>
        <definedTerm>
          <legacyItalic>DriverDescription</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the driver description.</para>
          <para>If <legacyItalic>DriverDescription</legacyItalic> is NULL, <legacyItalic>DescriptionLengthPtr</legacyItalic> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>DriverDescription</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength1</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>DriverDescription</legacyItalic> buffer, in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DescriptionLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of characters (excluding the null-termination character) available to return in *<legacyItalic>DriverDescription</legacyItalic>. If the number of characters available to return is greater than or equal to <legacyItalic>BufferLength1</legacyItalic>, the driver description in *<legacyItalic>DriverDescription</legacyItalic> is truncated to <legacyItalic>BufferLength1</legacyItalic> minus the length of a null-termination character.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DriverAttributes</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the list of driver attribute value pairs (see "Comments").</para>
          <para>If <legacyItalic>DriverAttributes</legacyItalic> is NULL, <legacyItalic>AttributesLengthPtr</legacyItalic> will still return the total number of bytes (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>DriverAttributes</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength2</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>DriverAttributes</legacyItalic> buffer, in characters. If the <legacyItalic>*DriverDescription</legacyItalic> value is a Unicode string (when calling <legacyBold>SQLDriversW</legacyBold>), the <legacyItalic>BufferLength</legacyItalic> argument must be an even number.</para>
        </definition>
        <definedTerm>
          <legacyItalic>AttributesLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of bytes (excluding the null-termination byte) available to return in *<legacyItalic>DriverAttributes</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>BufferLength2</legacyItalic>, the list of attribute value pairs in *<legacyItalic>DriverAttributes</legacyItalic> is truncated to <legacyItalic>BufferLength2</legacyItalic> minus the length of the null-termination character.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLDrivers</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>EnvironmentHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLDrivers</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>(DM) Driver Manager–specific informational message. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>(DM) The buffer *<legacyItalic>DriverDescription</legacyItalic> was not large enough to return the complete driver description. Therefore, the description was truncated. The length of the complete driver description is returned in *<legacyItalic>DescriptionLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
              <para>(DM) The buffer *<legacyItalic>DriverAttributes</legacyItalic> was not large enough to return the complete list of attribute value pairs. Therefore, the list was truncated. The length of the untruncated list of attribute value pairs is returned in *<legacyItalic>AttributesLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>(DM) The Driver Manager was unable to allocate memory that is required to support execution or completion of the function.</para>
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
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
              <para>(DM) The value specified for argument <legacyItalic>BufferLength1</legacyItalic> was less than 0.</para>
              <para>(DM) The value specified for argument <legacyItalic>BufferLength2</legacyItalic> was less than 0 or equal to 1.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY103</para>
            </TD>
            <TD>
              <para>Invalid retrieval code</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the argument <legacyItalic>Direction</legacyItalic> was not equal to SQL_FETCH_FIRST or SQL_FETCH_NEXT.</para>
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
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLDrivers</legacyBold> returns the driver description in the *<legacyItalic>DriverDescription</legacyItalic> buffer. It returns additional information about the driver in the *<legacyItalic>DriverAttributes</legacyItalic> buffer as a list of keyword-value pairs. All keywords listed in the system information for drivers will be returned for all drivers, except for <legacyBold>CreateDSN</legacyBold>, which is used to prompt creation of data sources and therefore is optional. Each pair is terminated with a null byte, and the complete list is terminated with a null byte (that is, two null bytes mark the end of the list). For example, a file-based driver using C syntax might return the following list of attributes ("\0" represents a null character):</para>
      <code>FileUsage=1\0FileExtns=*.dbf\0\0</code>
      <para>If *<legacyItalic>DriverAttributes</legacyItalic> is not large enough to hold the entire list, the list is truncated, <legacyBold>SQLDrivers</legacyBold> returns SQLSTATE 01004 (Data truncated), and the length of the list (excluding the final null-termination byte) is returned in *<legacyItalic>AttributesLengthPtr</legacyItalic>.</para>
      <para>Driver attribute keywords are added from the system information when the driver is installed. For more information, see <legacyLink xlink:href="b7e48e9c-8912-4003-b4ef-30aa44de06a7">Installing ODBC Components</legacyLink>.</para>
      <para>An application can call <legacyBold>SQLDrivers</legacyBold> multiple times to retrieve all driver descriptions. The Driver Manager retrieves this information from the system information. When there are no more driver descriptions, <legacyBold>SQLDrivers</legacyBold> returns SQL_NO_DATA. If <legacyBold>SQLDrivers</legacyBold> is called with SQL_FETCH_NEXT immediately after it returns SQL_NO_DATA, it returns the first driver description. For information about how an application uses the information returned by <legacyBold>SQLDrivers</legacyBold>, see <legacyLink xlink:href="10aaf570-01ab-4478-8339-bdde2a5e3dd1">Choosing a Data Source or Driver</legacyLink>.</para>
      <para>If SQL_FETCH_NEXT is passed to <legacyBold>SQLDrivers</legacyBold> the very first time it is called, <legacyBold>SQLDrivers</legacyBold> returns the first data source name.</para>
      <para>Because <legacyBold>SQLDrivers</legacyBold> is implemented in the Driver Manager, it is supported for all drivers regardless of a particular driver's standards compliance.</para>
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
              <para>Discovering and listing values required to connect to a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="b7f1be66-e6c7-4790-88ec-62b7662103c0">SQLBrowseConnect Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Connecting to a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning data source names</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="3f63b1b4-e70e-44cd-96c6-6878d50d0117">SQLDataSources Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Connecting to a data source using a connection string or dialog box</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect Function</legacyLink>
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