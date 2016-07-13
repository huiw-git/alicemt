---
title: SQLSetEnvAttr Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLSetEnvAttr
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetEnvAttr Function
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
          <legacyBold>SQLSetEnvAttr</legacyBold> sets attributes that govern aspects of environments.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLSetEnvAttr</legacyBold>(
     SQLHENV      <parameterReference>EnvironmentHandle</parameterReference>,
     SQLINTEGER   <parameterReference>Attribute</parameterReference>,
     SQLPOINTER   <parameterReference>ValuePtr</parameterReference>,
     SQLINTEGER   <parameterReference>StringLength</parameterReference>);</legacySyntax>
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
          <legacyItalic>Attribute</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Attribute to set, listed in "Comments."</para>
        </definition>
        <definedTerm>
          <legacyItalic>ValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to the value to be associated with <legacyItalic>Attribute</legacyItalic>. Depending on the value of <legacyItalic>Attribute</legacyItalic>, <legacyItalic>ValuePtr</legacyItalic> will be a 32-bit integer value or point to a null-terminated character string.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>ValuePtr</legacyItalic> points to a character string or a binary buffer, this argument should be the length of *<legacyItalic>ValuePtr</legacyItalic>. For character string data, this argument should contain the number of bytes in the string.</para>
          <para>If <legacyItalic>ValuePtr</legacyItalic> is an integer, <legacyItalic>StringLength</legacyItalic> is ignored.</para>
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
      <para>When <legacyBold>SQLSetEnvAttr</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>EnvironmentHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLSetEnvAttr</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise. If a driver does not support an environment attribute, the error can be returned only during connect time.</para>
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
              <para>01S02</para>
            </TD>
            <TD>
              <para>Option value changed</para>
            </TD>
            <TD>
              <para>The driver did not support the value specified in <legacyItalic>ValuePtr</legacyItalic> and substituted a similar value. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>The Attribute argument identified an environment attribute that required a string value, and the <legacyItalic>ValuePtr</legacyItalic> argument was a null pointer.</para>
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
              <para>(DM) A connection handle has been allocated on <legacyItalic>EnvironmentHandle</legacyItalic>.</para>
              <para>(DM) <system>SQL_ATTR_ODBC_VERSION</system> has not been set with <unmanagedCodeEntityReference>SQLSetEnvAttr</unmanagedCodeEntityReference> and <legacyItalic>Attribute</legacyItalic> is not equal to <system>SQL_ATTR_ODBC_VERSION</system>. You do not need to set <system>SQL_ATTR_ODBC_VERSION</system> explicitly if you are using <unmanagedCodeEntityReference>SQLAllocHandleStd</unmanagedCodeEntityReference>.</para>
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
              <para>HY024</para>
            </TD>
            <TD>
              <para>Invalid attribute value</para>
            </TD>
            <TD>
              <para>Given the specified <legacyItalic>Attribute</legacyItalic> value, an invalid value was specified in <legacyItalic>ValuePtr</legacyItalic>.</para>
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
              <para>The <legacyItalic>StringLength</legacyItalic> argument was less than 0 but was not SQL_NTS.</para>
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
              <para>(DM) The value specified for the argument <legacyItalic>Attribute</legacyItalic> was not valid for the version of ODBC supported by the driver.</para>
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
              <para>HYC00</para>
            </TD>
            <TD>
              <para>Optional feature not implemented</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>Attribute</legacyItalic> was a valid ODBC environment attribute for the version of ODBC supported by the driver, but was not supported by the driver.</para>
              <para>(DM) The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_OUTPUT_NTS, and <legacyItalic>ValuePtr</legacyItalic> was SQL_FALSE.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>An application can call <legacyBold>SQLSetEnvAttr</legacyBold> only if no connection handle is allocated on the environment. All environment attributes successfully set by the application for the environment persist until <legacyBold>SQLFreeHandle</legacyBold> is called on the environment. More than one environment handle can be allocated simultaneously in ODBC 3<legacyItalic>.x</legacyItalic>.</para>
      <para>The format of information set through <legacyItalic>ValuePtr</legacyItalic> depends on the specified <legacyItalic>Attribute</legacyItalic>. <legacyBold>SQLSetEnvAttr</legacyBold> will accept attribute information in one of two different formats: a null-terminated character string or a 32-bit integer value. The format of each is noted in the attribute's description.</para>
      <para>There are no driver-specific environment attributes.</para>
      <para>Connection attributes cannot be set by a call to <legacyBold>SQLSetEnvAttr</legacyBold>. Trying to do this will return SQLSTATE HY092 (Invalid attribute/option identifier).</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>Attribute</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>ValuePtr</legacyItalic> contents</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)</para>
            </TD>
            <TD>
              <para>A 32-bit SQLUINTEGER value that enables or disables connection pooling at the environment level. The following values are used:</para>
              <para>SQL_CP_OFF = Connection pooling is turned off. This is the default.</para>
              <para>SQL_CP_ONE_PER_DRIVER = A single connection pool is supported for each driver. Every connection in a pool is associated with one driver.</para>
              <para>SQL_CP_ONE_PER_HENV = A single connection pool is supported for each environment. Every connection in a pool is associated with one environment.</para>
              <para>SQL_CP_DRIVER_AWARE = Use the connection-pool awareness feature of the driver, if it is available. If the driver does not support connection-pool awareness, SQL_CP_DRIVER_AWARE is ignored and SQL_CP_ONE_PER_HENV is used. For more information, see <link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>. In an environment where some drivers support and some drivers do not support connection-pool awareness, SQL_CP_DRIVER_AWARE can enable the connection-pool awareness feature on those supporting drivers, but it is equivalent to setting to SQL_CP_ONE_PER_HENV on those drivers that do not support connection-pool awareness feature.</para>
              <para>Connection pooling is enabled by calling <legacyBold>SQLSetEnvAttr</legacyBold> to set the SQL_ATTR_CONNECTION_POOLING attribute to SQL_CP_ONE_PER_DRIVER or SQL_CP_ONE_PER_HENV. This call must be made before the application allocates the shared environment for which connection pooling is to be enabled. The environment handle in the call to <legacyBold>SQLSetEnvAttr</legacyBold> is set to null, which makes SQL_ATTR_CONNECTION_POOLING a process-level attribute. After connection pooling is enabled, the application then allocates an implicit shared environment by calling <legacyBold>SQLAllocHandle</legacyBold> with the <legacyItalic>InputHandle</legacyItalic> argument set to SQL_HANDLE_ENV.</para>
              <para>After connection pooling has been enabled and a shared environment has been selected for an application, SQL_ATTR_CONNECTION_POOLING cannot be reset for that environment, because <legacyBold>SQLSetEnvAttr</legacyBold> is called with a null environment handle when setting this attribute. If this attribute is set while connection pooling is already enabled on a shared environment, the attribute affects only shared environments that are allocated subsequently.</para>
              <para>It is also possible to enable connection pooling on an environment. Note the following about environment connection pooling:</para>
              <list class="bullet">
                <listItem>
                  <para>Enabling connection pooling on a NULL handle is a process-level attribute. Subsequently allocated environments will be a shared environment, and will inherit the process-level connection pooling setting.</para>
                </listItem>
                <listItem>
                  <para>After an environment is allocated, an application can still change its connection pool setting.</para>
                </listItem>
                <listItem>
                  <para>If environment connection pooling is enabled and the connection's driver uses driver pooling, environment pooling takes preference.</para>
                </listItem>
              </list>
              <para>SQL_ATTR_CONNECTION_POOLING is implemented inside the Driver Manager. A driver does not need to implement SQL_ATTR_CONNECTION_POOLING. ODBC 2.0 and 3.0 applications can set this environment attribute.</para>
              <para>For more information, see <legacyLink xlink:href="ee95ffdb-5aa1-49a3-beb2-7695b27c3df9">ODBC Connection Pooling</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CP_MATCH (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>A 32-bit SQLUINTEGER value that determines how a connection is chosen from a connection pool. When <legacyBold>SQLConnect</legacyBold> or <legacyBold>SQLDriverConnect</legacyBold> is called, the Driver Manager determines which connection is reused from the pool. The Driver Manager tries to match the connection options in the call and the connection attributes set by the application to the keywords and connection attributes of the connections in the pool. The value of this attribute determines the level of precision of the matching criteria.</para>
              <para>The following values are used to set the value of this attribute:</para>
              <para>SQL_CP_STRICT_MATCH = Only connections that exactly match the connection options in the call and the connection attributes set by the application are reused. This is the default.</para>
              <para>SQL_CP_RELAXED_MATCH = Connections with matching connection string keywords can be used. Keywords must match, but not all connection attributes must match.</para>
              <para>For more information about how the Driver Manager performs the match in connecting to a pooled connection, see <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink>. For more information about connection pooling, see <legacyLink xlink:href="ee95ffdb-5aa1-49a3-beb2-7695b27c3df9">ODBC Connection Pooling</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ODBC_VERSION (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>A 32-bit integer that determines whether certain functionality exhibits ODBC 2<legacyItalic>.x</legacyItalic> behavior or ODBC 3<legacyItalic>.x</legacyItalic> behavior. The following values are used to set the value of this attribute:</para>
              <para>SQL_OV_ODBC3_80 = The Driver Manager and driver exhibit the following ODBC 3.8 behavior:</para>
              <list class="bullet">
                <listItem>
                  <para>The driver returns and expects ODBC 3.<legacyItalic>x</legacyItalic> codes for date, time, and timestamp.</para>
                </listItem>
                <listItem>
                  <para>The driver returns ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATE codes when <legacyBold>SQLError</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, or <legacyBold>SQLGetDiagRec</legacyBold> is called.</para>
                </listItem>
                <listItem>
                  <para>The <legacyItalic>CatalogName</legacyItalic> argument in a call to <legacyBold>SQLTables</legacyBold> accepts a search pattern. </para>
                </listItem>
                <listItem>
                  <para>The Driver Manager supports C data type extensibility. For more information about C data type extensibility, see <link xlink:href="c91bef31-3794-4736-966a-d50997b2233c">C Data Types in ODBC</link>.</para>
                </listItem>
              </list>
              <para>For more information, see <link xlink:href="854f0bb4-17e9-489b-9595-eefffb8ba99f">What's New in ODBC 3.8</link>.</para>
              <para>SQL_OV_ODBC3 = The Driver Manager and driver exhibit the following ODBC 3<legacyItalic>.x</legacyItalic> behavior:  </para>
              <list class="bullet">
                <listItem>
                  <para>The driver returns and expects ODBC 3<legacyItalic>.x</legacyItalic> codes for date, time, and timestamp.</para>
                </listItem>
                <listItem>
                  <para>The driver returns ODBC 3<legacyItalic>.x</legacyItalic> SQLSTATE codes when <legacyBold>SQLError</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, or <legacyBold>SQLGetDiagRec</legacyBold> is called.</para>
                </listItem>
                <listItem>
                  <para>The <legacyItalic>CatalogName</legacyItalic> argument in a call to <legacyBold>SQLTables</legacyBold> accepts a search pattern.</para>
                </listItem>
                <listItem>
                  <para>The Driver Manager does not support C data type extensibility.</para>
                </listItem>
              </list>
              <para>SQL_OV_ODBC2 = The Driver Manager and driver exhibit the following ODBC 2<legacyItalic>.x </legacyItalic>behavior. This is especially useful for an ODBC 2<legacyItalic>.x</legacyItalic> application working with an ODBC 3<legacyItalic>.x</legacyItalic> driver.  </para>
              <list class="bullet">
                <listItem>
                  <para>The driver returns and expects ODBC 2<legacyItalic>.x</legacyItalic> codes for date, time, and timestamp.</para>
                </listItem>
                <listItem>
                  <para>The driver returns ODBC 2<legacyItalic>.x</legacyItalic> SQLSTATE codes when <legacyBold>SQLError</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, or <legacyBold>SQLGetDiagRec</legacyBold> is called.</para>
                </listItem>
                <listItem>
                  <para>The <legacyItalic>CatalogName</legacyItalic> argument in a call to <legacyBold>SQLTables</legacyBold> does not accept a search pattern.</para>
                </listItem>
                <listItem>
                  <para>The Driver Manager does not support C data type extensibility.</para>
                </listItem>
              </list>
              <para>An application must set this environment attribute before it calls any function that has an SQLHENV argument, or the call will return SQLSTATE HY010 (Function sequence error). It is driver-specific whether additional behavior exists for these environmental flags.</para>
              <list class="bullet">
                <listItem>
                  <para>For more information, see <legacyLink xlink:href="083a1ef5-580a-4979-9cf3-50f4549a080a">Declaring the Application's ODBC Version</legacyLink> and <legacyLink xlink:href="a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67">Behavioral Changes</legacyLink>.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_OUTPUT_NTS (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>A 32-bit integer that determines how the driver returns string data. If SQL_TRUE, the driver returns string data null-terminated. If SQL_FALSE, the driver does not return string data null-terminated.</para>
              <para>This attribute defaults to SQL_TRUE. A call to <legacyBold>SQLSetEnvAttr</legacyBold> to set it to SQL_TRUE returns SQL_SUCCESS. A call to <legacyBold>SQLSetEnvAttr</legacyBold> to set it to SQL_FALSE returns SQL_ERROR and SQLSTATE HYC00 (Optional feature not implemented).</para>
            </TD>
          </tr>
        </tbody>
      </table>
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
              <para>Allocating a handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the setting of an environment attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="01f4590f-427a-4280-a1c3-18de9f7d86c1">SQLGetEnvAttr Function</legacyLink>
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
<link xlink:href="854f0bb4-17e9-489b-9595-eefffb8ba99f">What's New in ODBC 3.8</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>