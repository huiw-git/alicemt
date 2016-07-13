---
title: Display Size
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f7f766f-2492-463c-aab7-f2476e222042
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Display Size
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The display size of a column is the maximum number of characters needed to display data in character form. The following table defines the display size for each ODBC SQL data type.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>SQL type identifier</para>
          </TD>
          <TD>
            <para>Display size</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>All character types[a]</para>
          </TD>
          <TD>
            <para>The defined (for fixed types) or maximum (for variable types) number of characters needed to display the data in character form.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DECIMAL SQL_NUMERIC</para>
          </TD>
          <TD>
            <para>The precision of the column plus 2 (a sign, <legacyItalic>precision</legacyItalic> digits, and a decimal point). For example, the display size of a column defined as NUMERIC(10,3) is 12.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIT</para>
          </TD>
          <TD>
            <para>1 (1 digit).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TINYINT</para>
          </TD>
          <TD>
            <para>4 if signed (a sign and 3 digits) or 3 if unsigned (3 digits).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_SMALLINT</para>
          </TD>
          <TD>
            <para>6 if signed (a sign and 5 digits) or 5 if unsigned (5 digits).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTEGER</para>
          </TD>
          <TD>
            <para>11 if signed (a sign and 10 digits) or 10 if unsigned (10 digits).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIGINT</para>
          </TD>
          <TD>
            <para>20 (a sign and 19 digits if signed or 20 digits if unsigned).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_REAL</para>
          </TD>
          <TD>
            <para>14 (a sign, 7 digits, a decimal point, the letter <legacyItalic>E</legacyItalic>, a sign, and 2 digits).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_FLOAT SQL_DOUBLE</para>
          </TD>
          <TD>
            <para>24 (a sign, 15 digits, a decimal point, the letter <legacyItalic>E</legacyItalic>, a sign, and 3 digits).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>All binary types[a]</para>
          </TD>
          <TD>
            <para>The defined or maximum (for variable types) length of the column times 2. (Each binary byte is represented by a 2-digit hexadecimal number.) </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_DATE</para>
          </TD>
          <TD>
            <para>10 (a date in the format <legacyItalic>yyyy-mm-dd</legacyItalic>).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIME</para>
          </TD>
          <TD>
            <para>8 (a time in the format <legacyItalic>hh:mm:ss</legacyItalic>)</para>
            <para>- or -</para>
            <para>9 + <legacyItalic>s</legacyItalic> (a time in the format <legacyItalic>hh:mm:ss</legacyItalic>[.fff...], where <legacyItalic>s</legacyItalic> is the fractional seconds precision).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIMESTAMP</para>
          </TD>
          <TD>
            <para>19 (for a timestamp in the <legacyItalic>yyyy-mm-dd hh:mm:ss</legacyItalic> format)</para>
            <para>- or -</para>
            <para>20 + <legacyItalic>s</legacyItalic> (for a timestamp in the <legacyItalic>yyyy-mm-dd hh:mm:ss</legacyItalic>[.fff...] format, where <legacyItalic>s</legacyItalic> is the fractional seconds precision).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>All interval data types</para>
          </TD>
          <TD>
            <para>See <legacyLink xlink:href="e9eb38d8-f9db-4401-8c62-aa394054cbbf">Interval Data Type Length</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_GUID</para>
          </TD>
          <TD>
            <para>36 (the number of characters in the <legacyItalic>aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee</legacyItalic> format</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   If the driver cannot determine the column or parameter length of variable types, it returns SQL_NO_TOTAL.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>