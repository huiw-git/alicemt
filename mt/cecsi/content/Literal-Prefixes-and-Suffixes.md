---
title: Literal Prefixes and Suffixes
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29f468f2-f557-4a92-b31d-569c63cc6272
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Literal Prefixes and Suffixes
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In an SQL statement, a <legacyItalic>literal</legacyItalic> is a character representation of an actual data value. For example, in the following statement, ABC, FFFF, and 10 are literals:</para>
    <code>SELECT CharCol, BinaryCol, IntegerCol FROM MyTable
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10</code>
    <para>Literals for some data types require special prefixes and suffixes. In the preceding example, the character literal (ABC) requires a single quotation mark (') as both a prefix and a suffix, the binary literal (FFFF) requires the characters 0x as a prefix, and the integer literal (10) does not require a prefix or suffix.</para>
    <para>For all data types except date, time, and timestamps, interoperable applications should use the values returned in the LITERAL_PREFIX and LITERAL_SUFFIX columns in the result set created by <legacyBold>SQLGetTypeInfo</legacyBold>. For date, time, timestamp, and datetime interval literals, interoperable applications should use the escape sequences discussed in the preceding section.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>