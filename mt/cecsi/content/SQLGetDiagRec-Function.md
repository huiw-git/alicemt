---
title: SQLGetDiagRec Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLGetDiagRec
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: ebdbac93-3d68-438f-8416-ef1f08e04269
translation.priority.ht: 
  - en-gb
---
# SQLGetDiagRec Function
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
          <legacyBold>SQLGetDiagRec</legacyBold> returns the current values of multiple fields of a diagnostic record that contains error, warning, and status information. Unlike <legacyBold>SQLGetDiagField</legacyBold>, which returns one diagnostic field per call, <legacyBold>SQLGetDiagRec</legacyBold> returns several commonly used fields of a diagnostic record, including the SQLSTATE, the native error code, and the diagnostic message text.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetDiagRec</legacyBold>(
     SQLSMALLINT     <parameterReference>HandleType</parameterReference>,
     SQLHANDLE       <parameterReference>Handle</parameterReference>,
     SQLSMALLINT     <parameterReference>RecNumber</parameterReference>,
     SQLCHAR *       <parameterReference>SQLState</parameterReference>,
     SQLINTEGER *    <parameterReference>NativeErrorPtr</parameterReference>,
     SQLCHAR *       <parameterReference>MessageText</parameterReference>,
     SQLSMALLINT     <parameterReference>BufferLength</parameterReference>,
     SQLSMALLINT *   <parameterReference>TextLengthPtr</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>HandleType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A handle type identifier that describes the type of handle for which diagnostics are required. Must be one of the following: </para>
          <list class="bullet">
            <listItem>
              <para>SQL_HANDLE_DBC</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_DBC_INFO_TOKEN</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_DESC</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_ENV</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_STMT</para>
            </listItem>
          </list>
          <para>SQL_HANDLE_DBC_INFO_TOKEN handle is used only by the Driver Manager and driver. Applications should not use this handle type. For more information about SQL_HANDLE_DBC_INFO_TOKEN, see <link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Handle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A handle for the diagnostic data structure, of the type indicated by <legacyItalic>HandleType</legacyItalic>. If <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_ENV, <legacyItalic>Handle</legacyItalic> can be either a shared or an unshared environment handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>RecNumber</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Indicates the status record from which the application seeks information. Status records are numbered from 1.</para>
        </definition>
        <definedTerm>
          <legacyItalic>SQLState</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return a five-character SQLSTATE code (and terminating NULL) for the diagnostic record <legacyItalic>RecNumber</legacyItalic>. The first two characters indicate the class; the next three indicate the subclass. This information is contained in the SQL_DIAG_SQLSTATE diagnostic field. For more information, see <legacyLink xlink:href="f29fff2e-3d09-4a8c-a2f9-2059062cbebf">SQLSTATEs</legacyLink>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NativeErrorPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the native error code, specific to the data source. This information is contained in the SQL_DIAG_NATIVE diagnostic field.</para>
        </definition>
        <definedTerm>
          <legacyItalic>MessageText</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the diagnostic message text string. This information is contained in the SQL_DIAG_MESSAGE_TEXT diagnostic field. For the format of the string, see <legacyLink xlink:href="98027871-9901-476e-a722-ee58b7723c1f">Diagnostic Messages</legacyLink>.</para>
          <para>If <legacyItalic>MessageText</legacyItalic> is NULL, <legacyItalic>TextLengthPtr</legacyItalic> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>MessageText</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>MessageText</legacyItalic> buffer in characters. There is no maximum length of the diagnostic message text.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TextLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of characters (excluding the number of characters required for the null-termination character) available to return in <legacyItalic>*MessageText</legacyItalic>. If the number of characters available to return is greater than <legacyItalic>BufferLength</legacyItalic>, the diagnostic message text in <legacyItalic>*MessageText</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character.</para>
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
      <para>
        <legacyBold>SQLGetDiagRec</legacyBold> does not post diagnostic records for itself. It uses the following return values to report the outcome of its own execution:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_SUCCESS: The function successfully returned diagnostic information.</para>
        </listItem>
        <listItem>
          <para>SQL_SUCCESS_WITH_INFO: The *<legacyItalic>MessageText</legacyItalic> buffer was too small to hold the requested diagnostic message. No diagnostic records were generated. To determine that a truncation occurred, the application must compare <legacyItalic>BufferLength</legacyItalic> to the actual number of bytes available, which is written to *<legacyItalic>StringLengthPtr</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>SQL_INVALID_HANDLE: The handle indicated by <legacyItalic>HandleType</legacyItalic> and <legacyItalic>Handle</legacyItalic> was not a valid handle.</para>
        </listItem>
        <listItem>
          <para>SQL_ERROR: One of the following occurred:</para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyItalic>RecNumber</legacyItalic> was negative or 0.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>BufferLength</legacyItalic> was less than zero.</para>
            </listItem>
            <listItem>
              <para>When using asynchronous notification, the asynchronous operation on the handle was not complete.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>SQL_NO_DATA: <legacyItalic>RecNumber</legacyItalic> was greater than the number of diagnostic records that existed for the handle specified in <legacyItalic>Handle.</legacyItalic> The function also returns SQL_NO_DATA for any positive <legacyItalic>RecNumber</legacyItalic> if there are no diagnostic records for <legacyItalic>Handle</legacyItalic>.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>An application typically calls <legacyBold>SQLGetDiagRec</legacyBold> when a previous call to an ODBC function has returned SQL_ERROR or SQL_SUCCESS_WITH_INFO. However, because any ODBC function can post zero or more diagnostic records each time it is called, an application can call <legacyBold>SQLGetDiagRec</legacyBold> after any ODBC function call. An application can call <legacyBold>SQLGetDiagRec</legacyBold> multiple times to return some or all of the records in the diagnostic data structure. ODBC imposes no limit to the number of diagnostic records that can be stored at any one time.</para>
      <para>
        <legacyBold>SQLGetDiagRec</legacyBold> cannot be used to return fields from the header of the diagnostic data structure. (The <legacyItalic>RecNumber</legacyItalic> argument must be greater than 0.) The application should call <legacyBold>SQLGetDiagField</legacyBold> for this purpose.</para>
      <para>
        <legacyBold>SQLGetDiagRec</legacyBold> retrieves only the diagnostic information most recently associated with the handle specified in the <legacyItalic>Handle</legacyItalic> argument. If the application calls another ODBC function, except <legacyBold>SQLGetDiagRec</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, or <legacyBold>SQLError</legacyBold>, any diagnostic information from the previous calls on the same handle is lost.</para>
      <para>An application can scan all diagnostic records by looping, incrementing <legacyItalic>RecNumber</legacyItalic>, as long as <legacyBold>SQLGetDiagRec</legacyBold> returns SQL_SUCCESS. Calls to <legacyBold>SQLGetDiagRec</legacyBold> are nondestructive to the header and record fields. The application can call <legacyBold>SQLGetDiagRec</legacyBold> again at a later time to retrieve a field from a record as long as no other function, except <legacyBold>SQLGetDiagRec</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, or <legacyBold>SQLError</legacyBold>, has been called in the interim. The application can also retrieve a count of the total number of diagnostic records available by calling <legacyBold>SQLGetDiagField</legacyBold> to retrieve the value of the SQL_DIAG_NUMBER field, and then calling <legacyBold>SQLGetDiagRec</legacyBold> that many times.</para>
      <para>For a description of the fields of the diagnostic data structure, see <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>. For more information, see <legacyLink xlink:href="4f486bb1-fad8-4064-ac9d-61f2de85b68b">Using SQLGetDiagRec and SQLGetDiagField</legacyLink> and <legacyLink xlink:href="11ba1857-b533-4517-8131-a2a8a0154a0a">Implementing SQLGetDiagRec and SQLGetDiagField</legacyLink>.</para>
      <para>Calling an API other than the one that’s being executed asynchronously will generate HY010 "Function sequence error". However, the error record cannot be retrieved before the asynchronous operation completes.</para>
    </content>
  </section>
  <section>
    <title>HandleType Argument</title>
    <content>
      <para>Each handle type can have diagnostic information associated with it. The <legacyItalic>HandleType</legacyItalic> argument denotes the handle type of the <legacyItalic>Handle </legacyItalic>argument. </para>
      <para>Some header and record fields cannot be returned for environment, connection, statement, and descriptor handles. Those handles for which a field is not applicable are indicated in the "Header Fields" and "Record Fields" sections in <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>. </para>
      <para>A call to <legacyBold>SQLGetDiagRec</legacyBold> will return SQL_INVALID_HANDLE if <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_SENV, which denotes a shared environment handle. However, if <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_ENV, <legacyItalic>Handle</legacyItalic> can be either a shared or an unshared environment handle.</para>
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
              <para>Obtaining a field of a diagnostic record or a field of the diagnostic header</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField Function</legacyLink>
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
<link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>