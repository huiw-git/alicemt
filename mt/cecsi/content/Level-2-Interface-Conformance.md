---
title: Level 2 Interface Conformance
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2dc87840-f2fe-43dd-9d7b-bd95523081d9
translation.priority.ht: 
  - en-gb
---
# Level 2 Interface Conformance
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Level 2 interface conformance level includes the Level 1 interface conformance–level functionality plus the following features:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>201</para>
          </TD>
          <TD>
            <para>Use three-part names of database tables and views. (For more information, see the two-part naming support feature 101 in <legacyLink xlink:href="ee3f5c08-0583-4f3b-8354-ef71b6086a7e">Level 1 Interface Conformance</legacyLink>.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>202</para>
          </TD>
          <TD>
            <para>Describe dynamic parameters, by calling <legacyBold>SQLDescribeParam</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>203</para>
          </TD>
          <TD>
            <para>Use not only input parameters but also output and input/output parameters, and result values of stored procedures.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>204</para>
          </TD>
          <TD>
            <para>Use bookmarks, including retrieving bookmarks, by calling <legacyBold>SQLDescribeCol</legacyBold> and <legacyBold>SQLColAttribute</legacyBold> on column number 0; fetching based on a bookmark, by calling <legacyBold>SQLFetchScroll</legacyBold> with the <legacyItalic>FetchOrientation</legacyItalic> argument set to SQL_FETCH_BOOKMARK; and update, delete, and fetch by bookmark operations, by calling <legacyBold>SQLBulkOperations</legacyBold> with the <legacyItalic>Operation</legacyItalic> argument set to SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK, or SQL_FETCH_BY_BOOKMARK.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>205</para>
          </TD>
          <TD>
            <para>Retrieve advanced information about the data dictionary, by calling <legacyBold>SQLColumnPrivileges</legacyBold>, <legacyBold>SQLForeignKeys</legacyBold>, and <legacyBold>SQLTablePrivileges</legacyBold>. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>206</para>
          </TD>
          <TD>
            <para>Use ODBC functions instead of SQL statements to perform additional database operations, by calling <legacyBold>SQLBulkOperations</legacyBold> with SQL_ADD, or <legacyBold>SQLSetPos</legacyBold> with SQL_DELETE or SQL_UPDATE. (Support for calls to <legacyBold>SQLSetPos</legacyBold> with the <legacyItalic>LockType</legacyItalic> argument set to SQL_LOCK_EXCLUSIVE or SQL_LOCK_UNLOCK is not a part of the conformance levels but is an optional feature.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>207</para>
          </TD>
          <TD>
            <para>Enable asynchronous execution of ODBC functions for specified individual statements.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>208</para>
          </TD>
          <TD>
            <para>Obtain the SQL_ROWVER row-identifying column of tables, by calling <legacyBold>SQLSpecialColumns</legacyBold>. (For more information, see the support for <legacyBold>SQLSpecialColumns</legacyBold> with the <legacyItalic>IdentifierType</legacyItalic> argument set to SQL_BEST_ROWID as feature 20 in <legacyLink xlink:href="aaaa864a-6477-45ff-a50a-96d8db66a252">Core Interface Conformance</legacyLink>.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>209</para>
          </TD>
          <TD>
            <para>Set the SQL_ATTR_CONCURRENCY statement attribute to at least one value other than SQL_CONCUR_READ_ONLY.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>210</para>
          </TD>
          <TD>
            <para>The ability to time out login request and SQL queries (SQL_ATTR_LOGIN_TIMEOUT and SQL_ATTR_QUERY_TIMEOUT).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>211</para>
          </TD>
          <TD>
            <para>The ability to change the default isolation level; the ability to execute transactions with the "serializable" level of isolation.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>