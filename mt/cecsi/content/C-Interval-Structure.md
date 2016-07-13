---
title: C Interval Structure
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52b42b56-50aa-4ce6-8d79-0963c7a71437
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# C Interval Structure
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each of the C interval data types listed in the <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink> section uses the same structure to contain the interval data. When <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLGetData</legacyBold> is called, the driver returns data into the SQL_INTERVAL_STRUCT structure, uses the value that was specified by the application for the C data types (in the call to <legacyBold>SQLBindCol</legacyBold>, <legacyBold>SQLGetData</legacyBold>, or <legacyBold>SQLBindParameter</legacyBold>) to interpret the contents of SQL_INTERVAL_STRUCT, and populates the <legacyItalic>interval_type</legacyItalic> field of the structure with the <legacyItalic>enum</legacyItalic> value corresponding to the C type. Note that drivers do not read the <legacyItalic>interval_type</legacyItalic> field to determine the type of the interval; they retrieve the value of the SQL_DESC_CONCISE_TYPE descriptor field. When the structure is used for parameter data, the driver uses the value specified by the application in the SQL_DESC_CONCISE_TYPE field of the APD to interpret the contents of SQL_INTERVAL_STRUCT, even if the application sets the value of the <legacyItalic>interval_type</legacyItalic> field to a different value.</para>
  </introduction>
  <section>
    <content>
      <para>This structure is defined as follows:</para>
      <code>typedef struct tagSQL_INTERVAL_STRUCT
{
   SQLINTERVAL interval_type; 
   SQLSMALLINT interval_sign;
   union {
         SQL_YEAR_MONTH_STRUCT   year_month;
         SQL_DAY_SECOND_STRUCT   day_second;
         } intval;
} SQL_INTERVAL_STRUCT;
typedef enum 
{
   SQL_IS_YEAR = 1,
   SQL_IS_MONTH = 2,
   SQL_IS_DAY = 3,
   SQL_IS_HOUR = 4,
   SQL_IS_MINUTE = 5,
   SQL_IS_SECOND = 6,
   SQL_IS_YEAR_TO_MONTH = 7,
   SQL_IS_DAY_TO_HOUR = 8,
   SQL_IS_DAY_TO_MINUTE = 9,
   SQL_IS_DAY_TO_SECOND = 10,
   SQL_IS_HOUR_TO_MINUTE = 11,
   SQL_IS_HOUR_TO_SECOND = 12,
   SQL_IS_MINUTE_TO_SECOND = 13
} SQLINTERVAL;

typedef struct tagSQL_YEAR_MONTH
{
   SQLUINTEGER year;
   SQLUINTEGER month; 
} SQL_YEAR_MONTH_STRUCT;

typedef struct tagSQL_DAY_SECOND
{
   SQLUINTEGER day;
   SQLUINTEGER hour;
   SQLUINTEGER minute;
   SQLUINTEGER second;
   SQLUINTEGER fraction;
} SQL_DAY_SECOND_STRUCT;</code>
      <para>The <legacyItalic>interval_type</legacyItalic> field of the SQL_INTERVAL_STRUCT indicates to the application what structure is held in the union and also what members of the structure are relevant. The <legacyItalic>interval_sign</legacyItalic> field has the value SQL_FALSE if the interval leading field is unsigned; if it is SQL_TRUE, the leading field is negative. The value in the leading field itself is always unsigned, regardless of the value of <legacyItalic>interval_sign</legacyItalic>. The <legacyItalic>interval_sign</legacyItalic> field acts as a sign bit.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>