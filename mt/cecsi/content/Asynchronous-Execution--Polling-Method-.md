---
title: Asynchronous Execution (Polling Method)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cd21734-ef8e-4066-afd5-1f340e213f9c
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Asynchronous Execution (Polling Method)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Prior to ODBC 3.8 and the Windows 7 SDK, asynchronous operations were permitted only on statement functions. For more information, see the <embeddedLabel>Executing Statement Operations Asynchronously</embeddedLabel>, later in this topic.</para>
    <para>ODBC 3.8 in the Windows 7 SDK introduced asynchronous execution on connection-related operations. For more information, see the <embeddedLabel>Executing Connection Operations Asynchronously</embeddedLabel> section, later in this topic.</para>
    <para>In the Windows 7 SDK, for asynchronous statement or connection operations, an application determined that the asynchronous operation was complete using the polling method. Beginning in the Windows 8 SDK, you can determine that an asynchronous operation is complete using the notification method. For more information, see <link xlink:href="e509dad9-5263-4a10-9a4e-03b84b66b6b3">Asynchronous Execution (Notification Method)</link>.</para>
    <para>By default, drivers execute ODBC functions synchronously; that is, the application calls a function and the driver does not return control to the application until it has finished executing the function. However, some functions can be executed asynchronously; that is, the application calls the function, and the driver, after minimal processing, returns control to the application. The application can then call other functions while the first function is still executing.</para>
    <para>Asynchronous execution is supported for most functions that are largely executed on the data source, such as the functions to establish connections, prepare and execute SQL statements, retrieve metadata, fetch data, and commit transactions. It is most useful when the task being executed on the data source takes a long time, such as a login process or a complex query against a large database.</para>
    <para>When the application executes a function with a statement or connection that is enabled for asynchronous processing, the driver performs a minimal amount of processing (such as checking arguments for errors), hands processing to the data source, and returns control to the application with the SQL_STILL_EXECUTING return code. The application then performs other tasks. To determine when the asynchronous function has finished, the application polls the driver at regular intervals by calling the function with the same arguments as it originally used. If the function is still executing, it returns SQL_STILL_EXECUTING; if it has finished executing, it returns the code it would have returned had it executed synchronously, such as SQL_SUCCESS, SQL_ERROR, or SQL_NEED_DATA.</para>
    <para>Whether a function executes synchronously or asynchronously is driver specific. For example, suppose the result set metadata is cached in the driver. In this case, it takes very little time to execute <unmanagedCodeEntityReference>SQLDescribeCol</unmanagedCodeEntityReference> and the driver should simply execute the function rather than artificially delay execution. On the other hand, if the driver needs to retrieve the metadata from the data source, it should return control to the application while it is doing this. Therefore, the application must be able to handle a return code other than SQL_STILL_EXECUTING when it first executes a function asynchronously.</para>
  </introduction>
  <section>
    <title>Executing Statement Operations Asynchronously</title>
    <content>
      <para>The following statement functions operate on a data source and can execute asynchronously:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="8c45c598-cb01-4789-a571-e93619a18ed9">SQLColAttribute</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ef233d9a-6ed5-4986-9d42-5e0b1a79fb6e">SQLColumnPrivileges</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0">SQLColumns</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="eddef353-83f3-4a3c-8f24-f9ed888890a4">SQLDescribeCol</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="1f5b63c4-2f3e-44da-b155-876405302281">SQLDescribeParam</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="07f3f645-f643-4d39-9a10-70a72f24e608">SQLForeignKeys</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="bdedb044-8924-4ca4-85f3-8b37578e0257">SQLGetTypeInfo</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="bf169ed5-4d55-412c-b184-12065a726e89">SQLMoreResults</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="dbf2da44-253b-4094-bd6b-29bafc23c7a3">SQLNumParams</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="d863179f-12a9-4b55-ac6b-7d84202d3da3">SQLNumResultCols</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="68fe010d-9539-4e5b-a260-c8d32423b1db">SQLParamData</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="3f809b09-3c1b-415e-80c5-a603e8e25d5b">SQLPrimaryKeys</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="4ca37b28-a6df-465b-8988-d422d37fc025">SQLProcedureColumns</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="d0d9ef10-2fd4-44a5-9334-649f186f4ba0">SQLProcedures</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="bb2d9f21-bda0-4e50-a8be-f710db660034">SQLSpecialColumns</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="45210682-cfea-4e5d-9951-bcf1cbe10f41">SQLStatistics</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="8cfdb64f-64c5-47e6-ad57-0533ac630afa">SQLTablePrivileges</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="60d5068a-7d7c-447c-acc6-f3f2cf73440c">SQLTables</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Asynchronous statement execution is controlled on either a per-statement or a per-connection basis, depending on the data source. That is, the application specifies not that a particular function is to be executed asynchronously, but that any function executed on a particular statement is to be executed asynchronously. To find out which one is supported, an application calls <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> with an option of SQL_ASYNC_MODE. SQL_AM_CONNECTION is returned if connection-level asynchronous execution (for a statement handle) is supported; SQL_AM_STATEMENT if statement-level asynchronous execution is supported.</para>
      <para>To specify that functions executed with a particular statement are to be executed asynchronously, the application calls <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_ASYNC_ENABLE attribute and sets it to SQL_ASYNC_ENABLE_ON. If connection-level asynchronous processing is supported, the SQL_ATTR_ASYNC_ENABLE statement attribute is read-only and its value is the same as the connection attribute of the connection on which the statement was allocated. It is driver-specific whether the value of the statement attribute is set at statement allocation time or later. Attempting to set it will return SQL_ERROR and SQLSTATE HYC00 (Optional feature not implemented).</para>
      <para>To specify that functions executed with a particular connection are to be executed asynchronously, the application calls <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_ASYNC_ENABLE attribute and sets it to SQL_ASYNC_ENABLE_ON. All future statement handles allocated on the connection will be enabled for asynchronous execution; it is driver-defined whether existing statement handles will be enabled by this action. If SQL_ATTR_ASYNC_ENABLE is set to SQL_ASYNC_ENABLE_OFF, all statements on the connection are in synchronous mode. An error is returned if asynchronous execution is enabled while there is an active statement on the connection.</para>
      <para>To determine the maximum number of active concurrent statements in asynchronous mode that the driver can support on a given connection, the application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_MAX_ASYNC_CONCURRENT_STATEMENTS option.</para>
      <para>The following code demonstrates how the polling model works:</para>
      <code>SQLHSTMT  hstmt1;
