---
title: Interval Literals
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9e6c3c7-4f98-483f-89d8-ebc5680f021b
translation.priority.ht: 
  - en-gb
---
# Interval Literals
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC requires that all drivers support conversion of the SQL_CHAR or SQL_VARCHAR data type to all C interval data types. If the underlying data source does not support interval data types, however, the driver needs to know the correct format of the value in the SQL_CHAR field in order to support these conversions. Similarly, ODBC requires that any ODBC C type be convertible to SQL_CHAR or SQL_VARCHAR, so a driver needs to know what format an interval stored in the character field should have. This section describes the syntax of interval literals, which the driver writer needs to use to validate the SQL_CHAR fields during conversion either to or from C interval data types.</para>
    <alert class="note">
      <para>The complete BNF syntax for interval literals is shown in the section <legacyLink xlink:href="2f2d22c1-51d6-4055-9f5a-53bc31e9fea0">Interval Literal Syntax</legacyLink> in Appendix C: SQL Grammar.</para>
    </alert>
    <para>To pass interval literals as part of an SQL statement, an escape clause syntax is defined for interval literals. For more information, see <legacyLink xlink:href="2b42a52a-6353-494c-a179-3a7533cd729f">Date, Time, and Timestamp Literals</legacyLink>.</para>
    <para>An interval literal is of the form:</para>
    <code>INTERVAL[&lt;sign&gt;] '<legacyItalic>value'</legacyItalic> &lt;interval qualifier&gt;</code>
    <para>where "INTERVAL" indicates that the character literal is an interval. The sign can be either plus or minus; it is outside the interval string and is optional.</para>
    <para>The interval qualifier can either be a single datetime field or be composed of two datetime fields, in the form: &lt;<legacyItalic>leading field</legacyItalic>&gt; TO &lt;<legacyItalic>trailing field</legacyItalic>&gt;.  </para>
    <list class="bullet">
      <listItem>
        <para>When the interval is composed of a single field, the single field can be a non-second field that may be accompanied by an optional leading precision in parentheses. The single datetime field can also be a second field that may be accompanied by the optional leading precision, the optional fractional-seconds precision in parentheses, or both. If both a leading precision and a fractional-seconds precision are present for a seconds field, they are separated by commas. If the seconds field has a fractional-seconds precision, it must also have a leading precision.</para>
      </listItem>
      <listItem>
        <para>When the interval is composed of leading and trailing fields, the leading field is a non-second field that may be accompanied by the interval leading field precision in parentheses. The trailing field can be either a non-second field or a second field that may be accompanied by an interval fractional-seconds precision in parentheses.</para>
      </listItem>
    </list>
    <para>The interval string in <legacyItalic>value</legacyItalic> is enclosed in single quotation marks. It can be either a year-month literal or a day-time literal. The format of the string in <legacyItalic>value</legacyItalic> is determined by the following rules:  </para>
    <list class="bullet">
      <listItem>
        <para>The string contains a decimal value for every field that is implied by the &lt;<legacyItalic>interval</legacyItalic> <legacyItalic>qualifier</legacyItalic>&gt;.</para>
      </listItem>
      <listItem>
        <para>If the interval precision includes the fields YEAR and MONTH, the values of these fields are separated by a minus sign.</para>
      </listItem>
      <listItem>
        <para>If the interval precision includes the fields DAY and HOUR, the values of these fields are separated by a space.</para>
      </listItem>
      <listItem>
        <para>If the interval precision includes the field HOUR and the lower order fields (MINUTE and SECOND), the values of these fields are separated by a colon.</para>
      </listItem>
      <listItem>
        <para>If the interval precision includes a SECOND field and the expressed or implied seconds precision is nonzero, the character immediately before the first digit of the fractional part of the second is a period.</para>
      </listItem>
      <listItem>
        <para>No field can be more than two digits long, except: </para>
        <list class="bullet">
          <listItem>
            <para>The value of the leading field can be as long as the expressed or implied interval leading precision.</para>
          </listItem>
          <listItem>
            <para>The fractional part of the SECOND field can be as long as the expressed or implied seconds precision.</para>
          </listItem>
          <listItem>
            <para>The trailing fields follow the usual constraints of the Gregorian calendar. (See <legacyLink xlink:href="70667410-c582-4369-8e06-9d98e21cd2bf">Constraints of the Gregorian Calendar</legacyLink>.)</para>
          </listItem>
        </list>
      </listItem>
    </list>
    <para>The following table lists examples of valid interval literals as included in the ODBC escape clause for intervals. The syntax of the escape clause is as follows:</para>
    <alert class="note">
      <para>           <legacyItalic>{INTERVAL sign interval-string interval-qualifier}</legacyItalic>         </para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Literal escape clause</para>
          </TD>
          <TD>
            <para>Interval specified</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>{INTERVAL '326' YEAR(4)}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 326 years. The interval leading precision is 4.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '326' MONTH(3)}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 326 months. The interval leading precision is 3.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '3261' DAY(4)}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 3261 days. The interval leading precision is 4.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163' HOUR(3)}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 163 days. The interval leading precision is 3.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163' MINUTE(3)}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 163 minutes. The interval leading precision is 3.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '223.16' SECOND(3,2)}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 223.16 seconds. The interval leading precision is 3, and the seconds precision is 2.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163-11' YEAR(3) TO MONTH}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 163 years and 11 months. The interval leading precision is 3.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163 12' DAY(3) TO HOUR}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 163 days and 12 hours. The interval leading precision is 3.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163 12:39' DAY(3) TO MINUTE}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 163 days, 12 hours, and 39 minutes. The interval leading precision is 3.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163 12:39:59.163' DAY(3) TO SECOND(3)}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 163 days, 12 hours, 39 minutes, and 59.163 seconds. The interval leading precision is 3, and the seconds precision is 3.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163:39' HOUR(3) TO MINUTE}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 163 hours and 39 minutes. The interval leading precision is 3.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163:39:59.163' HOUR(3) TO SECOND(4)}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 163 hours, 39 minutes, and 59.163 seconds. The interval leading precision is 3, and the seconds precision is 4.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163:59.163' MINUTE(3) TO SECOND(5)}</para>
          </TD>
          <TD>
            <para>Specifies an interval of 163 minutes and 59.163 seconds. The interval leading precision is 3, and the seconds precision is 5.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL -'16 23:39:56.23' DAY TO SECOND}</para>
          </TD>
          <TD>
            <para>Specifies an interval of minus 16 days, 23 hours, 39 minutes, and 56.23 seconds. The implied leading precision is 2, and the implied seconds precision is 6.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The following table lists examples of invalid interval literals:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Literal escape clause</para>
          </TD>
          <TD>
            <para>Reason why invalid</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>{INTERVAL '163' HOUR(2)}</para>
          </TD>
          <TD>
            <para>The interval leading precision is 2, but the value of the leading field is 163.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '223.16' SECOND(2,2)}</para>
            <para>{INTERVAL '223.16' SECOND(3,1)}</para>
          </TD>
          <TD>
            <para>In the first example, the leading precision is too small, and in the second example, the seconds precision is too small.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '223.16' SECOND}</para>
            <para>{INTERVAL '223' YEAR}</para>
          </TD>
          <TD>
            <para>Because the leading precision is unspecified, it defaults to 2, which is too small to hold the specified literal.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '22.1234567' SECOND}</para>
          </TD>
          <TD>
            <para>The seconds precision is unspecified, so it defaults to 6. The literal has seven digits after the decimal point.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>{INTERVAL '163-13' YEAR(3) TO MONTH}</para>
            <para>{INTERVAL '163 65' DAY(3) TO HOUR}</para>
            <para>{INTERVAL '163 62:39' DAY(3) TO MINUTE}</para>
            <para>{INTERVAL '163 12:125:59.163' DAY(3) TO SECOND(3)}</para>
            <para>{INTERVAL '163:144' HOUR(3) TO MINUTE}</para>
            <para>{INTERVAL '163:567:234.163' HOUR(3) TO SECOND(4)}</para>
            <para>{INTERVAL '163:591.163' MINUTE(3) TO SECOND(5)}</para>
          </TD>
          <TD>
            <para>The trailing field does not follow the rules of the Gregorian calendar. </para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>