---
title: SQLSetConnectOption (Access Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58399bc4-d0b1-4eaa-a474-c92b2d5855ea
translation.priority.ht: 
  - en-gb
---
# SQLSetConnectOption (Access Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Access Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
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
            <para>When the Microsoft Access driver is used, the SQL_AUTOCOMMIT option may be set to either SQL_AUTOCOMMIT_ON or SQL_AUTOCOMMIT_OFF, because the Microsoft Access driver supports transactions[1].</para>
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
            <para>SQL_TXN_ISOLATION is always SQL_TXN_READ_COMMITTED. </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   Atomic transactions are not supported by the Microsoft Access driver. When committing a transaction using the Microsoft Access driver, a finite delay exists between the time the transaction is committed and the time the values are written to disk. This delay is determined by a delay inherent in the Microsoft Jet engine. The page timeout will not be less than a minimum value, even if the PageTimeout option is set below that value. As a result, there is no guarantee that committed data is stable, since changes may be made during the delay.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>