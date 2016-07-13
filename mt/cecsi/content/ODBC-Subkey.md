---
title: ODBC Subkey
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9534144-8f42-4946-b0fb-638e9dcde9c8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Subkey
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The values under the ODBC subkey specify ODBC tracing options. These options are set through the Tracing tab of the ODBC Data Source Administrator dialog box displayed by <legacyBold>SQLManageDataSources</legacyBold>. The ODBC subkey itself is optional. The format of these values is as shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>Data type</para>
          </TD>
          <TD>
            <para>Data</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Trace</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyBold>0</legacyBold> | <legacyBold>1</legacyBold></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TraceFile</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>tracefile-path</legacyItalic>
            </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The values have the meanings described in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Value</para>
          </TD>
          <TD>
            <para>Meaning</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Trace</para>
          </TD>
          <TD>
            <para>If the Trace value is set to 1 when an application calls <legacyBold>SQLAllocHandle</legacyBold> with the SQL_HANDLE_ENV option, tracing is enabled for the calling application.</para>
            <para>If the Trace keyword is set to 0 when an application calls <legacyBold>SQLAllocHandle</legacyBold> with the SQL_HANDLE_ENV option, tracing is disabled for the calling application. This is the default value.</para>
            <para>An application can enable or disable tracing with the SQL_ATTR_TRACE connection attribute. However, doing so does not change the data for this value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TraceFile</para>
          </TD>
          <TD>
            <para>If tracing is enabled, the Driver Manager writes to the trace file specified by the TraceFile value.</para>
            <para>If no trace file is specified, the Driver Manager writes to the Sql.log file on the current drive. This is the default value.</para>
            <para>Tracing should be used only for a single application, or each application should specify a different trace file. Otherwise, two or more applications will attempt to open the same trace file at the same time, causing an error.</para>
            <para>An application can specify a new trace file with the SQL_ATTR_TRACEFILE connection attribute. However, doing so does not change the data for this value.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For example, suppose that tracing is enabled and the trace file is C:\Odbc.log. The values under the ODBC subkey would be as follows:</para>
    <code>Trace : REG_SZ : 1
TraceFile : REG_SZ : C:\ODBC.LOG
</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>