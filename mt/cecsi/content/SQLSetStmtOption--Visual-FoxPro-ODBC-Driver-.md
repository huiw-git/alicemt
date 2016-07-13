---
title: SQLSetStmtOption (Visual FoxPro ODBC Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetStmtOption (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Level 1</para>
    <para>Sets options related to a statement handle, <legacyItalic>hstmt</legacyItalic>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>                 <legacyItalic>fOption</legacyItalic>               </para>
          </TD>
          <TD>
            <para>Allowed values</para>
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
            <para>SQL_ASYNC_ENABLE_OFF</para>
          </TD>
          <TD>
            <para>If you attempt to set this <legacyItalic>fOption</legacyItalic>, the driver returns the error: "Driver not capable". Visual FoxPro does not support asynchronous execution.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIND_TYPE</para>
          </TD>
          <TD>
            <para>SQL_BIND_BY_COLUMN or a 32-bit value denoting the length of the structure or an instance of a buffer into which result columns will be bound.</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CONCURRENCY</para>
          </TD>
          <TD>
            <para>SQL_CONCUR_READ_ONLY </para>
            <para>SQL_CONCUR_LOCK </para>
            <para>SQL_CONCUR_VALUES</para>
          </TD>
          <TD>
            <para>The driver doesn't allow SQL_CONCUR_ROWVER, because Visual FoxPro does not have row versioning based on timestamps. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CURSOR_TYPE</para>
          </TD>
          <TD>
            <para>SQL_CURSOR_FORWARD_ONLY </para>
            <para>SQL_CURSOR_STATIC</para>
          </TD>
          <TD>
            <para>The driver does not allow SQL_CURSOR_KEYSET_DRIVEN or SQL_CURSOR_DYNAMIC; see <legacyLink xlink:href="693e6e28-a845-41b1-9622-5058b0d87229">SQLSetScrollOptions</legacyLink> for more information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_KEYSET_SIZE</para>
          </TD>
          <TD>
            <para>Error: "Driver not capable"</para>
          </TD>
          <TD>
            <para>Visual FoxPro does not support the keyset cursor model.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_LENGTH</para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>If you attempt to set this <legacyItalic>fOption</legacyItalic> value, the driver returns the error "Driver not capable".</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_ROWS</para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>If you attempt to set this <legacyItalic>fOption</legacyItalic> value, the driver returns the error "Driver not capable".</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_NOSCAN</para>
          </TD>
          <TD>
            <para>SQL_NOSCAN_OFF</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_QUERY_TIMEOUT</para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>If you attempt to set this <legacyItalic>fOption</legacyItalic> value, the driver returns the error "Driver not capable".</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_RETRIEVE_DATA</para>
          </TD>
          <TD>
            <para>SQL_RD_ON, SQL_RD_OFF</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROWSET_SIZE</para>
          </TD>
          <TD>
            <para>1 to 4,294,967,296</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_SIMULATE_CURSOR</para>
          </TD>
          <TD>
            <para>Error: "Driver not capable" </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_USE_BOOKMARKS</para>
          </TD>
          <TD>
            <para>SQL_UB_OFF </para>
            <para>SQL_UB_ON</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For more information, see <legacyLink xlink:href="9cbe2b62-4cf7-43ab-8fb4-9a53df2c6b3f">SQLSetStmtOption</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>