SQLRETURN rc;

// Specify that the statement is to be executed asynchronously.
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);

// Execute a SELECT statement asynchronously.
while ((rc=SQLExecDirect(hstmt1,"SELECT * FROM Orders",SQL_NTS))==SQL_STILL_EXECUTING) {
   // While the statement is still executing, do something else.
   // Do not use hstmt1, because it is being used asynchronously.
}

// When the statement has finished executing, retrieve the results.</code>
      <para>While a function is executing asynchronously, the application can call functions on any other statements. The application can also call functions on any connection, except the one associated with the asynchronous statement. But the application can only call the original function and the following functions (with the statement handle or its associated connection, environment handle), after a statement operation returns SQL_STILL_EXECUTING:</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle</legacyLink> (on the statement handle)</para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="ebdbac93-3d68-438f-8416-ef1f08e04269">SQLGetDiagRec</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="01f4590f-427a-4280-a1c3-18de9f7d86c1">SQLGetEnvAttr</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="3f63b1b4-e70e-44cd-96c6-6878d50d0117">SQLDataSources</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa">SQLDrivers</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="0451d2f9-0f4f-46ba-b252-670956a52183">SQLGetFunctions</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="b8efc247-27ab-4a00-92b6-1400785783fe">SQLNativeSql</legacyLink>
          </para>
        </listItem>
      </list>
      <para>If the application calls any other function with the asynchronous statement or with the connection associated with that statement, the function returns SQLSTATE HY010 (Function sequence error), for example.</para>
      <code>SQLHDBC       hdbc1, hdbc2;
