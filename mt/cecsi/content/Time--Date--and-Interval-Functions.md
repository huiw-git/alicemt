---
title: Time, Date, and Interval Functions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bdf054a0-7aba-4e99-a34a-799917376fd5
translation.priority.ht: 
  - en-gb
---
# Time, Date, and Interval Functions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists time and date functions that are included in the ODBC scalar function set. An application can determine which time and date functions are supported by a driver by calling <legacyBold>SQLGetInfo</legacyBold> with an <legacyItalic>information type</legacyItalic> of SQL_TIMEDATE_FUNCTIONS.</para>
    <para>Arguments denoted as <legacyItalic>timestamp_exp</legacyItalic> can be the name of a column, the result of another scalar function, or an <legacyItalic>ODBC-time-escape</legacyItalic>, <legacyItalic>ODBC-date- escape</legacyItalic>, or <legacyItalic>ODBC-timestamp-escape</legacyItalic>, where the underlying data type could be represented as SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, SQL_TYPE_DATE, or SQL_TYPE_TIMESTAMP.</para>
    <para>Arguments denoted as <legacyItalic>date_exp</legacyItalic> can be the name of a column, the result of another scalar function, or an <legacyItalic>ODBC-date- escape</legacyItalic> or <legacyItalic>ODBC-timestamp-escape</legacyItalic>, where the underlying data type could be represented as SQL_CHAR, SQL_VARCHAR, SQL_TYPE_DATE, or SQL_TYPE_TIMESTAMP.</para>
    <para>Arguments denoted as <legacyItalic>time_exp</legacyItalic> can be the name of a column, the result of another scalar function, or an <legacyItalic>ODBC-time-escape</legacyItalic> or <legacyItalic>ODBC-timestamp-escape</legacyItalic>, where the underlying data type could be represented as SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, or SQL_TYPE_TIMESTAMP.</para>
    <para>The CURRENT_DATE, CURRENT_TIME, and CURRENT_TIMESTAMP timedate scalar functions have been added in ODBC 3.0 to align with SQL-92.</para>
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
              <legacyBold>CURRENT_DATE( )</legacyBold> (ODBC 3.0)</para>
          </TD>
          <TD>
            <para>Returns the current date.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>CURRENT_TIME[(</legacyBold>
              <legacyItalic>time-precision</legacyItalic>
              <legacyBold>)]</legacyBold> (ODBC 3.0)</para>
          </TD>
          <TD>
            <para>Returns the current local time. The <legacyItalic>time-precision</legacyItalic> argument determines the seconds precision of the returned value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>CURRENT_TIMESTAMP</legacyBold> <legacyBold>[(</legacyBold><legacyItalic>timestamp-precision</legacyItalic><legacyBold>)]</legacyBold> (ODBC 3.0)</para>
          </TD>
          <TD>
            <para>Returns the current local date and local time as a timestamp value. The <legacyItalic>timestamp-precision</legacyItalic> argument determines the seconds precision of the returned timestamp.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>CURDATE( )</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the current date.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>CURTIME( )</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the current local time.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>DAYNAME(</legacyBold>
              <legacyItalic>date_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 2.0)</para>
          </TD>
          <TD>
            <para>Returns a character string containing the data source–specific name of the day (for example, Sunday through Saturday or Sun. through Sat. for a data source that uses English, or Sonntag through Samstag for a data source that uses German) for the day portion of <legacyItalic>date_exp</legacyItalic>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>DAYOFMONTH(</legacyBold>
              <legacyItalic>date_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the day of the month based on the month field in <legacyItalic>date_exp</legacyItalic> as an integer value in the range of 1–31.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>DAYOFWEEK(</legacyBold>
              <legacyItalic>date_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the day of the week based on the week field in <legacyItalic>date_exp</legacyItalic> as an integer value in the range of 1–7, where 1 represents Sunday.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>DAYOFYEAR(</legacyBold>
              <legacyItalic>date_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the day of the year based on the year field in <legacyItalic>date_exp</legacyItalic> as an integer value in the range of 1–366.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>EXTRACT(</legacyBold>
              <legacyItalic>extract-field FROM</legacyItalic> <legacyItalic>extract-source</legacyItalic><legacyBold>)</legacyBold> (ODBC 3.0)</para>
          </TD>
          <TD>
            <para>Returns the <legacyItalic>extract-field</legacyItalic> portion of the <legacyItalic>extract-source</legacyItalic>. The <legacyItalic>extract-source</legacyItalic> argument is a datetime or interval expression. The <legacyItalic>extract-field</legacyItalic> argument can be one of the following keywords:</para>
            <para>YEAR MONTH DAY HOUR MINUTE SECOND</para>
            <para>The precision of the returned value is implementation-defined. The scale is 0 unless SECOND is specified, in which case the scale is not less than the fractional seconds precision of the <legacyItalic>extract-source</legacyItalic> field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>HOUR(</legacyBold>
              <legacyItalic>time_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the hour based on the hour field in <legacyItalic>time_exp</legacyItalic> as an integer value in the range of 0–23.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>MINUTE(</legacyBold>
              <legacyItalic>time_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the minute based on the minute field in <legacyItalic>time_exp</legacyItalic> as an integer value in the range of 0–59.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>MONTH(</legacyBold>
              <legacyItalic>date_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the month based on the month field in <legacyItalic>date_exp</legacyItalic> as an integer value in the range of 1–12.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>MONTHNAME(</legacyBold>
              <legacyItalic>date_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 2.0)</para>
          </TD>
          <TD>
            <para>Returns a character string containing the data source–specific name of the month (for example, January through December or Jan. through Dec. for a data source that uses English, or Januar through Dezember for a data source that uses German) for the month portion of <legacyItalic>date_exp</legacyItalic>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>NOW( )</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns current date and time as a timestamp value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>QUARTER(</legacyBold>
              <legacyItalic>date_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the quarter in <legacyItalic>date_exp</legacyItalic> as an integer value in the range of 1–4, where 1 represents January 1 through March 31.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SECOND(</legacyBold>
              <legacyItalic>time_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the second based on the second field in <legacyItalic>time_exp</legacyItalic> as an integer value in the range of 0–59.</para>
            <para>Returns the timestamp calculated by adding <legacyItalic>integer_exp</legacyItalic> intervals of type <legacyItalic>interval</legacyItalic> to <legacyItalic>timestamp_exp</legacyItalic>. Valid values of <legacyItalic>interval</legacyItalic> are the following keywords:</para>
            <para>SQL_TSI_FRAC_SECOND</para>
            <para>SQL_TSI_SECOND</para>
            <para>SQL_TSI_MINUTE</para>
            <para>SQL_TSI_HOUR</para>
            <para>SQL_TSI_DAY</para>
            <para>SQL_TSI_WEEK</para>
            <para>SQL_TSI_MONTH</para>
            <para>SQL_TSI_QUARTER</para>
            <para>SQL_TSI_YEAR</para>
            <para>where fractional seconds are expressed in billionths of a second. For example, the following SQL statement returns the name of each employee and his or her one-year anniversary date:</para>
            <para>SELECT NAME, {fn  TIMESTAMPADD(SQL_TSI_YEAR, 1, HIRE_DATE)} FROM  EMPLOYEES</para>
            <para>If <legacyItalic>timestamp_exp</legacyItalic> is a time value and <legacyItalic>interval</legacyItalic> specifies days, weeks, months, quarters, or years, the date portion of <legacyItalic>timestamp_exp</legacyItalic> is set to the current date before calculating the resulting timestamp.</para>
            <para>If <legacyItalic>timestamp_exp</legacyItalic> is a date value and <legacyItalic>interval</legacyItalic> specifies fractional seconds, seconds, minutes, or hours, the time portion of <legacyItalic>timestamp_exp</legacyItalic> is set to 0 before calculating the resulting timestamp.</para>
            <para>An application determines which intervals a data source supports by calling <legacyBold>SQLGetInfo</legacyBold> with the SQL_TIMEDATE_ADD_INTERVALS option.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>TIMESTAMPDIFF(</legacyBold>
              <legacyItalic>interval</legacyItalic>, <legacyItalic>timestamp_exp1</legacyItalic>, <legacyItalic>timestamp_exp2</legacyItalic><legacyBold>)</legacyBold> (ODBC 2.0)</para>
          </TD>
          <TD>
            <para>Returns the integer number of intervals of type <legacyItalic>interval</legacyItalic> by which <legacyItalic>timestamp_exp2</legacyItalic> is greater than <legacyItalic>timestamp_exp1</legacyItalic>. Valid values of <legacyItalic>interval</legacyItalic> are the following keywords:</para>
            <para>SQL_TSI_FRAC_SECOND</para>
            <para>SQL_TSI_SECOND</para>
            <para>SQL_TSI_MINUTE</para>
            <para>SQL_TSI_HOUR</para>
            <para>SQL_TSI_DAY</para>
            <para>SQL_TSI_WEEK</para>
            <para>SQL_TSI_MONTH</para>
            <para>SQL_TSI_QUARTER</para>
            <para>SQL_TSI_YEAR</para>
            <para>where fractional seconds are expressed in billionths of a second. For example, the following SQL statement returns the name of each employee and the number of years he or she has been employed:</para>
            <para>SELECT NAME, {fn  TIMESTAMPDIFF(SQL_TSI_YEAR, {fn CURDATE()}, HIRE_DATE)} FROM EMPLOYEES</para>
            <para>If either timestamp expression is a time value and <legacyItalic>interval</legacyItalic> specifies days, weeks, months, quarters, or years, the date portion of that timestamp is set to the current date before calculating the difference between the timestamps.</para>
            <para>If either timestamp expression is a date value and <legacyItalic>interval</legacyItalic> specifies fractional seconds, seconds, minutes, or hours, the time portion of that timestamp is set to 0 before calculating the difference between the timestamps.</para>
            <para>An application determines which intervals a data source supports by calling <legacyBold>SQLGetInfo</legacyBold> with the SQL_TIMEDATE_DIFF_INTERVALS option.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>WEEK(</legacyBold>
              <legacyItalic>date_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the week of the year based on the week field in <legacyItalic>date_exp</legacyItalic> as an integer value in the range of 1–53.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>YEAR(</legacyBold>
              <legacyItalic>date_exp</legacyItalic>
              <legacyBold>)</legacyBold> (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>Returns the year based on the year field in <legacyItalic>date_exp</legacyItalic> as an integer value. The range is data source–dependent.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>