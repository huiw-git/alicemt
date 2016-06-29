---
title: Using SQLConfigDatasource with the ODBC Driver for Oracle
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e535d1ef-aff9-4ae7-a3ed-ef4ca2584289
translation.priority.ht: 
  - en-gb
---
# Using SQLConfigDatasource with the ODBC Driver for Oracle
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The following table lists valid <legacyBold>SQLConfigDatasource</legacyBold> settings for the Microsoft ODBC Driver for Oracle, version 1.0 (Msorcl10.dll) and the Microsoft ODBC Driver for Oracle, version 2.0 (Msorcl32.dll).</para>
    <alert class="note">
      <para>The Msorcl10.dll driver (version 1.0) supports all settings except <legacyBold>Server</legacyBold>. The Msorcl32.dll driver (version 2.0 and higher) supports all settings.</para>
    </alert>
    <para>Some settings are ignored by the driver but are accepted by <legacyBold>SQLConfigDatasource</legacyBold>. Including these settings in the ODBC connection string is the only way they will be accepted at run time. An ignored setting will not be stored in the registry when <legacyBold>SQLConfigDatasource</legacyBold> creates the data source.</para>
    <para>In the following table, <legacyItalic>A/N</legacyItalic> means any valid alphanumeric string up to the maximum allowable length. <legacyItalic>Max Len</legacyItalic> (maximum length) is the maximum allowable string length accepted by the setting, including the string-terminator character.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Setting</para>
          </TD>
          <TD>
            <para>Max Len</para>
          </TD>
          <TD>
            <para>Default value</para>
          </TD>
          <TD>
            <para>Valid values</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>BufferSize</para>
          </TD>
          <TD>
            <para>7 </para>
          </TD>
          <TD>
            <para>65535</para>
          </TD>
          <TD>
            <para>1000</para>
          </TD>
          <TD>
            <para>Minimum fetch buffer size up to 65535 bytes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CatalogCap</para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>0 or 1</para>
          </TD>
          <TD>
            <para>If 1, nonquoted identifiers will be converted to uppercase in the catalog functions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ConnectString</para>
          </TD>
          <TD>
            <para>128</para>
          </TD>
          <TD>
            <para>"" </para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Connection string. Required method of specifying the server name with the Msorcl10.dll driver.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Description</para>
          </TD>
          <TD>
            <para>256</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Description.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DSN</para>
          </TD>
          <TD>
            <para>33</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Data source name.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>GuessTheColDef</para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Returns a non-zero value for columns without Oracle-defined scale. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NumberFloat</para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>0 or 1</para>
          </TD>
          <TD>
            <para>If 0, FLOAT columns are treated as SQL_FLOAT. If 1, FLOAT columns are treated as SQL_DOUBLE.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PWD</para>
          </TD>
          <TD>
            <para>30</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Password.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>RDOSupport</para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>0 or 1</para>
          </TD>
          <TD>
            <para>Allows RDO to call Oracle procedures.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Remarks</para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>0 or 1</para>
          </TD>
          <TD>
            <para>Include REMARKS in catalog functions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>RowLimit</para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>0 to 99</para>
          </TD>
          <TD>
            <para>Maximum number of rows returned by a SELECT statement. A zero-length string indicates that no limit is applied.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Server</para>
          </TD>
          <TD>
            <para>128</para>
          </TD>
          <TD>
            <para>"" </para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Oracle server name.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SynonymColumns</para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>0 or 1</para>
          </TD>
          <TD>
            <para>Include SYNONYMs in SQLColumns.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SystemTable</para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>0 or 1</para>
          </TD>
          <TD>
            <para>If 0, system tables will not be displayed. If 1, system tables will be displayed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TranslationDLL</para>
          </TD>
          <TD>
            <para>33</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Translation .dll name.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TranslationName</para>
          </TD>
          <TD>
            <para>33</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Translation name.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TranslationOption</para>
          </TD>
          <TD>
            <para>33</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Translation option.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TxnCap</para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>"" </para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>Transaction capable. If 0, the driver reports that it does not support transactions. If 1, the driver reports that it is capable of performing transactions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>UID</para>
          </TD>
          <TD>
            <para>30</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
          <TD>
            <para>A/N</para>
          </TD>
          <TD>
            <para>User name.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>