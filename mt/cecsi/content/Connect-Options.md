---
title: Connect Options
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
translation.priority.ht: 
  - en-gb
---
# Connect Options
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>These options allow customization of the database connection within an application.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Connect option</para>
          </TD>
          <TD>
            <para>Notes</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_AUTOCOMMIT</para>
          </TD>
          <TD>
            <para>If you choose SQL_AUTOCOMMIT_OFF, your application must explicitly commit or roll back transactions with <legacyLink xlink:href="8596eed7-bda6-4cac-ae1f-efde1aab785f">SQLTransact</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ODBC_CURSORS</para>
          </TD>
          <TD>
            <para>This connection attribute is implemented in the Driver Manager.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_OPT_TRACE</para>
          </TD>
          <TD>
            <para>This connection attribute is implemented in the Driver Manager.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_OPT_TRACEFILE</para>
          </TD>
          <TD>
            <para>This connection attribute is implemented in the Driver Manager.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TRANSLATE_DLL</para>
          </TD>
          <TD>
            <para>Returns error: "Driver not capable."</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TRANSLATE_OPTION</para>
          </TD>
          <TD>
            <para>A 32-bit value passed to the translation .dll.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TXN_ISOLATION</para>
          </TD>
          <TD>
            <para>The driver allows only SQL_TXN_READ_COMMITTED.</para>
            <para>The following vParams are not supported:</para>
            <para>   SQL_TXN_READ_UNCOMMITTED </para>
            <para>   SQL_TXN_REAPEATABLE_READ </para>
            <para>   SQL_TXN_SERIALIZABLE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ENLIST_IN_DTC</para>
          </TD>
          <TD>
            <para>This ODBC 3.0 connection attribute allows you to use the ODBC Driver for Oracle in distributed transactions coordinated by Microsoft Component Services (or MTS, if you are using Windows NT). It provides the interface pointer <legacyItalic>pITransaction</legacyItalic> to the transaction as the <legacyItalic>vParam</legacyItalic> argument.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CONNECTION_DEAD</para>
          </TD>
          <TD>
            <para>This read-only ODBC 3.5 connection attribute allows you to determine whether the connection to the Oracle server has failed. Get only; cannot Set.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>