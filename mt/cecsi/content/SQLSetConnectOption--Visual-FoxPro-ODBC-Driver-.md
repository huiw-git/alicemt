---
title: SQLSetConnectOption (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a35449e-4694-4ee5-9fa1-45d5a8fe7823
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetConnectOption (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Partial </para>
    <para>ODBC API Conformance: Level 1</para>
    <para>Sets options that govern aspects of connections. This function is partially supported: The driver supports all values for the <legacyItalic>fOption</legacyItalic> argument but does not support some of <legacyItalic>vParam</legacyItalic> values for the <legacyItalic>fOption</legacyItalic> argument SQL_TXN_ISOLATION.</para>
    <para>The following table describes only those arguments with behavior specific to the Visual FoxPro ODBC Driver implementation of <legacyBold>SQLSetConnectOption</legacyBold>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>                 <legacyItalic>fOption</legacyItalic>               </para>
          </TD>
          <TD>
            <para>Remarks</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_AUTOCOMMIT</para>
          </TD>
          <TD>
            <para>If you choose SQL_AUTOCOMMIT_OFF, your application must explicitly commit or roll back transactions with <legacyLink xlink:href="92cf86c0-f7a8-44d7-b59f-a1342677440b">SQLTransact</legacyLink>; the Visual FoxPro ODBC Driver does not automatically commit a transactable statement upon completion. The driver does begin a transaction if the statement is transactable.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CURRENT_QUALIFIER</para>
          </TD>
          <TD>
            <para>Can be a fully qualified <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">database</legacyLink> name or fully qualified path to a directory containing zero or more <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">free tables</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_LOGINTIMEOUT</para>
          </TD>
          <TD>
            <para>Returns "Driver not capable" error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CURSORS</para>
          </TD>
          <TD>
            <para>Returns "Driver not capable" error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_PACKET_SIZE</para>
          </TD>
          <TD>
            <para>Returns "Driver not capable" error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TXN_ISOLATION</para>
          </TD>
          <TD>
            <para>The driver allows only SQL_TXN_READ_COMMITTED.</para>
            <para>The following <legacyItalic>vParam</legacyItalic>s are not supported:</para>
            <para>   SQL_TXN_READ_UNCOMMITTED </para>
            <para>   SQL_TXN_REAPEATABLE_READ </para>
            <para>   SQL_TXN_SERIALIZABLE</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For more information, see <legacyLink xlink:href="8cd2c2a2-25c8-4aff-951c-b593bbfc90ad">SQLSetConnectOption</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>