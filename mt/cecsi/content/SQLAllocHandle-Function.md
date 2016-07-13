---
title: SQLAllocHandle Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLAllocHandle
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 6e7fe420-8cf4-4e72-8dad-212affaff317
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLAllocHandle Function
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
          <legacyBold>SQLAllocHandle</legacyBold> allocates an environment, connection, statement, or descriptor handle.</para>
        <alert class="note">
          <para>This function is a generic function for allocating handles that replaces the ODBC 2.0 functions <legacyBold>SQLAllocConnect</legacyBold>, <legacyBold>SQLAllocEnv</legacyBold>, and<legacyBold> SQLAllocStmt</legacyBold>. To allow applications calling <legacyBold>SQLAllocHandle</legacyBold> to work with ODBC 2.<legacyItalic>x</legacyItalic> drivers, a call to <legacyBold>SQLAllocHandle</legacyBold> is mapped in the Driver Manager to <legacyBold>SQLAllocConnect</legacyBold>, <legacyBold>SQLAllocEnv</legacyBold>, or<legacyBold> SQLAllocStmt</legacyBold>, as appropriate. For more information, see "Comments." For more information about what the Driver Manager maps this function to when an ODBC 3.<legacyItalic>x</legacyItalic> application is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, see <legacyLink xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</legacyLink>.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLAllocHandle</legacyBold>(
      SQLSMALLINT   <parameterReference>HandleType</parameterReference>,
      SQLHANDLE     <parameterReference>InputHandle</parameterReference>,
      SQLHANDLE *   <parameterReference>OutputHandlePtr</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>HandleType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The type of handle to be allocated by <legacyBold>SQLAllocHandle</legacyBold>. Must be one of the following values:</para>
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
          <legacyItalic>InputHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The input handle in whose context the new handle is to be allocated. If <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_ENV, this is SQL_NULL_HANDLE. If <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_DBC, this must be an environment handle, and if it is SQL_HANDLE_STMT or SQL_HANDLE_DESC, it must be a connection handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>OutputHandlePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the handle to the newly allocated data structure.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_INVALID_HANDLE, or SQL_ERROR.</para>
      <para>When allocating a handle other than an environment handle, if <legacyBold>SQLAllocHandle </legacyBold>returns SQL_ERROR, it sets <legacyItalic>OutputHandlePtr</legacyItalic> to SQL_NULL_HDBC, SQL_NULL_HSTMT, or SQL_NULL_HDESC, depending on the value of <legacyItalic>HandleType</legacyItalic>, unless the output argument is a null pointer. The application can then obtain additional information from the diagnostic data structure associated with the handle in the <legacyItalic>InputHandle</legacyItalic> argument.</para>
    </content>
  </section>
  <section>
    <title>Environment Handle Allocation Errors</title>
    <content>
      <para>Environment allocation occurs both within the Driver Manager and within each driver. The error returned by <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV depends on the level in which the error occurred.</para>
      <para>If the Driver Manager cannot allocate memory for <legacyItalic>*OutputHandlePtr</legacyItalic> when <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV is called, or the application provides a null pointer for <legacyItalic>OutputHandlePtr</legacyItalic>, <legacyBold>SQLAllocHandle </legacyBold>returns SQL_ERROR. The Driver Manager sets *<legacyItalic>OutputHandlePtr</legacyItalic> to SQL_NULL_HENV (unless the application provided a null pointer, which returns SQL_ERROR). There is no handle with which to associate additional diagnostic information.</para>
      <para>The Driver Manager does not call the driver-level environment handle allocation function until the application calls <legacyBold>SQLConnect</legacyBold>,<legacyBold> SQLBrowseConnect</legacyBold>, or <legacyBold>SQLDriverConnect</legacyBold>. If an error occurs in the driver-level <legacyBold>SQLAllocHandle</legacyBold> function, then the Driver Manager–level <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLBrowseConnect</legacyBold>, or <legacyBold>SQLDriverConnect</legacyBold> function returns SQL_ERROR. The diagnostic data structure contains SQLSTATE IM004 (Driver's <legacyBold>SQLAllocHandle</legacyBold> failed). The error is returned on a connection handle.</para>
      <para>For more information about the flow of function calls between the Driver Manager and a driver, see <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLAllocHandle</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with the appropriate <legacyItalic>HandleType</legacyItalic> and <legacyItalic>Handle</legacyItalic> set to the value of <legacyItalic>InputHandle</legacyItalic>. SQL_SUCCESS_WITH_INFO (but not SQL_ERROR) can be returned for the <legacyItalic>OutputHandle</legacyItalic> argument. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLAllocHandle</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>08003</para>
            </TD>
            <TD>
              <para>Connection not open</para>
            </TD>
            <TD>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_STMT or SQL_HANDLE_DESC, but the connection specified by the <legacyItalic>InputHandle</legacyItalic> argument was not open. The connection process must be completed successfully (and the connection must be open) for the driver to allocate a statement or descriptor handle. </para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the *<legacyItalic>MessageText</legacyItalic> buffer describes the error and its cause.</para>
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
              <para>(DM) The Driver Manager was unable to allocate memory for the specified handle.</para>
              <para>The driver was unable to allocate memory for the specified handle.</para>
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
              <para>(DM) The <legacyItalic>OutputHandlePtr</legacyItalic> argument was a null pointer.</para>
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
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_DBC, and <legacyBold>SQLSetEnvAttr</legacyBold> has not been called to set the SQL_ODBC_VERSION environment attribute.</para>
              <para>(DM) An asynchronously executing function was called for the <unmanagedCodeEntityReference>InputHandle</unmanagedCodeEntityReference> and was still executing when the <unmanagedCodeEntityReference>SQLAllocHandle</unmanagedCodeEntityReference> function was called with <unmanagedCodeEntityReference>HandleType</unmanagedCodeEntityReference> set to SQL_HANDLE_STMT or SQL_HANDLE_DESC.</para>
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
              <para>The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_DBC, SQL_HANDLE_STMT, or SQL_HANDLE_DESC; and the function call could not be processed because the underlying memory objects could not be accessed, possibly because of low memory conditions.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY014</para>
            </TD>
            <TD>
              <para>Limit on the number of handles exceeded</para>
            </TD>
            <TD>
              <para>The driver-defined limit for the number of handles that can be allocated for the type of handle indicated by the <legacyItalic>HandleType</legacyItalic> argument has been reached.</para>
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
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was not: SQL_HANDLE_ENV, SQL_HANDLE_DBC, SQL_HANDLE_STMT, or SQL_HANDLE_DESC.</para>
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
              <para>The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_DESC and the driver was an ODBC 2.<legacyItalic>x</legacyItalic> driver.</para>
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
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_STMT, and the driver was not a valid ODBC driver.</para>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_DESC, and the driver does not support allocating a descriptor handle.</para>
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
        <legacyBold>SQLAllocHandle</legacyBold> is used to allocate handles for environments, connections, statements, and descriptors, as described in the following sections. For general information about handles, see <legacyLink xlink:href="f663101e-a4cc-402b-b9d7-84d5e975be71">Handles</legacyLink>.</para>
      <para>More than one environment, connection, or statement handle can be allocated by an application at a time if multiple allocations are supported by the driver. In ODBC, no limit is defined on the number of environment, connection, statement, or descriptor handles that can be allocated at any one time. Drivers may impose a limit on the number of a certain type of handle that can be allocated at a time; for more information, see the driver documentation.</para>
      <para>If the application calls <legacyBold>SQLAllocHandle</legacyBold> with <legacyItalic>*OutputHandlePtr</legacyItalic> set to an environment, connection, statement, or descriptor handle that already exists, the driver overwrites the information associated with the <legacyItalic>handle</legacyItalic>, unless the application is using connection pooling (see "Allocating an Environment Attribute for Connection Pooling" later in this section). The Driver Manager does not check to see whether the <legacyItalic>handle </legacyItalic>entered in <legacyItalic>*OutputHandlePtr</legacyItalic> is already being used, nor does it check the previous contents of a handle before overwriting them.</para>
      <alert class="note">
        <para>It is incorrect ODBC application programming to call <legacyBold>SQLAllocHandle</legacyBold> two times with the same application variable defined for <legacyItalic>*OutputHandlePtr</legacyItalic> without calling <legacyBold>SQLFreeHandle</legacyBold> to free the handle before reallocating it. Overwriting ODBC handles in such a manner could lead to inconsistent behavior or errors on the part of ODBC drivers.</para>
      </alert>
      <para>On operating systems that support multiple threads, applications can use the same environment, connection, statement, or descriptor handle on different threads. Drivers must therefore support safe, multithread access to this information; one way to achieve this, for example, is by using a critical section or a semaphore. For more information about threading, see <legacyLink xlink:href="cdfebdf5-12ff-4e28-8055-41f49b77f664">Multithreading</legacyLink>.</para>
      <para>
        <legacyBold>SQLAllocHandle</legacyBold> does not set the SQL_ATTR_ODBC_VERSION environment attribute when it is called to allocate an environment handle; the environment attribute must be set by the application, or SQLSTATE HY010 (Function sequence error) will be returned when <legacyBold>SQLAllocHandle</legacyBold> is called to allocate a connection handle.</para>
      <para>For standards-compliant applications, <legacyBold>SQLAllocHandle</legacyBold> is mapped to <legacyBold>SQLAllocHandleStd</legacyBold> at compile time. The difference between these two functions is that <legacyBold>SQLAllocHandleStd</legacyBold> sets the SQL_ATTR_ODBC_VERSION environment attribute to SQL_OV_ODBC3 when it is called with the <legacyItalic>HandleType</legacyItalic> argument set to SQL_HANDLE_ENV. This is done because standards-compliant applications are always ODBC 3.<legacyItalic>x</legacyItalic> applications. Moreover, the standards do not require the application version to be registered. This is the only difference between these two functions; otherwise, they are identical. <legacyBold>SQLAllocHandleStd</legacyBold> is mapped to <legacyBold>SQLAllocHandle</legacyBold> inside the driver manager. Therefore, third-party drivers do not have to implement <legacyBold>SQLAllocHandleStd</legacyBold>. </para>
      <para>ODBC 3.8 applications should use:</para>
      <list class="bullet">
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLAllocHandle and not SQLAllocHandleStd</unmanagedCodeEntityReference> to allocate an environment handle.</para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLSetEnvAttr</unmanagedCodeEntityReference> to set the SQL_ATTR_ODBC_VERSION environment attribute to SQL_OV_ODBC3_80.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Allocating an Environment Handle</title>
    <content>
      <para>An environment handle provides access to global information such as valid connection handles and active connection handles. For general information about environment handles, see <legacyLink xlink:href="917f1b0c-272b-4e37-a1f5-87cd24b9fa21">Environment Handles</legacyLink>.</para>
      <para>To request an environment handle, an application calls <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV and an <legacyItalic>InputHandle</legacyItalic> of SQL_NULL_HANDLE. The driver allocates memory for the environment information and passes the value of the associated handle back in the <legacyItalic>*OutputHandlePtr</legacyItalic> argument. The application passes the <legacyItalic>*OutputHandle</legacyItalic> value in all subsequent calls that require an environment handle argument. For more information, see <legacyLink xlink:href="77b5d1d6-7eb7-428d-bf75-a5c5a325d25c">Allocating the Environment Handle</legacyLink>.</para>
      <para>Under a Driver Manager's environment handle, if there already exists a driver's environment handle, then <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV is not called in that driver when a connection is made, only <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC. If a driver's environment handle does not exist under the Driver Manager's environment handle, both SQLAllocHandle with a HandleType of SQL_HANDLE_ENV and SQLAllocHandle with a HandleType of SQL_HANDLE_DBC are called in the driver when the first connection handle of the environment is connected to the driver.</para>
      <para>When the Driver Manager processes the <legacyBold>SQLAllocHandle</legacyBold> function with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV, it checks the <legacyBold>Trace</legacyBold> keyword in the [ODBC] section of the system information. If it is set to 1, the Driver Manager enables tracing for the current application. If the trace flag is set, tracing starts when the first environment handle is allocated and ends when the last environment handle is freed. For more information, see <legacyLink xlink:href="f11985c2-c054-4ab4-840e-aca4c585c9d8">Configuring Data Sources</legacyLink>.</para>
      <para>After allocating an environment handle, an application must call <legacyBold>SQLSetEnvAttr</legacyBold> on the environment handle to set the SQL_ATTR_ODBC_VERSION environment attribute. If this attribute is not set before <legacyBold>SQLAllocHandle</legacyBold> is called to allocate a connection handle on the environment, the call to allocate the connection will return SQLSTATE HY010 (Function sequence error). For more information, see <legacyLink xlink:href="083a1ef5-580a-4979-9cf3-50f4549a080a">Declaring the Application's ODBC Version</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Allocating Shared Environments for Connection Pooling</title>
    <content>
      <para>Environments can be shared among multiple components on a single process. A shared environment can be used by more than one component at the same time. When a component uses a shared environment, it can use pooled connections, which allow it to allocate and use an existing connection without re-creating that connection.</para>
      <para>Before allocating a shared environment that can be used for connection pooling, an application must call <legacyBold>SQLSetEnvAttr</legacyBold> to set the SQL_ATTR_CONNECTION_POOLING environment attribute to SQL_CP_ONE_PER_DRIVER or SQL_CP_ONE_PER_HENV. <legacyBold>SQLSetEnvAttr</legacyBold> in this case is called with <legacyItalic>EnvironmentHandle</legacyItalic> set to null, which makes the attribute a process-level attribute.</para>
      <para>After connection pooling has been enabled, an application calls <legacyBold>SQLAllocHandle</legacyBold> with the <legacyItalic>HandleType</legacyItalic> argument set to SQL_HANDLE_ENV. The environment allocated by this call will be an implicit shared environment because connection pooling has been enabled.</para>
      <para>When a shared environment is allocated, the environment that will be used is not determined until <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC is called. At that point, the Driver Manager tries to find an existing environment that matches the environment attributes requested by the application. If no such environment exists, one is created as a shared environment. The Driver Manager maintains a reference count for each shared environment; the count is set to 1 when the environment is first created. If a matching environment is found, the handle of that environment is returned to the application and the reference count is incremented. An environment handle allocated in this manner can be used in any ODBC function that accepts an environment handle as an input argument.</para>
    </content>
  </section>
  <section>
    <title>Allocating a Connection Handle</title>
    <content>
      <para>A connection handle provides access to information such as the valid statement and descriptor handles on the connection and whether a transaction is currently open. For general information about connection handles, see <legacyLink xlink:href="12222653-f04d-46d6-bdee-61348f5d550f">Connection Handles</legacyLink>.</para>
      <para>To request a connection handle, an application calls <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC. The <legacyItalic>InputHandle</legacyItalic> argument is set to the environment handle that was returned by the call to <legacyBold>SQLAllocHandle</legacyBold> that allocated that handle. The driver allocates memory for the connection information and passes the value of the associated handle back in <legacyItalic>*OutputHandlePtr</legacyItalic>. The application passes the <legacyItalic>*OutputHandlePtr</legacyItalic> value in all subsequent calls that require a connection handle. For more information, see <legacyLink xlink:href="c99a8159-7693-4f97-8dcf-401336550e77">Allocating a Connection Handle</legacyLink>.</para>
      <para>The Driver Manager processes the <legacyBold>SQLAllocHandle</legacyBold> function and calls the driver's <legacyBold>SQLAllocHandle</legacyBold> function when the application calls <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLBrowseConnect</legacyBold>, or <legacyBold>SQLDriverConnect</legacyBold>. (For more information, see <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>.)</para>
      <para>If the SQL_ATTR_ODBC_VERSION environment attribute is not set before <legacyBold>SQLAllocHandle</legacyBold> is called to allocate a connection handle on the environment, the call to allocate the connection will return SQLSTATE HY010 (Function sequence error).</para>
      <para>When an application calls <legacyBold>SQLAllocHandle</legacyBold> with the <legacyItalic>InputHandle</legacyItalic> argument set to SQL_HANDLE_DBC and also set to a shared environment handle, the Driver Manager tries to find an existing shared environment that matches the environment attributes set by the application. If no such environment exists, one is created, with a reference count (maintained by the Driver Manager) of 1. If a matching shared environment is found, that handle is returned to the application and its reference count is incremented.</para>
      <para>The actual connection that will be used is not determined by the Driver Manager until <legacyBold>SQLConnect</legacyBold> or <legacyBold>SQLDriverConnect</legacyBold> is called. The Driver Manager uses the connection options in the call to <legacyBold>SQLConnect</legacyBold> (or the connection keywords in the call to <legacyBold>SQLDriverConnect</legacyBold>) and the connection attributes set after connection allocation to determine which connection in the pool should be used. For more information, see <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Allocating a Statement Handle</title>
    <content>
      <para>A statement handle provides access to statement information, such as error messages, the cursor name, and status information for SQL statement processing. For general information about statement handles, see <legacyLink xlink:href="65d6d78b-a8c8-489a-9dad-f8d127a44882">Statement Handles</legacyLink>.</para>
      <para>To request a statement handle, an application connects to a data source and then calls <legacyBold>SQLAllocHandle</legacyBold> before it submits SQL statements. In this call, <legacyItalic>HandleType</legacyItalic> should be set to SQL_HANDLE_STMT and <legacyItalic>InputHandle</legacyItalic> should be set to the connection handle that was returned by the call to <legacyBold>SQLAllocHandle</legacyBold> that allocated that handle. The driver allocates memory for the statement information, associates the statement handle with the specified connection, and passes the value of the associated handle back in <legacyItalic>*OutputHandlePtr</legacyItalic>. The application passes the <legacyItalic>*OutputHandlePtr</legacyItalic> value in all subsequent calls that require a statement handle. For more information, see <legacyLink xlink:href="4ce3b446-34ab-46dc-96e5-f40ec95c267e">Allocating a Statement Handle</legacyLink>.</para>
      <para>When the statement handle is allocated, the driver automatically allocates a set of four descriptors and assigns the handles for these descriptors to the SQL_ATTR_APP_ROW_DESC, SQL_ATTR_APP_PARAM_DESC, SQL_ATTR_IMP_ROW_DESC, and SQL_ATTR_IMP_PARAM_DESC statement attributes. These are referred to as <legacyItalic>implicitly</legacyItalic> allocated descriptors. To allocate an application descriptor explicitly, see the following section, "Allocating a Descriptor Handle."</para>
    </content>
  </section>
  <section>
    <title>Allocating a Descriptor Handle</title>
    <content>
      <para>When an application calls <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DESC, the driver allocates an application descriptor. These are referred to as <legacyItalic>explicitly</legacyItalic> allocated descriptors. The application directs a driver to use an explicitly allocated application descriptor instead of an automatically allocated one for a given statement handle by calling the <legacyBold>SQLSetStmtAttr</legacyBold> function with the SQL_ATTR_APP_ROW_DESC or SQL_ATTR_APP_PARAM_DESC attribute. An implementation descriptor cannot be allocated explicitly, nor can an implementation descriptor be specified in an <legacyBold>SQLSetStmtAttr</legacyBold> function call.</para>
      <para>Explicitly allocated descriptors are associated with a connection handle instead of a statement handle (as automatically allocated descriptors are). Descriptors remain allocated only when an application is actually connected to the database. Because explicitly allocated descriptors are associated with a connection handle, an application can associate an explicitly allocated descriptor with more than one statement within a connection. An implicitly allocated application descriptor, on the other hand, cannot be associated with more than one statement handle. (It cannot be associated with any statement handle other than the one that it was allocated for.) Explicitly allocated descriptor handles can be freed explicitly either by the application or by calling <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DESC, or implicitly when the connection is closed.</para>
      <para>When the explicitly allocated descriptor is freed, the implicitly allocated descriptor is again associated with the statement. (The SQL_ATTR_APP_ROW_DESC or SQL_ATTR_APP_PARAM_DESC attribute for that statement is again set to the implicitly allocated descriptor handle.) This is true for all statements that were associated with the explicitly allocated descriptor on the connection.</para>
      <para>For more information about descriptors, see <legacyLink xlink:href="ef2cbb93-cd00-40f8-b1d2-5f5723a991aa">Descriptors</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>See <link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link>, <legacyLink xlink:href="b7f1be66-e6c7-4790-88ec-62b7662103c0">SQLBrowseConnect Function</legacyLink>, <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>, and <legacyLink xlink:href="4e055946-12d4-4589-9891-41617a50f34e">SQLSetCursorName Function</legacyLink>.</para>
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
              <para>Freeing an environment, connection, statement, or descriptor handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preparing a statement for execution</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a connection attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a descriptor field</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting an environment attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a statement attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr Function</legacyLink>
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