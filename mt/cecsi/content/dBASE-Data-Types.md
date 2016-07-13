---
title: dBASE Data Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0e31e6b-d02b-4ee2-9b37-5baf6a11c0a6
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# dBASE Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table shows how dBASE data types are mapped to ODBC SQL data types. Note that not all ODBC SQL data types are supported.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>dBASE data type</para>
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
              <para>DATE</para>
            </TD>
            <TD>
              <para>SQL_DATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FLOAT[1]</para>
            </TD>
            <TD>
              <para>SQL_DOUBLE</para>
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
              <para>MEMO</para>
            </TD>
            <TD>
              <para>SQL_LONGVARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NUMERIC (BCD)</para>
            </TD>
            <TD>
              <para>SQL_DOUBLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OLEOBJECT[1]</para>
            </TD>
            <TD>
              <para>SQL_LONGBINARY</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   Valid only for dBASE version 5.<legacyItalic>x</legacyItalic></para>
      <para>Precision in dBASE III allows numbers with up to two-digit exponents and in dBASE IV numbers with up to three-digit exponents. Because numbers are stored as text, they are converted to numbers. If the number to convert does not fit in a field, unexplained results may occur.</para>
      <para>While dBASE allows a precision and a scale to be specified with a NUMERIC data type, it is not supported by the ODBC dBASE driver. The ODBC dBASE driver always returns a precision of 15 and a scale of 0 for a NUMERIC data type.</para>
      <para>A column created with the Numeric data type using the ODBC dBASE driver maps to the SQL_DOUBLE ODBC data type. Thus the data in this column is subject to rounding. This behavior is not the same as that of the NUMERIC data type in dBASE (type N), which is Binary Coded Decimal (BCD).</para>
      <alert class="note">
        <para>
          <legacyBold>SQLGetTypeInfo</legacyBold> returns ODBC SQL data types. All conversions in Appendix D of the <legacyItalic>ODBC Programmer's Reference</legacyItalic> are supported for the ODBC SQL data types listed earlier in this topic.</para>
      </alert>
      <para>The following table shows limitations on dBASE data types.</para>
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
              <para>Creating a CHAR column of zero or unspecified length actually returns a 254-byte column. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Encrypted data</para>
            </TD>
            <TD>
              <para>The dBASE driver does not support encrypted dBASE tables.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LOGICAL</para>
            </TD>
            <TD>
              <para>The dBASE driver cannot create an index on a LOGICAL column.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MEMO</para>
            </TD>
            <TD>
              <para>The maximum length of a MEMO column is 65,500 bytes.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>More limitations on data types can be found in <legacyLink xlink:href="81c4eab7-1f6b-47a0-b940-89d6c6a14dae">Data Type Limitations</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>