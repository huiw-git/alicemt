---
title: LIKE Predicate Escape Character
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# LIKE Predicate Escape Character
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In a <legacyBold>LIKE</legacyBold> predicate, the percent sign (%) matches zero or more of any character and the underscore (_) matches any one character. To match an actual percent sign or underscore in a <legacyBold>LIKE</legacyBold> predicate, an escape character must come before the percent sign or underscore. The escape sequence that defines the <legacyBold>LIKE</legacyBold> predicate escape character is:</para>
    <para>         <legacyBold>{escape '</legacyBold>         <legacyItalic>escape-character</legacyItalic>         <legacyBold>'}</legacyBold>       </para>
    <para>where <legacyItalic>escape-character</legacyItalic> is any character supported by the data source.</para>
    <para>For more information about the LIKE escape sequence, see <legacyLink xlink:href="798d75ea-be9d-4bef-b297-318bc327f1ca">LIKE Escape Sequence</legacyLink> in Appendix C: SQL Grammar.</para>
    <para>For example, the following SQL statements create the same result set of customer names that start with the characters "%AAA". The first statement uses the escape-sequence syntax. The second statement uses the native syntax for Microsoft® Access and is not interoperable. Notice that the second percent character in each <legacyBold>LIKE</legacyBold> predicate is a wildcard character that matches zero or more of any character.</para>
    <code>SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}

SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'</code>
    <para>To determine whether the <legacyBold>LIKE</legacyBold> predicate escape character is supported by a data source, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_LIKE_ESCAPE_CLAUSE option.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>