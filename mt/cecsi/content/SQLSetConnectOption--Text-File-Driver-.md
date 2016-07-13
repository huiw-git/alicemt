---
title: SQLSetConnectOption (Text File Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b631a20c-2f60-4102-a61d-93b8780a4620
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetConnectOption (Text File Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Text File Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>fOption</para>
          </TD>
          <TD>
            <para>Comment</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_ACCESS_MODE</para>
          </TD>
          <TD>
            <para>The SQL_ACCESS_MODE fOption can be set to either SQL_MODE_READ_ONLY or SQL_MODE_READ_WRITE. However, the driver does not prevent updates if SQL_ACCESS_MODE is set to SQL_MODE_READ_ONLY.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_AUTOCOMMIT</para>
          </TD>
          <TD>
            <para>The Text driver only supports SQL_AUTOCOMMIT being set to ON (the default state), because they do not support transactions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CURRENT_QUALIFIER</para>
          </TD>
          <TD>
            <para>Supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_LOGIN_TIMEOUT</para>
          </TD>
          <TD>
            <para>Not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_OPT_TRACE</para>
          </TD>
          <TD>
            <para>Supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_OPT_TRACEFILE</para>
          </TD>
          <TD>
            <para>Supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_PACKET_SIZE</para>
          </TD>
          <TD>
            <para>Not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_QUIET_MODE</para>
          </TD>
          <TD>
            <para>Not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TRANSLATE_DLL</para>
          </TD>
          <TD>
            <para>Not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TRANSLATION_OPTION</para>
          </TD>
          <TD>
            <para>Not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TXN_ISOLATION</para>
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