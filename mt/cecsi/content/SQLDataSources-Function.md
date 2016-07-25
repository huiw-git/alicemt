---
title: "SQLDataSources Function"
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
  - SQLDataSources
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 3f63b1b4-e70e-44cd-96c6-6878d50d0117
caps.latest.revision: 21
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLDataSources Function
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
          <legacyBold>SQLDataSources</legacyBold> returns information about a data source. This function is implemented only by the Driver Manager.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLDataSources</legacyBold>(
     SQLHENV          <parameterReference>EnvironmentHandle</parameterReference>,
     SQLUSMALLINT     <parameterReference>Direction</parameterReference>,
     SQLCHAR *        <parameterReference>ServerName</parameterReference>,
     SQLSMALLINT      <parameterReference>BufferLength1</parameterReference>,
     SQLSMALLINT *    <parameterReference>NameLength1Ptr</parameterReference>,
     SQLCHAR *        <parameterReference>Description</parameterReference>,
     SQLSMALLINT      <parameterReference>BufferLength2</parameterReference>,
     SQLSMALLINT *    <parameterReference>NameLength2Ptr</parameterReference>);</legacySyntax>
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
          <para>[Input] Determines which data source the Driver Manager returns information about. Can be:</para>
          <para>SQL_FETCH_NEXT (to fetch the next data source name in the list), SQL_FETCH_FIRST (to fetch from the beginning of the list), SQL_FETCH_FIRST_USER (to fetch the first user DSN), or SQL_FETCH_FIRST_SYSTEM (to fetch the first system DSN).   </para>
          <para>When <legacyItalic>Direction</legacyItalic> is set to SQL_FETCH_FIRST, subsequent calls to <legacyBold>SQLDataSources</legacyBold> with <legacyItalic>Direction</legacyItalic> set to SQL_FETCH_NEXT return both user and system DSNs. When <legacyItalic>Direction</legacyItalic> is set to SQL_FETCH_FIRST_USER, all subsequent calls to <legacyBold>SQLDataSources</legacyBold> with <legacyItalic>Direction</legacyItalic> set to SQL_FETCH_NEXT return only user DSNs. When <legacyItalic>Direction</legacyItalic> is set to SQL_FETCH_FIRST_SYSTEM, all subsequent calls to <legacyBold>SQLDataSources</legacyBold> with <legacyItalic>Direction</legacyItalic> set to SQL_FETCH_NEXT return only system DSNs. </para>
        </definition>
        <definedTerm>
          <legacyItalic>ServerName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the data source name.</para>
          <para>If <legacyItalic>ServerName</legacyItalic> is NULL, <legacyItalic>NameLength1Ptr</legacyItalic> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>ServerName</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength1</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>ServerName</legacyItalic> buffer, in characters; this does not need to be longer than SQL_MAX_DSN_LENGTH plus the null-termination character.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength1Ptr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of characters (excluding the null-termination character) available to return in *<legacyItalic>ServerName</legacyItalic>. If the number of characters available to return is greater than or equal to <legacyItalic>BufferLength1</legacyItalic>, the data source name in *<legacyItalic>ServerName</legacyItalic> is truncated to <legacyItalic>BufferLength1</legacyItalic> minus the length of a null-termination character.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Description</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the description of the driver associated with the data source. For example, dBASE or SQL Server.</para>
          <para>If <legacyItalic>Description</legacyItalic> is NULL, <legacyItalic>NameLength2Ptr</legacyItalic> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>Description</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength2</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of the *<legacyItalic>Description</legacyItalic> buffer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength2Ptr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of characters (excluding the null-termination character) available to return in *<legacyItalic>Description</legacyItalic>. If the number of characters available to return is greater than or equal to <legacyItalic>BufferLength2</legacyItalic>, the driver description in *<legacyItalic>Description</legacyItalic> is truncated to <legacyItalic>BufferLength2</legacyItalic> minus the length of a null-termination character.</para>
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
      <para>When <legacyBold>SQLDataSources</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>EnvironmentHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLDataSources</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>(DM) The buffer *<legacyItalic>ServerName</legacyItalic> was not large enough to return the complete data source name. Therefore, the name was truncated. The length of the entire data source name is returned in *<legacyItalic>NameLength1Ptr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
              <para>(DM) The buffer *<legacyItalic>Description</legacyItalic> was not large enough to return the complete driver description. Therefore, the description was truncated. The length of the untruncated data source description is returned in *<legacyItalic>NameLength2Ptr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>(DM) An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>*MessageText</legacyItalic> buffer describes the error and its cause.</para>
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
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>,<unmanagedCodeEntityReference> SQLExecDirect</unmanagedCodeEntityReference>, or<unmanagedCodeEntityReference> SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
              <para>(DM) The value specified for argument <legacyItalic>BufferLength2</legacyItalic> was less than 0.</para>
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
              <para>(DM) The value specified for the argument <legacyItalic>Direction</legacyItalic> was not equal to SQL_FETCH_FIRST, SQL_FETCH_FIRST_USER, SQL_FETCH_FIRST_SYSTEM, or SQL_FETCH_NEXT.</para>
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
      <para>Because <legacyBold>SQLDataSources</legacyBold> is implemented in the Driver Manager, it is supported for all drivers regardless of a particular driver's standards compliance.</para>
      <para>An application can call <legacyBold>SQLDataSources</legacyBold> multiple times to retrieve all data source names. The Driver Manager retrieves this information from the system information. When there are no more data source names, the Driver Manager returns SQL_NO_DATA. If <legacyBold>SQLDataSources</legacyBold> is called with SQL_FETCH_NEXT immediately after it returns SQL_NO_DATA, it will return the first data source name. For information about how an application uses the information returned by <legacyBold>SQLDataSources</legacyBold>, see <legacyLink xlink:href="10aaf570-01ab-4478-8339-bdde2a5e3dd1">Choosing a Data Source or Driver</legacyLink>.</para>
      <para>If SQL_FETCH_NEXT is passed to <legacyBold>SQLDataSources</legacyBold> the very first time it is called, it will return the first data source name.</para>
      <para>The driver determines how data source names are mapped to actual data sources.</para>
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
              <para>Connecting to a data source using a connection string or dialog box</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning driver descriptions and attributes</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa">SQLDrivers Function</legacyLink>
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