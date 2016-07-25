---
title: "Microsoft Excel Data Types"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b44c8e5-0bc3-4912-8a5d-56f4d5562fe6
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Microsoft Excel Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table shows how Microsoft Excel driver data types are mapped to ODBC SQL data types. The Microsoft Excel driver assigns these data types to columns in Microsoft Excel tables based on the data in the column.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Microsoft Excel data type</para>
            </TD>
            <TD>
              <para>ODBC data type</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>CURRENCY</para>
            </TD>
            <TD>
              <para>SQL_NUMERIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DATETIME</para>
            </TD>
            <TD>
              <para>SQL_TIMESTAMP</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LOGICAL</para>
            </TD>
            <TD>
              <para>SQL_BIT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NUMBER</para>
            </TD>
            <TD>
              <para>SQL_DOUBLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TEXT</para>
            </TD>
            <TD>
              <para>SQL_VARCHAR</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>
          <legacyBold>SQLGetTypeInfo</legacyBold> returns ODBC SQL data types. All conversions in Appendix D of the <legacyItalic>ODBC Programmer's Reference</legacyItalic> are supported for the ODBC SQL data types listed earlier in this topic.</para>
      </alert>
      <para>The following table shows limitations on Microsoft Excel data types.</para>
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
              <para>Encrypted data</para>
            </TD>
            <TD>
              <para>The Microsoft Excel driver cannot read encrypted data.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Error Strings</para>
            </TD>
            <TD>
              <para>The Microsoft Excel driver cannot return a character string for the Microsoft Excel error values (#N/A!, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, and #NULL!), but returns a NULL instead.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LOGICAL</para>
            </TD>
            <TD>
              <para>The value in a LOGICAL column is returned in a SQL_C_CHAR buffer as either 0 or 1.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NUMBER</para>
            </TD>
            <TD>
              <para>If an integer column is created, numbers that are too big for the integer data type can be entered, and data containing non-integer values can be inserted, with the result that the column may be converted to SQL_DOUBLE.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TEXT</para>
            </TD>
            <TD>
              <para>When the rows of a column contain more than one Microsoft Excel data type, the ODBC Microsoft Excel driver assigns the SQL_VARCHAR data type to the column. There is one exception to this: if the column contains only two or three of the datetime data types (DATE, TIME, and DATETIME), the ODBC Microsoft Excel driver assigns the SQL_TIMESTAMP data type to the column.</para>
              <para>Creating a TEXT column of zero or unspecified length actually returns a 255-byte column.</para>
              <para>A character string literal can contain any ANSI character (1-255 decimal). Use two consecutive single quotation marks (") to represent one single quotation mark (').</para>
              <para>Inserting a NULL into a column with a data type other than SQL_VARCHAR will cause the data type of the column to change to SQL_VARCHAR.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>More limitations on data types can be found in <legacyLink xlink:href="81c4eab7-1f6b-47a0-b940-89d6c6a14dae">Data Type Limitations</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>