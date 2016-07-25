---
title: "Core Interface Conformance"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaaa864a-6477-45ff-a50a-96d8db66a252
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Core Interface Conformance
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>All ODBC drivers must exhibit at least Core-level interface conformance. Because the features in the Core level are those required by most generic interoperable applications, the driver can work with such applications. The features in the Core level also correspond to the features defined in the ISO CLI specification and to the nonoptional features defined in the Open Group CLI specification. A Core-level interface–conformant ODBC driver allows the application to do all of the following:  </para>
    <list class="bullet">
      <listItem>
        <para>Allocate and free all types of handles, by calling <legacyBold>SQLAllocHandle</legacyBold> and <legacyBold>SQLFreeHandle</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Use all forms of the <legacyBold>SQLFreeStmt</legacyBold> function.</para>
      </listItem>
      <listItem>
        <para>Bind result set columns, by calling <legacyBold>SQLBindCol</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Handle dynamic parameters, including arrays of parameters, in the input direction only, by calling <legacyBold>SQLBindParameter</legacyBold> and <legacyBold>SQLNumParams</legacyBold>. (Parameters in the output direction are feature 203 in <legacyLink xlink:href="2dc87840-f2fe-43dd-9d7b-bd95523081d9">Level 2 Interface Conformance</legacyLink>.)</para>
      </listItem>
      <listItem>
        <para>Specify a bind offset.</para>
      </listItem>
      <listItem>
        <para>Use the data-at-execution dialog, involving calls to <legacyBold>SQLParamData</legacyBold> and <legacyBold>SQLPutData</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Manage cursors and cursor names, by calling <legacyBold>SQLCloseCursor</legacyBold>, <legacyBold>SQLGetCursorName</legacyBold>, and <legacyBold>SQLSetCursorName</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Gain access to the description (metadata) of result sets, by calling <legacyBold>SQLColAttribute</legacyBold>, <legacyBold>SQLDescribeCol</legacyBold>, <legacyBold>SQLNumResultCols</legacyBold>, and <legacyBold>SQLRowCount</legacyBold>. (Use of these functions on column number 0 to retrieve bookmark metadata is feature 204 in <legacyLink xlink:href="2dc87840-f2fe-43dd-9d7b-bd95523081d9">Level 2 Interface Conformance</legacyLink>.)</para>
      </listItem>
      <listItem>
        <para>Query the data dictionary, by calling the catalog functions <legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLGetTypeInfo</legacyBold>, <legacyBold>SQLStatistics</legacyBold>, and <legacyBold>SQLTables</legacyBold>. </para>
        <para>The driver is not required to support multipart names of database tables and views. (For more information, see feature 101 in <legacyLink xlink:href="ee3f5c08-0583-4f3b-8354-ef71b6086a7e">Level 1 Interface Conformance</legacyLink> and feature 201 in <legacyLink xlink:href="2dc87840-f2fe-43dd-9d7b-bd95523081d9">Level 2 Interface Conformance</legacyLink>.) However, certain features of the SQL-92 specification, such as column qualification and names of indexes, are syntactically comparable to multipart naming. The present list of ODBC features is not intended to introduce new options into these aspects of SQL-92. </para>
      </listItem>
      <listItem>
        <para>Manage data sources and connections, by calling <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLDataSources</legacyBold>, <legacyBold>SQLDisconnect</legacyBold>, and <legacyBold>SQLDriverConnect</legacyBold>. Obtain information on drivers, no matter which ODBC level they support, by calling <legacyBold>SQLDrivers</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Prepare and execute SQL statements, by calling <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, and <legacyBold>SQLPrepare</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Fetch one row of a result set or multiple rows, in the forward direction only, by calling <legacyBold>SQLFetch</legacyBold> or by calling <legacyBold>SQLFetchScroll</legacyBold> with the <legacyItalic>FetchOrientation</legacyItalic> argument set to SQL_FETCH_NEXT.</para>
      </listItem>
      <listItem>
        <para>Obtain an unbound column in parts, by calling <legacyBold>SQLGetData</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Obtain current values of all attributes, by calling <legacyBold>SQLGetConnectAttr</legacyBold>, <legacyBold>SQLGetEnvAttr</legacyBold>, and <legacyBold>SQLGetStmtAttr</legacyBold>, and set all attributes to their default values and set certain attributes to nondefault values by calling <legacyBold>SQLSetConnectAttr</legacyBold>, <legacyBold>SQLSetEnvAttr</legacyBold>, and <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Manipulate certain fields of descriptors, by calling <legacyBold>SQLCopyDesc</legacyBold>, <legacyBold>SQLGetDescField</legacyBold>, <legacyBold>SQLGetDescRec</legacyBold>, <legacyBold>SQLSetDescField</legacyBold>, and <legacyBold>SQLSetDescRec</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Obtain diagnostic information, by calling <legacyBold>SQLGetDiagField</legacyBold> and <legacyBold>SQLGetDiagRec</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Detect driver capabilities, by calling <legacyBold>SQLGetFunctions</legacyBold> and <legacyBold>SQLGetInfo</legacyBold>. Also, detect the result of any text substitutions made to an SQL statement before it is sent to the data source, by calling <legacyBold>SQLNativeSql</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Use the syntax of <legacyBold>SQLEndTran</legacyBold> to commit a transaction. A Core-level driver need not support true transactions; therefore, the application cannot specify SQL_ROLLBACK nor SQL_AUTOCOMMIT_OFF for the SQL_ATTR_AUTOCOMMIT connection attribute. (For more information, see feature 109 in <legacyLink xlink:href="2dc87840-f2fe-43dd-9d7b-bd95523081d9">Level 2 Interface Conformance</legacyLink>.)</para>
      </listItem>
      <listItem>
        <para>Call <legacyBold>SQLCancel</legacyBold> to cancel the data-at-execution dialog and, in multithread environments, to cancel an ODBC function executing in another thread. Core-level interface conformance does not mandate support for asynchronous execution of functions, nor the use of <legacyBold>SQLCancel</legacyBold> to cancel an ODBC function executing asynchronously. Neither the platform nor the ODBC driver need be multithread for the driver to conduct independent activities at the same time. However, in multithread environments, the ODBC driver must be thread-safe. Serialization of requests from the application is a conformant way to implement this specification, even though it might create serious performance problems.</para>
      </listItem>
      <listItem>
        <para>Obtain the SQL_BEST_ROWID row-identifying column of tables, by calling <legacyBold>SQLSpecialColumns</legacyBold>. (Support for SQL_ROWVER is feature 208 in <legacyLink xlink:href="2dc87840-f2fe-43dd-9d7b-bd95523081d9">Level 2 Interface Conformance</legacyLink>.) </para>
        <alert class="important">
          <para>ODBC Drivers must implement the functions in the Core interface conformance level.</para>
        </alert>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>