SQLHSTMT      hstmt1, hstmt2, hstmt3;
SQLCHAR *     SQLStatement = "SELECT * FROM Orders";
SQLUINTEGER   InfoValue;
SQLRETURN     rc;

SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &amp;hstmt1);
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &amp;hstmt2);
SQLAllocHandle(SQL_HANDLE_STMT, hdbc2, &amp;hstmt3);

// Specify that hstmt1 is to be executed asynchronously.
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);

// Execute hstmt1 asynchronously.
while ((rc = SQLExecDirect(hstmt1, SQLStatement, SQL_NTS)) == SQL_STILL_EXECUTING) {
   // The following calls return HY010 because the previous call to
   // SQLExecDirect is still executing asynchronously on hstmt1. The
   // first call uses hstmt1 and the second call uses hdbc1, on which
   // hstmt1 is allocated.
   SQLExecDirect(hstmt1, SQLStatement, SQL_NTS);   // Error!
   SQLGetInfo(hdbc1, SQL_UNION, (SQLPOINTER) &amp;InfoValue, 0, NULL);   // Error!

   // The following calls do not return errors. They use a statement
   // handle other than hstmt1 or a connection handle other than hdbc1.
   SQLExecDirect(hstmt2, SQLStatement, SQL_NTS);   // OK
   SQLTables(hstmt3, NULL, 0, NULL, 0, NULL, 0, NULL, 0);   // OK
   SQLGetInfo(hdbc2, SQL_UNION, (SQLPOINTER) &amp;InfoValue, 0, NULL);   // OK
}</code>
      <para>When an application calls a function to determine whether it is still executing asynchronously, it must use the original statement handle. This is because asynchronous execution is tracked on a per-statement basis. The application must also supply valid values for the other arguments — the original arguments will do — to get past error checking in the Driver Manager. However, after the driver checks the statement handle and determines that the statement is executing asynchronously, it ignores all other arguments.</para>
      <para>While a function is executing asynchronously — that is, after it has returned SQL_STILL_EXECUTING and before it returns a different code — the application can cancel it by calling <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> with the same statement handle. This is not guaranteed to cancel function execution. For example, the function might have already finished. Furthermore, the code returned by <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> only indicates whether the attempt to cancel the function was successful, not whether it actually canceled the function. To determine whether the function was canceled, the application calls the function again. If the function was canceled, it returns SQL_ERROR and SQLSTATE HY008 (Operation canceled). If the function was not canceled, it returns another code, such as SQL_SUCCESS, SQL_STILL_EXECUTING, or SQL_ERROR with a different SQLSTATE.</para>
      <para>To disable asynchronous execution of a particular statement when the driver supports statement-level asynchronous processing, the application calls <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_ASYNC_ENABLE attribute and sets it to SQL_ASYNC_ENABLE_OFF. If the driver supports connection-level asynchronous processing, the application calls <legacyBold>SQLSetConnectAttr</legacyBold> to set SQL_ATTR_ASYNC_ENABLE to SQL_ASYNC_ENABLE_OFF, which disables asynchronous execution of all statements on the connection.</para>
      <para>The application should process diagnostic records in the repeating loop of the original function. If <legacyBold>SQLGetDiagField</legacyBold> or <legacyBold>SQLGetDiagRec</legacyBold> is called when an asynchronous function is executing, it will return the current list of diagnostic records. Each time the original function call is repeated, it clears previous diagnostic records.</para>
    </content>
  </section>
  <section>
    <title>Executing Connection Operations Asynchronously</title>
    <content>
      <para>Before ODBC 3.8, asynchronous execution was allowed for statement-related operations such as prepare, execute, and fetch, as well as for catalog metadata operations. Starting in ODBC 3.8, asynchronous execution is also possible for connection-related operations such as connect, disconnect, commit, and rollback.</para>
      <para>For more information on ODBC 3.8, see <link xlink:href="854f0bb4-17e9-489b-9595-eefffb8ba99f">What's New in ODBC 3.8</link>.</para>
      <para>Executing connection operations asynchronously is useful in the following scenarios:</para>
      <list class="bullet">
        <listItem>
          <para>When a small number of threads manages a large number of devices with very high data rates. To maximize responsiveness and scalability it is desirable for all operations to be asynchronous.</para>
        </listItem>
        <listItem>
          <para>When you want to overlap database operations over multiple connections to reduce elapsed transfer times.</para>
        </listItem>
        <listItem>
          <para>Efficient asynchronous ODBC calls and the ability to cancel connection operations enable an application to allow the user to cancel any slow operation without having to wait for timeouts.</para>
        </listItem>
      </list>
      <para>The following functions, which operate on connection handles, can now be executed asynchronously:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="b7f1be66-e6c7-4790-88ec-62b7662103c0">SQLBrowseConnect</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9e84a58e-db48-4821-a0cd-5c711fcbe36b">SQLDisconnect</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>To determine whether a driver supports asynchronous operations on these functions, an application calls <unmanagedCodeEntityReference>SQLGetInfo</unmanagedCodeEntityReference> with SQL_ASYNC_DBC_FUNCTIONS. SQL_ASYNC_DBC_CAPABLE is returned if asynchronous operations are supported. SQL_ASYNC_DBC_NOT_CAPABLE is returned if asynchronous operations are not supported.</para>
      <para>To specify that functions executed with a particular connection are to be executed asynchronously, the application calls <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference> and sets the SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE attribute to SQL_ASYNC_DBC_ENABLE_ON. Setting a connection attribute before establishing a connection always executes synchronously. Also, the operation setting the connection attribute SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE with <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference> always executes synchronously.</para>
      <para>An application can enable asynchronous operation before making a connection. Because the Driver Manager cannot determine which driver to use before making a connection, the Driver Manager will always return success in <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference>. However, it may fail to connect if the ODBC driver does not support asynchronous operations.</para>
      <para>In general, there can be at most one asynchronously executing function associated with a particular connection handle or statement handle. However, a connection handle can have more than one associated statement handle. If there is no asynchronous operation executing on the connection handle, an associated statement handle can execute an asynchronous operation. Similarly, you can have an asynchronous operation on a connection handle if there are no asynchronous operations in progress on any associated statement handle. An attempt to execute an asynchronous operation using a handle that is currently executing an asynchronous operation will return HY010, "Function sequence error".</para>
      <para>If a connection operation returns SQL_STILL_EXECUTING, an application can only call the original function and the following functions for that connection handle:</para>
      <list class="bullet">
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> (on the connection handle)</para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetDiagField</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetDiagRec</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLAllocHandle</unmanagedCodeEntityReference> (allocating ENV/DBC)</para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLAllocHandleStd</unmanagedCodeEntityReference> (allocating ENV/DBC)</para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetEnvAttr</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetConnectAttr</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLDataSources</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLDrivers</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetInfo</unmanagedCodeEntityReference>
          </para>
        </listItem>
        <listItem>
          <para>
            <unmanagedCodeEntityReference>SQLGetFunctions</unmanagedCodeEntityReference>
          </para>
        </listItem>
      </list>
      <para>The application should process diagnostic records in the repeating loop of the original function. If SQLGetDiagField or SQLGetDiagRec is called when an asynchronous function is executing, it will return the current list of diagnostic records. Each time the original function call is repeated, it clears previous diagnostic records.</para>
      <para>If a connection is being opened or closed asynchronously, the operation is complete when the application receives SQL_SUCCESS or SQL_SUCCESS_WITH_INFO in the original function call.</para>
      <para>A new function has been added to ODBC 3.8, <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference>. This function cancels the six connection functions (<unmanagedCodeEntityReference>SQLBrowseConnect</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLConnect</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLEndTran</unmanagedCodeEntityReference>, and <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference>). An application should call <unmanagedCodeEntityReference>SQLGetFunctions</unmanagedCodeEntityReference> to determine if the driver supports <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference>. As with <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference>, if <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> returns success, it does not mean the operation was canceled. An application should call the original function again to determine if the operation was canceled.<unmanagedCodeEntityReference> SQLCancelHandle</unmanagedCodeEntityReference> lets you cancel asynchronous operations on connection handles or statement handles. Using <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> to cancel an operation on a statement handle is the same as calling <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference>.</para>
      <para>It is not necessary to support both <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> and asynchronous connection operations at the same time. A driver can support asynchronous connection operations but not <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference>, or vice versa.</para>
      <para>Asynchronous connection operations and <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> can also be used by ODBC 3.x and ODBC 2.x applications with an ODBC 3.8 driver and ODBC 3.8 Driver Manager. For information about for how to enable an older application to use new features in later ODBC version, see <link xlink:href="0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6">Compatibility Matrix</link>.</para>
    </content>
    <sections>
      <section>
        <title>Connection Pooling</title>
        <content>
          <para>Whenever connection pooling is enabled, asynchronous operations are only minimally supported for establishing a connection (with <unmanagedCodeEntityReference>SQLConnect</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference>) and closing a connection with <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference>. But an application should still be able to handle the SQL_STILL_EXECUTING return value from <unmanagedCodeEntityReference>SQLConnect</unmanagedCodeEntityReference>,<unmanagedCodeEntityReference> SQLDriverConnect</unmanagedCodeEntityReference>, and <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference>.</para>
          <para>When connection pooling is enabled, <unmanagedCodeEntityReference>SQLEndTran</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference> are supported for asynchronous operations.</para>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Example</title>
    <content />
    <sections>
      <section>
        <title>Description</title>
        <content>
          <para>The following example shows how to use <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference> to enable asynchronous execution for connection-related functions.</para>
        </content>
      </section>
      <section>
        <title>Code</title>
        <content>
          <code>BOOL AsyncConnect (SQLHANDLE hdbc) 
{
   SQLRETURN r;
   SQLHANDLE hdbc;

   // Enable asynchronous execution of connection functions.
   // This must be executed synchronously, that is r != SQL_STILL_EXECUTING
   r = SQLSetConnectAttr(
         hdbc, 
         SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE,
         reinterpret_cast&lt;SQLPOINTER&gt; (SQL_ASYNC_DBC_ENABLE_ON),
         0);
   if (r != SQL_SUCCESS &amp;&amp; r != SQL_SUCCESS_WITH_INFO) 
   {
      return FALSE;
   }

   TCHAR szConnStrIn[256] = _T("DSN=AsyncDemo");

   r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);

   if (r == SQL_ERROR) 
   {
      // Use SQLGetDiagRec to process the error.
      // If SQLState is HY114, the driver does not support asynchronous execution.
      return FALSE;
   }

   while (r == SQL_STILL_EXECUTING) 
   {
      // Do something else.

      // Check for completion, with the same set of arguments.
      r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);
   }
   
   if (r != SQL_SUCCESS &amp;&amp; r != SQL_SUCCESS_WITH_INFO) 
   {
      return FALSE;
   }

   return TRUE;
}
</code>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Example</title>
    <content />
    <sections>
      <section>
        <title>Description</title>
        <content>
          <para>This example shows asynchronous commit operations. Rollback operations can also be done this way. </para>
        </content>
      </section>
      <section>
        <title>Code</title>
        <content>
          <code>BOOL AsyncCommit () 
{
   SQLRETURN r; 

   // Assume that SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE is SQL_ASYNC_DBC_ENABLE_ON.

   r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);
   while (r == SQL_STILL_EXECUTING) 
   {
      // Do something else.

      // Check for completion with the same set of arguments.
      r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);
   }
   
   if (r != SQL_SUCCESS &amp;&amp; r != SQL_SUCCESS_WITH_INFO) 
   {
      return FALSE;
   }
   return TRUE;
}</code>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="09063f43-f5f0-4cf0-baa9-12fec8898997">Executing Statements ODBC</link>
</relatedTopics>
</developerConceptualDocument>