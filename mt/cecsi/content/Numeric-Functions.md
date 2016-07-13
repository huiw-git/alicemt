---
title: Numeric Functions
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fa548dc-e8b0-4179-92ff-81d6a79d10c3
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Numeric Functions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table describes numeric functions that are included in the ODBC scalar function set. By calling <legacyBold>SQLGetInfo</legacyBold> with an <legacyItalic>information type</legacyItalic> of SQL_NUMERIC_FUNCTIONS, an application can determine which numeric functions are supported by a driver.</para>
  </introduction>
  <section>
    <content>
      <para>All numeric functions return values of data type SQL_FLOAT except for ABS, ROUND, TRUNCATE, SIGN, FLOOR, and CEILING, which return values of the same data type as the input parameters.</para>
      <para>Arguments denoted as <legacyItalic>numeric_exp</legacyItalic> can be the name of a column, the result of another scalar function, or a <legacyItalic>numeric-litera</legacyItalic>l, where the underlying data type could be represented as SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, or SQL_DOUBLE.</para>
      <para>Arguments denoted as <legacyItalic>float_exp</legacyItalic> can be the name of a column, the result of another scalar function, or a <legacyItalic>numeric-literal</legacyItalic>, where the underlying data type can be represented as SQL_FLOAT.</para>
      <para>Arguments denoted as <legacyItalic>integer_exp</legacyItalic> can be the name of a column, the result of another scalar function, or a <legacyItalic>numeric-literal</legacyItalic>, where the underlying data type can be represented as SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, or SQL_BIGINT.</para>
      <para>The CURRENT_DATE, CURRENT_TIME, and CURRENT_TIMESTAMP scalar functions have been added in ODBC 3.0 to align with SQL-92.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Function</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
              <legacyBold>ABS(</legacyBold>
              <legacyItalic>numeric_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the absolute value of <legacyItalic>numeric_exp</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>ACOS(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the arccosine of <legacyItalic>float_exp</legacyItalic> as an angle, expressed in radians.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>ASIN(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the arcsine of <legacyItalic>float_exp</legacyItalic> as an angle, expressed in radians.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>ATAN(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the arctangent of <legacyItalic>float_exp</legacyItalic> as an angle, expressed in radians.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>ATAN2(</legacyBold>
              <legacyItalic>float_exp1</legacyItalic>, <legacyItalic>float_exp2</legacyItalic><legacyBold>) </legacyBold>
(ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns the arctangent of the <legacyItalic>x</legacyItalic> and <legacyItalic>y</legacyItalic> coordinates, specified by <legacyItalic>float_exp1</legacyItalic> and <legacyItalic>float_exp2</legacyItalic>, respectively, as an angle, expressed in radians.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>CEILING(</legacyBold>
              <legacyItalic>numeric_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the smallest integer greater than or equal to <legacyItalic>numeric_exp</legacyItalic>. The return value is of the same data type as the input parameter.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>COS(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the cosine of <legacyItalic>float_exp</legacyItalic>, where <legacyItalic>float_exp</legacyItalic> is an angle expressed in radians.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>COT(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the cotangent of <legacyItalic>float_exp</legacyItalic>, where <legacyItalic>float_exp</legacyItalic> is an angle expressed in radians.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>DEGREES(</legacyBold>
              <legacyItalic>numeric_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns the number of degrees converted from <legacyItalic>numeric_exp</legacyItalic> radians.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>EXP(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the exponential value of <legacyItalic>float_exp</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>FLOOR(</legacyBold>
              <legacyItalic>numeric_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the largest integer less than or equal to <legacyItalic>numeric_exp</legacyItalic>. The return value is of the same data type as the input parameter.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>LOG(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the natural logarithm of <legacyItalic>float_exp</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>LOG10(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns the base 10 logarithm of <legacyItalic>float_exp</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>MOD(</legacyBold>
              <legacyItalic>integer_exp1</legacyItalic>, <legacyItalic>integer_exp2</legacyItalic><legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the remainder (modulus) of <legacyItalic>integer_exp1</legacyItalic> divided by <legacyItalic>integer_exp2</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>PI( ) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the constant value of pi as a floating-point value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>POWER(</legacyBold>
              <legacyItalic>numeric_exp</legacyItalic>, <legacyItalic>integer_exp</legacyItalic><legacyBold>) </legacyBold>
(ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns the value of <legacyItalic>numeric_exp</legacyItalic> to the power of <legacyItalic>integer_exp</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>RADIANS(</legacyBold>
              <legacyItalic>numeric_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns the number of radians converted from <legacyItalic>numeric_exp</legacyItalic> degrees.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>RAND(</legacyBold>[<legacyItalic>integer_exp</legacyItalic>]<legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns a random floating-point value using <legacyItalic>integer_exp</legacyItalic> as the optional seed value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>ROUND(</legacyBold>
              <legacyItalic>numeric_exp</legacyItalic>, <legacyItalic>integer_exp</legacyItalic><legacyBold>) </legacyBold>
(ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns <legacyItalic>numeric_exp</legacyItalic> rounded to <legacyItalic>integer_exp</legacyItalic> places right of the decimal point. If <legacyItalic>integer_exp</legacyItalic> is negative, <legacyItalic>numeric_exp</legacyItalic> is rounded to |<legacyItalic>integer_exp</legacyItalic>| places to the left of the decimal point.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SIGN(</legacyBold>
              <legacyItalic>numeric_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns an indicator of the sign of <legacyItalic>numeric_exp</legacyItalic>. If <legacyItalic>numeric_exp</legacyItalic> is less than zero, –1 is returned. If <legacyItalic>numeric_exp</legacyItalic> equals zero, 0 is returned. If <legacyItalic>numeric_exp</legacyItalic> is greater than zero, 1 is returned.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SIN(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the sine of <legacyItalic>float_exp</legacyItalic>, where <legacyItalic>float_exp</legacyItalic> is an angle expressed in radians.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQRT(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the square root of <legacyItalic>float_exp</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>TAN(</legacyBold>
              <legacyItalic>float_exp</legacyItalic>
              <legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the tangent of <legacyItalic>float_exp</legacyItalic>, where <legacyItalic>float_exp</legacyItalic> is an angle expressed in radians.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>TRUNCATE(</legacyBold>
              <legacyItalic>numeric_exp</legacyItalic>, <legacyItalic>integer_exp</legacyItalic><legacyBold>) </legacyBold>
(ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns <legacyItalic>numeric_exp</legacyItalic> truncated to <legacyItalic>integer_exp</legacyItalic> places right of the decimal point. If <legacyItalic>integer_exp</legacyItalic> is negative, <legacyItalic>numeric_exp</legacyItalic> is truncated to |<legacyItalic>integer_exp</legacyItalic>| places to the left of the decimal point.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>