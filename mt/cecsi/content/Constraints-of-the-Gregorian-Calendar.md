---
title: Constraints of the Gregorian Calendar
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Constraints of the Gregorian Calendar
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Date and datetime data types, and the trailing fields of interval data types, must conform to the constraints of the Gregorian calendar. These constraints are as follows:

</para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>The value of the month field must be between 1 and 12, inclusive.</para>
        </listItem>
        <listItem>
          <para>The value of the day field must be in the range from 1 through the number of days in the month. The number of days in the month is determined from the values of the year and months fields and can be 28, 29, 30, or 31. (The number of days in the month can also depend on whether it is a leap year.)</para>
        </listItem>
        <listItem>
          <para>The value of the hour field must be between 0 and 23, inclusive.</para>
        </listItem>
        <listItem>
          <para>The value of the minute field must be between 0 and 59, inclusive.</para>
        </listItem>
        <listItem>
          <para>For the trailing seconds field of interval data types, the value of the seconds field must be between 0 and 59.9(<legacyItalic>n</legacyItalic>), inclusive, where <legacyItalic>n</legacyItalic> is the number of digits in the fractional seconds precision.</para>
        </listItem>
        <listItem>
          <para>For the trailing seconds field of datetime data types, the value of the seconds field must be between 0 and 61.9(<legacyItalic>n</legacyItalic>), inclusive, where <legacyItalic>n</legacyItalic> specifies the number of "9" digits and the value of <legacyItalic>n </legacyItalic>is the fractional seconds precision. (The range of seconds allows as many as two leap seconds to maintain synchronization of sidereal time.)</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>