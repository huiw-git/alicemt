---
title: "SQLGetTypeInfo (Visual FoxPro ODBC Driver)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetTypeInfo (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Level 1</para>
    <para>Returns information about the data types supported by a data source. The driver returns the information in an SQL result set. The following table lists ODBC data types and the corresponding Visual FoxPro data type.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ODBC type</para>
          </TD>
          <TD>
            <para>Visual FoxPro type</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_BIGINT</para>
          </TD>
          <TD>
            <para>Not supported. There is no 64-bit Visual FoxPro type.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIT</para>
          </TD>
          <TD>
            <para>Logical</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CHAR</para>
          </TD>
          <TD>
            <para>Character</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DATE</para>
          </TD>
          <TD>
            <para>Date</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DECIMAL</para>
          </TD>
          <TD>
            <para>Numeric</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DOUBLE</para>
          </TD>
          <TD>
            <para>Double</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_FLOAT</para>
          </TD>
          <TD>
            <para>Double</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTEGER</para>
          </TD>
          <TD>
            <para>Integer</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_LONGVARBINARY</para>
          </TD>
          <TD>
            <para>Memo (Binary)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_LONGVARCHAR</para>
          </TD>
          <TD>
            <para>Memo</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_NUMERIC</para>
          </TD>
          <TD>
            <para>Numeric*, Currency, Float</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_REAL</para>
          </TD>
          <TD>
            <para>Double</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_SMALLINT</para>
          </TD>
          <TD>
            <para>Integer</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TIME</para>
          </TD>
          <TD>
            <para>Not supported. There is no Visual FoxPro <legacyItalic>time</legacyItalic> type.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TIMESTAMP</para>
          </TD>
          <TD>
            <para>DateTime</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TINYINT</para>
          </TD>
          <TD>
            <para>Integer</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_VARBINARY</para>
          </TD>
          <TD>
            <para>Memo (Binary)*, General</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_VARCHAR</para>
          </TD>
          <TD>
            <para>Character</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>*Default type</para>
    <para>For more information about Visual FoxPro data types, see <legacyLink xlink:href="be2143ba-fc16-42c9-84f7-8985cd924860">CREATE TABLE</legacyLink>. For more information about this function, see <legacyLink xlink:href="bdedb044-8924-4ca4-85f3-8b37578e0257">SQLGetTypeInfo</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>