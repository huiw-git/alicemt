---
title: Functions Accepting String Parameters
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 869b8421-f71e-4dfd-adce-691bd3012b16
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Functions Accepting String Parameters
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>All functions that take string parameters will be converted to Unicode. (The "W" form of the function will be exported.) Count of bytes is converted to count of characters for those applicable ODBC APIs. This applies to the following functions:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>SQLConnect</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLDriverConnect</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLColAttributes</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLDescribeCol</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLError</legacyBold> (replaced by <legacyBold>SQLGetDiagField</legacyBold>)</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLExecDirect</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLGetCursorName</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLSetCursorName</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLGetStmtAttr</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLGetInfo</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLGetStmtOption</legacyBold> (becomes <legacyBold>SQLGetStmtAttr</legacyBold>)</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLSetStmtOption</legacyBold> (becomes <legacyBold>SQLSetStmtAttr</legacyBold>)</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLGetConnectOption</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLSetConnectOption</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLGetTypeInfo</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLStatistics</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLTables</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLNativeSQL</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLSpecialColumns</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>ConfigDSNEx</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>ConfigDSN</legacyBold>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>