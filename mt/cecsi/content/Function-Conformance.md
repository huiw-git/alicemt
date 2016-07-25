---
title: "Function Conformance"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb5d68cf-d238-481e-babc-2e9401b4700e
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Function Conformance
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table indicates the conformance level of each ODBC function, where this is well defined.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Function</para>
          </TD>
          <TD>
            <para>Conformance level</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyBold>SQLAllocHandle</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLBindCol</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLBindParameter</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLBrowseConnect</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLBulkOperations</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLCancel</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLCloseCursor</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLColAttribute</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLColumnPrivileges</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLConnect</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLCopyDesc</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLDataSources</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLDescribeCol</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLDescribeParam</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLDisconnect</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLDriverConnect</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLDrivers</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLEndTran</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLExecDirect</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLExecute</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLFetch</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLFetchScroll</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLForeignKeys</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLFreeHandle</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLFreeStmt</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetConnectAttr</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetCursorName</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetData</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetDescField</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetDescRec</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetDiagField</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetDiagRec</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetEnvAttr</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetFunctions</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetInfo</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetStmtAttr</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetTypeInfo</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLMoreResults</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLNativeSql</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLNumParams</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLNumResultCols</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLParamData</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLPrepare</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLPrimaryKeys</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLProcedureColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLProcedures</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLPutData</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLRowCount</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetConnectAttr</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetCursorName</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetDescField</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetDescRec</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetEnvAttr</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetPos</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 1[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetStmtAttr</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSpecialColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLStatistics</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLTablePrivileges</legacyBold>             </para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLTables</legacyBold>             </para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   Significant features of this function are available only at higher conformance levels.</para>
    <para>[2]   Setting certain attributes to nondefault values depends on the conformance level. For more information, see the next section, <legacyLink xlink:href="34fea100-10f9-46d5-bc50-3aa867b70f24">Attribute Conformance</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>