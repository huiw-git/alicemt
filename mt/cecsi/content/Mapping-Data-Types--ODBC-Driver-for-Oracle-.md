---
title: "Mapping Data Types (ODBC Driver for Oracle)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Mapping Data Types (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The Oracle Server supports a set of data types. The ODBC Driver for Oracle maps these data types to their appropriate ODBC SQL data types. The following table lists the Oracle 7.3 Server data types and their corresponding ODBC SQL data types.</para>
    <para>The ODBC Driver for Oracle supports Oracle 7.3 and some Oracle8 data types. For more information about supported Oracle8 data types, see <legacyLink xlink:href="21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870">Supported Data Types</legacyLink>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Oracle Server data type</para>
          </TD>
          <TD>
            <para>ODBC SQL data type</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>CHAR</para>
          </TD>
          <TD>
            <para>SQL_CHAR</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DATE</para>
          </TD>
          <TD>
            <para>SQL_TIMESTAMP</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FLOAT</para>
          </TD>
          <TD>
            <para>SQL_DOUBLE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>INTEGER</para>
          </TD>
          <TD>
            <para>SQL_DECIMAL</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>LONG</para>
          </TD>
          <TD>
            <para>SQL_LONGVARCHAR</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>LONG RAW</para>
          </TD>
          <TD>
            <para>SQL_LONGVARBINARY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMBER</para>
          </TD>
          <TD>
            <para>SQL_DECIMAL</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>RAW</para>
          </TD>
          <TD>
            <para>SQL_VARBINARY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>VARCHAR2</para>
          </TD>
          <TD>
            <para>SQL_VARCHAR</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <alert class="note">
      <para>For more information about the allowable size of the VARCHAR column, see <legacyLink xlink:href="eb4cb410-3d00-4251-8c5e-a06f36c4dac7">VARCHAR Column Size</legacyLink> in this guide.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>