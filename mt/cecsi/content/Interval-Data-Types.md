---
title: Interval Data Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fba93f65-c1db-44f4-91ba-532f87241cf7
translation.priority.ht: 
  - en-gb
---
# Interval Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An interval is defined as the difference between two dates and times. Intervals are expressed in one of two different ways. One is a <legacyItalic>year-month</legacyItalic> interval that expresses intervals in terms of years and an integral number of months. The other is a <legacyItalic>day-time</legacyItalic> interval that expresses intervals in terms of days, minutes, and seconds. These two types of intervals are distinct and cannot be mixed, because months can have varying numbers of days.</para>
    <para>An interval consists of a set of fields. There is an implied ordering among the fields. For example, in a year-to-month interval, the year comes first, followed by the month. Similarly, in a day-to-minute interval, the fields are in the order day, hour, and minute. The first field in an interval type is called the <legacyItalic>leading</legacyItalic> field, or the <legacyItalic>high-order</legacyItalic> field. The last field is called the <legacyItalic>trailing</legacyItalic> field.</para>
    <para>In all intervals, the leading field is not constrained by rules of the Gregorian calendar. For example, in an hour-to-minute interval, the hour field is not constrained to be between 0 and 23 (inclusive), as it normally is. The trailing fields subsequent to the leading field follow the usual constraints of the Gregorian calendar. For more information, see <legacyLink xlink:href="70667410-c582-4369-8e06-9d98e21cd2bf">Constraints of the Gregorian Calendar</legacyLink>, later in this appendix.</para>
    <para>There are 13 interval SQL data types and 13 interval C data types. Each of the interval C data types uses the same structure, SQL_INTERVAL_STRUCT, to contain the interval data. (For more information, see the next section, <legacyLink xlink:href="52b42b56-50aa-4ce6-8d79-0963c7a71437">C Interval Structure</legacyLink>.) For more information on the SQL data types, see <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink>; for more information on the C data types, see <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Type identifier</para>
          </TD>
          <TD>
            <para>Class</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>MONTH</para>
          </TD>
          <TD>
            <para>Year-Month</para>
          </TD>
          <TD>
            <para>Number of months between two dates.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>YEAR</para>
          </TD>
          <TD>
            <para>Year-Month</para>
          </TD>
          <TD>
            <para>Number of years between two dates. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>YEAR_TO_MONTH</para>
          </TD>
          <TD>
            <para>Year-Month</para>
          </TD>
          <TD>
            <para>Number of years and months between two dates.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DAY</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of days between two dates.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>HOUR</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of hours between two date/times.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MINUTE</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of minutes between two date/times.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SECOND</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of seconds between two date/times.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DAY_TO_HOUR</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of days/hours between two date/times.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DAY_TO_MINUTE</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of days/hours/minutes between two date/times.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DAY_TO_SECOND</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of days/hours/minutes/seconds between two date/times.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>HOUR_TO_MINUTE</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of hours/minutes between two date/times.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>HOUR_TO_SECOND</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of hours/minutes/seconds between two date/times.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MINUTE_TO_SECOND</para>
          </TD>
          <TD>
            <para>Day-Time</para>
          </TD>
          <TD>
            <para>Number of minutes/seconds between two date/times.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="52b42b56-50aa-4ce6-8d79-0963c7a71437">C Interval Structure</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="eb73bd77-2e7e-4498-a266-4d7c990a0d56">Interval Data Type Precision</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e9eb38d8-f9db-4401-8c62-aa394054cbbf">Interval Data Type Length</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f9e6c3c7-4f98-483f-89d8-ebc5680f021b">Interval Literals</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="3d65493f-dce7-4d29-9f59-c63a4e47918c">Overriding Default Leading and Seconds Precision for Interval Data Types</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>