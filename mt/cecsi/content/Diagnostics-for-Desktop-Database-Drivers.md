---
title: Diagnostics for Desktop Database Drivers
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Diagnostics for Desktop Database Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>All errors and warnings not checked or partially checked by the Driver Manager are handled by the driver. The driver also maps native errors, or errors returned by the data source, to SQLSTATEs. Each function listed in the <legacyItalic>ODBC Programmer's Reference</legacyItalic> contains a "Diagnostics" section that specifies conditions and messages. </para>
    <para>Applications call <legacyBold>SQLGetDiagRec</legacyBold> to retrieve SQLSTATE, native error code, and diagnostic messages. Calling <legacyBold>SQLGetDiagField</legacyBold> and specifying the field retrieves individual diagnostic fields. The support level of the diagnostic identifiers is listed in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>DiagIdentifiers</para>
          </TD>
          <TD>
            <para>Support level</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_DIA_DYNAMIC_FUNCTION</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_CLASS_ORIGIN</para>
          </TD>
          <TD>
            <para>Supported. Always "ODBC 3.0" for versions 3.0 and later of this driver.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_COLUMN_NUMBER</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_CURSOR_ROW_COUNT</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_DYNAMIC_FUNCTION_CODE</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_MESSAGE_TEXT</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_NATIVE</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_NUMBER</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_RETURNCODE</para>
          </TD>
          <TD>
            <para>Supported but implemented by the Driver Manager</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_ROW_COUNT</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_ROW_NUMBER</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_SERVER_NAME</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_SQLSTATE</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DIAG_SUBCLASS_ORIGIN</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>