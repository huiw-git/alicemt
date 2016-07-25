---
title: "Quoted Identifiers"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Quoted Identifiers
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In an SQL statement, identifiers containing special characters or match keywords must be enclosed in <legacyItalic>identifier quote characters</legacyItalic>; identifiers enclosed in such characters are known as <legacyItalic>quoted identifiers </legacyItalic>(also known as <legacyItalic>delimited identifiers </legacyItalic>in SQL-92). For example, the Accounts Payable identifier is quoted in the following <legacyBold>SELECT</legacyBold> statement:</para>
    <code>SELECT * FROM "Accounts Payable"</code>
    <para>The reason for quoting identifiers is to make the statement parseable. For example, if Accounts Payable was not quoted in the previous statement, the parser would assume there were two tables, Accounts and Payable, and return a syntax error that they were not separated by a comma. The identifier quote character is driver-specific and is retrieved with the SQL_IDENTIFIER_QUOTE_CHAR option in <legacyBold>SQLGetInfo</legacyBold>. The lists of special characters and of keywords are retrieved with the SQL_SPECIAL_CHARACTERS and SQL_KEYWORDS options in <legacyBold>SQLGetInfo</legacyBold>.</para>
    <para>To be safe, interoperable applications often quote all identifiers except those for pseudo-columns, such as the ROWID column in Oracle. <legacyBold>SQLSpecialColumns</legacyBold> returns a list of pseudo-columns. Also, if there are application-specific restrictions on where special characters can appear in an object name, it is best for interoperable applications not to use special characters in those positions.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>