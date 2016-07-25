---
title: "SQLSetStmtOption (Desktop Database Drivers)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetStmtOption (Desktop Database Drivers)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>                 <legacyItalic>fOption</legacyItalic>               </para>
          </TD>
          <TD>
            <para>Comments</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_ASYNC_ENABLE</para>
          </TD>
          <TD>
            <para>Asynchronous processing is not supported. The SQL_ASYNC_ENABLE fOption will return SQLSTATE S1C00 (Driver not capable). </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_KEYSET_SIZE</para>
          </TD>
          <TD>
            <para>The only valid keyset size is 0, because mixed and dynamic cursors are not supported. If this value is set to any other number, it will be changed to 0 and the call will return SQL_SUCCESS_WITH_INFO and SQLSTATE 01S02 (Option value changed).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_ROWS</para>
          </TD>
          <TD>
            <para>The only valid rowset size is 0, because the Desktop Database Drivers do not support limiting the number of rows that are returned. If this value is set to any other number, it will be changed to 0 and the call will return SQL_SUCCESS_WITH_INFO and SQLSTATE 01S02 (Option value changed).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_QUERY_TIMEOUT</para>
          </TD>
          <TD>
            <para>Not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROW_NUMBER</para>
          </TD>
          <TD>
            <para>Not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_SIMULATE_CURSOR</para>
          </TD>
          <TD>
            <para>Not supported.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>