---
title: Microsoft Access Data Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
translation.priority.ht: 
  - en-gb
---
# Microsoft Access Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table shows the Microsoft Access data types, data types used to create tables, and ODBC SQL data types. </para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Microsoft Access data type</para>
          </TD>
          <TD>
            <para>Data type (CREATETABLE)</para>
          </TD>
          <TD>
            <para>ODBC SQL data type</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>BIGBINARY[1]</para>
          </TD>
          <TD>
            <para>LONGBINARY</para>
          </TD>
          <TD>
            <para>SQL_LONGVARBINARY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>BINARY</para>
          </TD>
          <TD>
            <para>BINARY</para>
          </TD>
          <TD>
            <para>SQL_BINARY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>BIT</para>
          </TD>
          <TD>
            <para>BIT</para>
          </TD>
          <TD>
            <para>SQL_BIT</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>COUNTER</para>
          </TD>
          <TD>
            <para>COUNTER</para>
          </TD>
          <TD>
            <para>SQL_INTEGER</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CURRENCY</para>
          </TD>
          <TD>
            <para>CURRENCY</para>
          </TD>
          <TD>
            <para>SQL_NUMERIC</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DATE/TIME</para>
          </TD>
          <TD>
            <para>DATETIME</para>
          </TD>
          <TD>
            <para>SQL_TIMESTAMP</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>GUID</para>
          </TD>
          <TD>
            <para>GUID</para>
          </TD>
          <TD>
            <para>SQL_GUID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>LONG BINARY</para>
          </TD>
          <TD>
            <para>LONGBINARY</para>
          </TD>
          <TD>
            <para>SQL_LONGVARBINARY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>LONG TEXT</para>
          </TD>
          <TD>
            <para>LONGTEXT</para>
          </TD>
          <TD>
            <para>SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MEMO</para>
          </TD>
          <TD>
            <para>LONGTEXT</para>
          </TD>
          <TD>
            <para>SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMBER (FieldSize= SINGLE)</para>
          </TD>
          <TD>
            <para>SINGLE</para>
          </TD>
          <TD>
            <para>SQL_REAL</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMBER (FieldSize= DOUBLE)</para>
          </TD>
          <TD>
            <para>DOUBLE</para>
          </TD>
          <TD>
            <para>SQL_DOUBLE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMBER (FieldSize= BYTE)</para>
          </TD>
          <TD>
            <para>UNSIGNED BYTE</para>
          </TD>
          <TD>
            <para>SQL_TINYINT</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMBER (FieldSize= INTEGER)</para>
          </TD>
          <TD>
            <para>SHORT</para>
          </TD>
          <TD>
            <para>SQL_SMALLINT</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMBER (FieldSize= LONG INTEGER)</para>
          </TD>
          <TD>
            <para>LONG</para>
          </TD>
          <TD>
            <para>SQL_INTEGER</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMERIC </para>
          </TD>
          <TD>
            <para>NUMERIC</para>
          </TD>
          <TD>
            <para>SQL_NUMERIC</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>OLE</para>
          </TD>
          <TD>
            <para>LONGBINARY</para>
          </TD>
          <TD>
            <para>SQL_LONGVARBINARY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TEXT</para>
          </TD>
          <TD>
            <para>VARCHAR</para>
          </TD>
          <TD>
            <para>SQL_VARCHAR[1] SQL_WVARCHAR[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>VARBINARY</para>
          </TD>
          <TD>
            <para>VARBINARY</para>
          </TD>
          <TD>
            <para>SQL_VARBINARY</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   Access 4.0 applications only. Maximum length of 4000 bytes. Behavior similar to LONGBINARY.</para>
    <para>[2]   ANSI applications only. </para>
    <para>[3]   Unicode and Access 4.0 applications only.</para>
    <alert class="note">
      <para>           <legacyBold>SQLGetTypeInfo</legacyBold> returns ODBC data types. It will not return all Microsoft Access data types if more than one Microsoft Access type is mapped to the same ODBC SQL data type. All conversions in Appendix D of the <legacyItalic>ODBC Programmer's Reference</legacyItalic> are supported for the SQL data types listed in the previous table.</para>
    </alert>
    <para>The following table shows limitations on Microsoft Access data types. </para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Data type</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>BINARY, VARBINARY, and VARCHAR</para>
          </TD>
          <TD>
            <para>Creating a BINARY, VARBINARY, or VARCHAR column of zero or unspecified length actually returns a 510-byte column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>BYTE</para>
          </TD>
          <TD>
            <para>Even though a Microsoft Access NUMBER field with a FieldSize equal to BYTE is unsigned, a negative number can be inserted into the field when using the Microsoft Access driver.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CHAR, LONGVARCHAR, and VARCHAR</para>
          </TD>
          <TD>
            <para>A character string literal can contain any ANSI character (1-255 decimal). Use two consecutive single quotation marks ('') to represent one single quotation mark (').</para>
            <para>Procedures should be used to pass character data when using any special character in a character data type column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DATE</para>
          </TD>
          <TD>
            <para>Date values must be either delimited according to the ODBC canonical date format or delimited by the datetime delimiter ("#"). Otherwise, Microsoft Access will treat the value as an arithmetic expression and will not raise a warning or error. </para>
            <para>For example, the date "March 5, 1996" must be represented as {d '1996-03-05'} or #03/05/1996#; otherwise, if only 03/05/1993 is submitted, Microsoft Access will evaluate this as 3 divided by 5 divided by 1996. This value rounds up to the integer 0, and since the zero day maps to 1899-12-31, this is the date used.</para>
            <para>A pipe character (|) cannot be used in a date value, even if enclosed in back quotes.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>GUID</para>
          </TD>
          <TD>
            <para>Data type limited to Microsoft Access 4.0.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMERIC</para>
          </TD>
          <TD>
            <para>Data type limited to Microsoft Access 4.0.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>More limitations on data types can be found in <legacyLink xlink:href="81c4eab7-1f6b-47a0-b940-89d6c6a14dae">Data Type Limitations</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>