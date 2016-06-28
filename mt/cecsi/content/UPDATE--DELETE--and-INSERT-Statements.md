---
title: UPDATE, DELETE, and INSERT Statements
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
translation.priority.ht: 
  - en-gb
---
# UPDATE, DELETE, and INSERT Statements
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>SQL-based applications make changes to tables by executing the <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, and <legacyBold>INSERT</legacyBold> statements. These statements are part of the Minimum SQL grammar conformance level and must be supported by all drivers and data sources.</para>
    <para>The syntax of these statements is:</para>
    <para>
      <legacyBold>UPDATE </legacyBold>         <legacyItalic>table-name</legacyItalic> </para>
    <para>     <legacyBold>SET </legacyBold><legacyItalic>column-identifier</legacyItalic><legacyBold> = </legacyBold>{<legacyItalic>expression</legacyItalic> | <legacyBold>NULL</legacyBold>}</para>
    <para>          [<legacyBold>, </legacyBold><legacyItalic>column-identifier</legacyItalic><legacyBold> = </legacyBold>{<legacyItalic>expression</legacyItalic> | <legacyBold>NULL</legacyBold>}]...</para>
    <para>     [<legacyBold>WHERE </legacyBold><legacyItalic>search-condition</legacyItalic>]</para>
    <para>
      <legacyBold>DELETE FROM</legacyBold> <legacyItalic>table-name</legacyItalic>[<legacyBold>WHERE</legacyBold> <legacyItalic>search-condition</legacyItalic>]</para>
    <para>
      <legacyBold>INSERT INTO</legacyBold> <legacyItalic>table-name</legacyItalic>[<legacyBold>(</legacyBold><legacyItalic>column-identifier</legacyItalic> [<legacyBold>, </legacyBold><legacyItalic>column-identifier</legacyItalic>]...<legacyBold>)</legacyBold>]</para>
    <para>     {<legacyItalic>query-specification</legacyItalic> | <legacyBold>VALUES</legacyBold> <legacyBold>(</legacyBold><legacyItalic>insert-value</legacyItalic> [<legacyBold>, </legacyBold><legacyItalic>insert-value</legacyItalic>]...<legacyBold>)</legacyBold>}</para>
    <para>Note that the <legacyItalic>query-specification</legacyItalic> element is valid only in the Core and Extended SQL grammars, and that the <legacyItalic>expression</legacyItalic> and <legacyItalic>search-condition</legacyItalic> elements become more complex in the Core and Extended SQL grammars.</para>
    <para>Like other SQL statements, <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, and <legacyBold>INSERT</legacyBold> statements are often more efficient when they use parameters. For example, the following statement can be prepared and repeatedly executed to insert multiple rows in the Orders table:</para>
    <code>INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)</code>
    <para>This efficiency can be increased by passing arrays of parameter values. For more information about statement parameters and arrays of parameter values, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>