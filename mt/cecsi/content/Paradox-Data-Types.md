---
title: Paradox Data Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
translation.priority.ht: 
  - en-gb
---
# Paradox Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ODBC Paradox driver maps Paradox data types to ODBC SQL data types. The following table lists all Paradox data types and shows the ODBC SQL data types they are mapped to.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Paradox data type</para>
            </TD>
            <TD>
              <para>ODBC data type</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ALPHANUMERIC</para>
            </TD>
            <TD>
              <para>SQL_VARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AUTOINCREMENT[1]</para>
            </TD>
            <TD>
              <para>SQL_INTEGER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BCD[1]</para>
            </TD>
            <TD>
              <para>SQL_DOUBLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BYTES[1]</para>
            </TD>
            <TD>
              <para>SQL_BINARY</para>
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
              <para>IMAGE[2]</para>
            </TD>
            <TD>
              <para>SQL_LONGVARBINARY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LOGICAL[1]</para>
            </TD>
            <TD>
              <para>SQL_BIT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LONG[1]</para>
            </TD>
            <TD>
              <para>SQL_INTEGER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MEMO[2]</para>
            </TD>
            <TD>
              <para>SQL_LONGVARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MONEY[1]</para>
            </TD>
            <TD>
              <para>SQL_DOUBLE</para>
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
              <para>SHORT</para>
            </TD>
            <TD>
              <para>SQL_SMALLINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TIME[1]</para>
            </TD>
            <TD>
              <para>SQL_TIMESTAMP</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TIMESTAMP[1]</para>
            </TD>
            <TD>
              <para>SQL_TIMESTAMP</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   Valid only for Paradox versions 5.<legacyItalic>x</legacyItalic>.</para>
      <para>[2]   Valid only for Paradox versions 4.<legacyItalic>x</legacyItalic> and 5.<legacyItalic>x</legacyItalic>. </para>
      <alert class="note">
        <para>
          <legacyBold>SQLGetTypeInfo</legacyBold> returns ODBC SQL data types. All conversions in Appendix D of the <legacyItalic>ODBC Programmer's Reference</legacyItalic> are supported for the ODBC SQL data types listed earlier in this topic.</para>
      </alert>
      <para>The following table shows limitations on Paradox data types. </para>
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
              <para>ALPHANUMERIC</para>
            </TD>
            <TD>
              <para>Creating an ALPHANUMERIC column of zero or unspecified length actually returns a 255-byte column.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BYTES</para>
            </TD>
            <TD>
              <para>If you insert NULL into a binary column with the Paradox5 driver, it is changed to 0.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LONG</para>
            </TD>
            <TD>
              <para>The maximum negative value supported by the Paradox driver for the Long data type in Paradox 5.<legacyItalic>x</legacyItalic> is not -2^31 (-2147483648), as it should be since Long maps to the ODBC data type SQL_INTEGER. The maximum negative value supported for Long is actually -2^31 + 1 (-2147483647).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TIMESTAMP</para>
            </TD>
            <TD>
              <para>When a value is inserted into a TIMESTAMP column by the Paradox driver, then subsequently retrieved from the column, the retrieved value may differ from the inserted value by as much as 1 second because of rounding.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>More limitations on data types can be found in <legacyLink xlink:href="81c4eab7-1f6b-47a0-b940-89d6c6a14dae">Data Type Limitations</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>