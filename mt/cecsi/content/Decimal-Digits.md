---
title: "Decimal Digits"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07f3d1fc-b4ee-4693-b342-330b2231b6d0
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Decimal Digits
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyItalic>decimal digits</legacyItalic> of decimal and numeric data types is defined as the maximum number of digits to the right of the decimal point, or the scale of the data. For approximate floating-point number columns or parameters, the scale is undefined because the number of digits to the right of the decimal point is not fixed. For datetime or interval data that contains a seconds component, the decimal digits is defined as the number of digits to the right of the decimal point in the seconds component of the data.</para>
  </introduction>
  <section>
    <content>
      <para>For the SQL_DECIMAL and SQL_NUMERIC data types, the maximum scale is usually the same as the maximum precision. However, some data sources impose a separate limit on the maximum scale. To determine the minimum and maximum scales allowed for a data type, an application calls <legacyBold>SQLGetTypeInfo</legacyBold>.</para>
      <para>The decimal digits defined for each concise SQL data type is shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQL type</para>
            </TD>
            <TD>
              <para>Decimal digits</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>All character and binary types[a]</para>
            </TD>
            <TD>
              <para>n/a</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DECIMAL
SQL_NUMERIC</para>
            </TD>
            <TD>
              <para>The defined number of digits to the right of the decimal point. For example, the scale of a column defined as NUMERIC(10,3) is 3. This can be a negative number to support storage of very large numbers without using exponential notation; for example, "12000" could be stored as "12" with a scale of –3.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All exact numeric types other than SQL_DECIMAL and SQL_NUMERIC[a]</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All approximate data types[a]</para>
            </TD>
            <TD>
              <para>n/a</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TYPE_DATE, and all interval types with no seconds component[a]</para>
            </TD>
            <TD>
              <para>n/a</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All datetime types except SQL_TYPE_DATE, and all interval types with a seconds component</para>
            </TD>
            <TD>
              <para>The number of digits to the right of the decimal point in the seconds part of the value (fractional seconds). This number cannot be negative.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_GUID</para>
            </TD>
            <TD>
              <para>n/a</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[a]   The <legacyItalic>DecimalDigits</legacyItalic> argument of <legacyBold>SQLBindParameter</legacyBold> is ignored for this data type.</para>
      <para>The values returned for the decimal digits do not correspond to the values in any one descriptor field. The values can come from either the SQL_DESC_SCALE or the SQL_DESC_PRECISION field, depending on the data type, as shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQL type</para>
            </TD>
            <TD>
              <para>Descriptor field corresponding to</para>
              <para>decimal digits</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>All character and binary types</para>
            </TD>
            <TD>
              <para>n/a</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All exact numeric types</para>
            </TD>
            <TD>
              <para>SCALE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BIT</para>
            </TD>
            <TD>
              <para>n/a</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All approximate numeric types</para>
            </TD>
            <TD>
              <para>n/a</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All datetime types</para>
            </TD>
            <TD>
              <para>PRECISION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All interval types with a seconds component</para>
            </TD>
            <TD>
              <para>PRECISION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All interval types with no seconds component</para>
            </TD>
            <TD>
              <para>n/a</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>