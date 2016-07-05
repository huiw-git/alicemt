---
title: Text File Data Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e113112e-ae42-469e-8e4b-a365a10d9071
translation.priority.ht: 
  - en-gb
---
# Text File Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table shows how text data types are mapped to ODBC SQL data types. Note that not all ODBC SQL data types are supported by the ODBC Text driver.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Text data type</para>
          </TD>
          <TD>
            <para>ODBC data type</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>CHAR</para>
          </TD>
          <TD>
            <para>SQL_VARCHAR</para>
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
            <para>SQL_INTEGER</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>LONGCHAR</para>
          </TD>
          <TD>
            <para>SQL_LONGVARCHAR</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <alert class="note">
      <para>
        <legacyBold>SQLGetTypeInfo</legacyBold> returns ODBC data types. All conversions in Appendix D of the <legacyItalic>ODBC Programmer's Reference</legacyItalic> are supported for the SQL data types listed in the previous table.</para>
    </alert>
    <para>The following table shows limitations on Text data types. </para>
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
            <para>CHAR</para>
          </TD>
          <TD>
            <para>Creating a CHAR column of zero or unspecified length actually returns a 255-bit column.</para>
            <para>In delimited files, a CHAR column may or may not have double quotation mark delimiters at the beginning and the end; in fixed-length files, double quotation marks are not used as delimiters.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DATETIME</para>
          </TD>
          <TD>
            <para>MM-DD-YY (for example, 01-17-92)</para>
            <para>MMM-DD-YY (for example, Jan-17-92)</para>
            <para>DD-MMM-YY (for example, 17-Jan-92)</para>
            <para>YYYY-MM-DD (for example, 1992-01-17)</para>
            <para>YYYY-MMM-DD (for example, 1992-Jan-17)</para>
            <para>Mixed date separators are not allowed within a table.</para>
            <para>The Text ISAM formats a DATETIME field in the United States or European format, depending upon the International setting in the Windows Control Panel.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FLOAT</para>
          </TD>
          <TD>
            <para>The maximum width includes the sign and decimal point. In Schema.ini, the width is denoted as follows:</para>
            <para>14.083 is FLOAT Width 6</para>
            <para>-14.083 is FLOAT Width 7</para>
            <para>+14.083 is FLOAT Width 7</para>
            <para>14083. is FLOAT Width 6</para>
            <para>ODBC always returns 8 for FLOAT columns.</para>
            <para>FLOAT columns can also be in scientific notation, for example:</para>
            <para>-3.04E+2 is Float Width 8</para>
            <para>25E4 is Float Width 4</para>
            <para>
              <legacyBold>Note   </legacyBold>Decimal and scientific notation cannot be mixed in a column.</para>
            <para>NULL values are represented by a blank padded string in fixed-length files, and are omitted in delimited files.</para>
            <para>Float data can be padded with leading blanks.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>INTEGER</para>
          </TD>
          <TD>
            <para>Valid values for INTEGER columns are 32767 to -32766.</para>
            <para>In Schema.ini, the width is denoted as follows:</para>
            <para>14083 is INTEGER Width 5</para>
            <para>0 is INTEGER Width 1</para>
            <para>ODBC always returns 4 for INTEGER columns.</para>
            <para>The maximum width includes a sign. The maximum width of an INTEGER column is 11, although the width can be greater due to blanks that are allowed in fixed-format tables. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>LONGCHAR</para>
          </TD>
          <TD>
            <para>The theoretical limit on the width of a LONGCHAR column in either a fixed-length or delimited table is 65500K. The Text ISAM is more likely to provide reliable support up to about 32K.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>More limitations on data types can be found in <legacyLink xlink:href="81c4eab7-1f6b-47a0-b940-89d6c6a14dae">Data Type Limitations</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>