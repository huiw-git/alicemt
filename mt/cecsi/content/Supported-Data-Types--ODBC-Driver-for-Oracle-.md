---
title: "Supported Data Types (ODBC Driver for Oracle)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Supported Data Types (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The ODBC Driver for Oracle supports all Oracle 7.3 data types; however, it does not support any of the new Oracle8 data types listed here.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Data type</para>
          </TD>
          <TD>
            <para>Oracle 7.3</para>
          </TD>
          <TD>
            <para>Oracle8</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>BFILE</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>BLOB</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CHAR</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CLOB</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DATE</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FLOAT</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>INTEGER</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>LONG</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>LONG RAW</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NCHAR</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NCLOB</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMBER</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NVARCHAR2</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
          <TD>
            <para>Not supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>RAW</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>VARCHAR2</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
          <TD>
            <para>Supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MLSLABEL</para>
          </TD>
          <TD>
            <para>Not supported. </para>
          </TD>
          <TD>
            <para>Not supported.</para>
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