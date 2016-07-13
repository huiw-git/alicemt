---
title: Data Buffer Type
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Data Buffer Type
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The C data type of a buffer is specified by the application. With a single variable, this occurs when the application allocates the variable. With generic memory — that is, memory pointed to by a pointer of type void — this occurs when the application casts the memory to a particular type. The driver discovers this type in two ways:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Data buffer type argument.</legacyBold> Buffers used to transfer parameter values and result set data, such as the buffer bound with <legacyItalic>TargetValuePtr</legacyItalic> in <legacyBold>SQLBindCol</legacyBold>, usually have an associated type argument, such as the <legacyItalic>TargetType</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold>. In this argument, the application passes the C type identifier that corresponds to the type of the buffer. For example, in the following call to <legacyBold>SQLBindCol</legacyBold>, the value SQL_C_TYPE_DATE tells the driver that the <legacyItalic>Date</legacyItalic> buffer is an SQL_DATE_STRUCT: </para>
        <code>SQL_DATE_STRUCT Date;
SQLINTEGER  DateInd;
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &amp;Date, 0, &amp;DateInd);</code>
        <para>For more information about type identifiers, see the <legacyLink xlink:href="7332d93e-44db-4132-9c10-988dbc13369e">Data Types in ODBC</legacyLink> section, later in this section. </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Predefined type.</legacyBold> Buffers used to send and retrieve options or attributes, such as the buffer pointed to by the <legacyItalic>InfoValuePtr</legacyItalic> argument in <legacyBold>SQLGetInfo</legacyBold>, have a fixed type that depends on the option specified. The driver assumes that the data buffer is of this type; it is the application's responsibility to allocate a buffer of this type. For example, in the following call to <legacyBold>SQLGetInfo</legacyBold>, the driver assumes the buffer is a 32-bit integer because this is what the SQL_STRING_FUNCTIONS option requires: </para>
        <code>SQLUINTEGER StringFuncs;
SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &amp;StringFuncs, 0,
            NULL);</code>
      </listItem>
    </list>
    <para>The driver uses the C data type to interpret the data in the buffer.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>