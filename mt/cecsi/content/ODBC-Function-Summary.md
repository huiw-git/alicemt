---
title: "ODBC Function Summary"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
caps.latest.revision: 13
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Function Summary
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists ODBC functions, grouped by type of task, and includes the conformance designation and a brief description of the purpose of each function. For more information about conformance designations, see <legacyLink xlink:href="79b9c268-16ac-4b80-b451-f9dcd8c02ca4">ODBC and the Standard CLI</legacyLink>. For more information about the syntax and semantics for each function, see <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    <para>An application can call the <legacyBold>SQLGetInfo</legacyBold> function to obtain conformance information about a driver. To obtain information about support for a specific function in a driver, an application can call <legacyBold>SQLGetFunctions</legacyBold>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Task</para>
          </TD>
          <TD>
            <para>Function name</para>
          </TD>
          <TD>
            <para>Conformance</para>
          </TD>
          <TD>
            <para>Purpose</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Connecting to a data source</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Obtains an environment, connection, statement, or descriptor handle.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Connects to a specific driver by data source name, user ID, and password. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Connects to a specific driver by connection string or requests that the Driver Manager and driver display connection dialog boxes for the user.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="b7f1be66-e6c7-4790-88ec-62b7662103c0">SQLBrowseConnect</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Returns successive levels of connection attributes and valid attribute values. When a value has been specified for each connection attribute, connects to the data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Obtaining information about a driver and data source</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="3f63b1b4-e70e-44cd-96c6-6878d50d0117">SQLDataSources</legacyLink>
            </para>
            <para>
              <legacyLink xlink:href="6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa">SQLDrivers</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Returns the list of available data sources.</para>
            <para>Returns the list of installed drivers and their attributes.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns information about a specific driver and data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="0451d2f9-0f4f-46ba-b252-670956a52183">SQLGetFunctions</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns supported driver functions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="bdedb044-8924-4ca4-85f3-8b37578e0257">SQLGetTypeInfo</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns information about supported data types.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Setting and retrieving driver attributes</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>
            </para>
            <para>
              <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
            <para> ISO 92</para>
          </TD>
          <TD>
            <para>Sets a connection attribute.</para>
            <para>Returns the value of a connection attribute.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Sets an environment attribute.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="01f4590f-427a-4280-a1c3-18de9f7d86c1">SQLGetEnvAttr</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns the value of an environment attribute.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Sets a statement attribute.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns the value of a statement attribute.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Setting and retrieving descriptor fields</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="f09ff660-1e4a-4370-be85-90d4da0487d3">SQLGetDescField</legacyLink>
            </para>
            <para>
              <legacyLink xlink:href="325e0907-8e87-44e8-a111-f39e636a9cbc">SQLGetDescRec</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns the value of a single descriptor field.</para>
            <para>Returns the values of multiple descriptor fields.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>  </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Sets a single descriptor field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>  </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="bf55256c-7eb7-4e3f-97ef-b0fee09ba829">SQLSetDescRec</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Sets multiple descriptor fields.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="d5450895-3824-44c4-8aa4-d4f9752a9602">SQLCopyDesc</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Copies descriptor information from one descriptor handle to another.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Preparing SQL requests</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Prepares an SQL statement for later execution.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Assigns storage for a parameter in an SQL statement.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="e6e92199-7bb6-447c-8987-049a4c6ce05d">SQLGetCursorName</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns the cursor name associated with a statement handle.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="4e055946-12d4-4589-9891-41617a50f34e">SQLSetCursorName</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Specifies a cursor name.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="2a825ba7-7942-4c23-bcdb-c80dc12f8c86">SQLSetScrollOptions</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Sets options that control cursor behavior.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Submitting requests</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute</legacyLink>
            </para>
            <para>
              <legacyLink xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Executes a prepared statement.</para>
            <para>Executes a statement.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="b8efc247-27ab-4a00-92b6-1400785783fe">SQLNativeSql</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Returns the text of an SQL statement as translated by the driver.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="1f5b63c4-2f3e-44da-b155-876405302281">SQLDescribeParam</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Returns the description for a specific parameter in a statement.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="dbf2da44-253b-4094-bd6b-29bafc23c7a3">SQLNumParams</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns the number of parameters in a statement.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="68fe010d-9539-4e5b-a260-c8d32423b1db">SQLParamData</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Used in conjunction with <legacyBold>SQLPutData</legacyBold> to supply parameter data at execution time. (Useful for long data values.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Sends part or all of a data value for a parameter. (Useful for long data values.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Retrieving results and information about results</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="61e00a8a-9b3b-45b9-b397-7fe818822416">SQLRowCount</legacyLink>
            </para>
            <para>
              <legacyLink xlink:href="d863179f-12a9-4b55-ac6b-7d84202d3da3">SQLNumResultCols</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
            <para> ISO 92</para>
          </TD>
          <TD>
            <para>Returns the number of rows affected by an insert, update, or delete request.</para>
            <para>Returns the number of columns in the result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="eddef353-83f3-4a3c-8f24-f9ed888890a4">SQLDescribeCol</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Describes a column in the result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="8c45c598-cb01-4789-a571-e93619a18ed9">SQLColAttribute</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Describes attributes of a column in the result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Assigns storage for a result column and specifies the data type.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns multiple result rows.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns scrollable result rows.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns part or all of one column of one row of a result set. (Useful for long data values.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Positions a cursor within a fetched block of data and allows an application to refresh data in the rowset or to update or delete data in the result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Performs bulk insertions and bulk bookmark operations, including update, delete, and fetch by bookmark.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="bf169ed5-4d55-412c-b184-12065a726e89">SQLMoreResults</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Determines whether there are more result sets available and, if so, initializes processing for the next result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns additional diagnostic information (a single field of the diagnostic data structure).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="ebdbac93-3d68-438f-8416-ef1f08e04269">SQLGetDiagRec</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns additional diagnostic information (multiple fields of the diagnostic data structure).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Obtaining information about the data source's system tables (catalog functions)</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="ef233d9a-6ed5-4986-9d42-5e0b1a79fb6e">SQLColumnPrivileges</legacyLink>
            </para>
            <para>
              <legacyLink xlink:href="4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0">SQLColumns</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
            <para> Open Group</para>
          </TD>
          <TD>
            <para>Returns a list of columns and associated privileges for one or more tables.</para>
            <para>Returns the list of column names in specified tables.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="07f3f645-f643-4d39-9a10-70a72f24e608">SQLForeignKeys</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Returns a list of column names that make up foreign keys, if they exist for a specified table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="3f809b09-3c1b-415e-80c5-a603e8e25d5b">SQLPrimaryKeys</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Returns the list of column names that make up the primary key for a table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="4ca37b28-a6df-465b-8988-d422d37fc025">SQLProcedureColumns</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Returns the list of input and output parameters, as well as the columns that make up the result set for the specified procedures.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="d0d9ef10-2fd4-44a5-9334-649f186f4ba0">SQLProcedures</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Returns the list of procedure names stored in a specific data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="bb2d9f21-bda0-4e50-a8be-f710db660034">SQLSpecialColumns</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Open Group</para>
          </TD>
          <TD>
            <para>Returns information about the optimal set of columns that uniquely identifies a row in a specified table, or the columns that are automatically updated when any value in the row is updated by a transaction.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="45210682-cfea-4e5d-9951-bcf1cbe10f41">SQLStatistics</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Returns statistics about a single table and the list of indexes associated with the table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="8cfdb64f-64c5-47e6-ad57-0533ac630afa">SQLTablePrivileges</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Returns a list of tables and the privileges associated with each table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="60d5068a-7d7c-447c-acc6-f3f2cf73440c">SQLTables</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Open Group</para>
          </TD>
          <TD>
            <para>Returns the list of table names stored in a specific data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Terminating a statement</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Ends statement processing, discards pending results, and, optionally, frees all resources associated with the statement handle.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="05b0a054-e28d-4e16-b5b0-07418486b372">SQLCloseCursor</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Closes a cursor that has been opened on a statement handle.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Cancels the processing on a statement.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para />
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ODBC</para>
          </TD>
          <TD>
            <para>Cancels the processing on a statement or connection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Commits or rolls back a transaction.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Terminating a connection</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="9e84a58e-db48-4821-a0cd-5c711fcbe36b">SQLDisconnect</legacyLink>
            </para>
            <para>
              <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle</legacyLink>
            </para>
          </TD>
          <TD>
            <para>ISO 92</para>
            <para>ISO 92</para>
          </TD>
          <TD>
            <para>Closes the connection.</para>
            <para>Releases an environment, connection, statement, or descriptor handle. </para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>