---
title: SQLColAttributes Mapping
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLColAttributes Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLColAttributes</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call to <legacyBold>SQLColAttributes</legacyBold> is mapped to <legacyBold>SQLColAttribute</legacyBold> as follows:</para>
    <alert class="note">
      <para>The prefix used in <legacyItalic>FieldIdentifier</legacyItalic> values in ODBC 3<legacyItalic>.x</legacyItalic> has been changed from that used in ODBC 2.<legacyItalic>x</legacyItalic>. The new prefix is "SQL_DESC"; the old prefix was "SQL_COLUMN".</para>
    </alert>
    <list class="ordered">
      <listItem>
        <para>If the application is an ODBC 2.<legacyItalic>x</legacyItalic> application, <legacyItalic>fDescType</legacyItalic> is SQL_COLUMN_TYPE, and the returned type is a concise DATETIME type, the Driver Manager maps the return values for date, time, and timestamp codes.</para>
      </listItem>
      <listItem>
        <para>If <legacyItalic>fDescType</legacyItalic> is SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE, or SQL_COLUMN_COUNT, the Driver Manager calls <legacyBold>SQLColAttribute</legacyBold> in the driver with the <legacyItalic>FieldIdentifier</legacyItalic> argument mapped to SQL_DESC_NAME, SQL_DESC_NULLABLE, or SQL_DESC_COUNT, as appropriate<legacyItalic>. </legacyItalic>All other values of <legacyItalic>fDescType </legacyItalic>are passed through to the driver.</para>
      </listItem>
    </list>
    <para>An ODBC 3<legacyItalic>.x</legacyItalic> driver must support all the ODBC 3<legacyItalic>.x</legacyItalic> <legacyItalic>FieldIdentifiers</legacyItalic> listed for <legacyBold>SQLColAttribute</legacyBold>. </para>
    <para>An ODBC 3<legacyItalic>.x</legacyItalic> driver must support SQL_COLUMN_PRECISION and SQL_DESC_PRECISION, SQL_COLUMN_SCALE and SQL_DESC_SCALE, and SQL_COLUMN_LENGTH and SQL_DESC_LENGTH. These values are different because precision, scale, and length are defined differently in ODBC 3<legacyItalic>.x</legacyItalic> than they were in ODBC 2.<legacyItalic>x</legacyItalic>. For more information, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>