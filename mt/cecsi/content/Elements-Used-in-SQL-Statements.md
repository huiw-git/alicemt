---
title: Elements Used in SQL Statements
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 85777525-1555-4731-8309-63a464c6b43a
translation.priority.ht: 
  - en-gb
---
# Elements Used in SQL Statements
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following elements are used in the SQL statements listed previously.</para>
  </introduction>
  <section>
    <title>Element</title>
    <content>
      <para>
        <legacyItalic>base-table-identifier</legacyItalic> ::= <legacyItalic>user-defined-name</legacyItalic></para>
      <para>
        <legacyItalic>base-table-name</legacyItalic> ::= <legacyItalic>base-table-identifier</legacyItalic></para>
      <para>
        <legacyItalic>boolean-factor</legacyItalic> ::= [NOT] <legacyItalic>boolean-primary</legacyItalic></para>
      <para>
        <legacyItalic>boolean-primary</legacyItalic> ::= comparison<legacyItalic>-predicate</legacyItalic> | ( <legacyItalic>search-condition</legacyItalic> )</para>
      <para>
        <legacyItalic>boolean-term</legacyItalic> ::= <legacyItalic>boolean-factor</legacyItalic> [AND <legacyItalic>boolean-term</legacyItalic>]</para>
      <para>
        <legacyItalic>character-string-literal</legacyItalic> ::= ''{<legacyItalic>character</legacyItalic>}...'' (<legacyItalic>character </legacyItalic>is any character in the character set of the driver/data source. To include a single literal quote character ('') in a character-string-literal, use two literal quote characters [''''].)</para>
      <para>
        <legacyItalic>column-identifier</legacyItalic> ::= <legacyItalic>user-defined-name</legacyItalic></para>
      <para>
        <legacyItalic>column-name</legacyItalic> ::= [<legacyItalic>table-name</legacyItalic>.]<legacyItalic>column-identifier</legacyItalic></para>
      <para>
        <legacyItalic>comparison-operator</legacyItalic> ::= &lt; | &gt; | &lt;= | &gt;= | = | &lt;&gt;</para>
      <para>
        <legacyItalic>comparison-predicate</legacyItalic> ::= <legacyItalic>expression</legacyItalic> comparison-operator expression</para>
      <para>
        <legacyItalic>data-type</legacyItalic> ::= <legacyItalic>character-string-type</legacyItalic> (<legacyItalic>character-string-type </legacyItalic>is any data type for which the ""DATA_TYPE"" column in the result set returned by SQLGetTypeInfo is either SQL_CHAR or SQL_VARCHAR.)</para>
      <para>
        <legacyItalic>digit</legacyItalic> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 </para>
      <para>
        <legacyItalic>dynamic-parameter</legacyItalic> ::= ?</para>
      <para>
        <legacyItalic>expression </legacyItalic>::= term | expression {+|–} term</para>
      <para>
        <legacyItalic>factor</legacyItalic> ::= [<legacyItalic>+</legacyItalic>|<legacyItalic>–</legacyItalic>]<legacyItalic>primary</legacyItalic></para>
      <para>
        <legacyItalic>insert-value</legacyItalic> ::= </para>
      <para>     <legacyItalic>dynamic-parameter</legacyItalic> </para>
      <para>     | <legacyItalic>literal</legacyItalic> </para>
      <para>     | NULL </para>
      <para>     | USER</para>
      <para>
        <legacyItalic>letter</legacyItalic> ::= <legacyItalic>lower-case-letter | upper-case-letter</legacyItalic></para>
      <para>
        <legacyItalic>literal</legacyItalic> ::= <legacyItalic>character-string-literal</legacyItalic></para>
      <para>
        <legacyItalic>lower-case-letter</legacyItalic> ::= a | b | c | d | e | f | g | h | i | j | k | l | m | n | o | p | q | r | s | t | u | v | w | x | y | z</para>
      <para>
        <legacyItalic>order-by-clause</legacyItalic> ::=    ORDER BY <legacyItalic>sort-specification</legacyItalic> [, <legacyItalic>sort-specification</legacyItalic>]...</para>
      <para>
        <legacyItalic>primary</legacyItalic> ::= <legacyItalic>column-name</legacyItalic> </para>
      <para>     | <legacyItalic>dynamic-parameter</legacyItalic> </para>
      <para>     | <legacyItalic>literal</legacyItalic> </para>
      <para>     | ( <legacyItalic>expression</legacyItalic> )</para>
      <para>
        <legacyItalic>search-condition</legacyItalic> ::= <legacyItalic>boolean-term</legacyItalic> [OR <legacyItalic>search-condition</legacyItalic>]</para>
      <para>
        <legacyItalic>select-list</legacyItalic> ::= * | <legacyItalic>select-sublist</legacyItalic> [, <legacyItalic>select-sublist</legacyItalic>]...  (<legacyItalic>select-list</legacyItalic> cannot contain parameters.)</para>
      <para>
        <legacyItalic>select-sublist</legacyItalic> ::= <legacyItalic>expression</legacyItalic></para>
      <para>
        <legacyItalic>sort-specification</legacyItalic> ::= {<legacyItalic>unsigned-integer | column-name</legacyItalic>} [<legacyItalic>ASC | DESC</legacyItalic>]</para>
      <para>
        <legacyItalic>table-identifier</legacyItalic> ::= <legacyItalic>user-defined-name</legacyItalic></para>
      <para>
        <legacyItalic>table-name</legacyItalic> ::= <legacyItalic>table-identifier</legacyItalic></para>
      <para>
        <legacyItalic>table-reference </legacyItalic>::= <legacyItalic>table-name</legacyItalic></para>
      <para>
        <legacyItalic>table-reference-list</legacyItalic> ::= <legacyItalic>table-reference</legacyItalic> [,<legacyItalic>table-reference</legacyItalic>]...</para>
      <para>         <legacyItalic>term</legacyItalic> ::= <legacyItalic>factor</legacyItalic> | <legacyItalic>term</legacyItalic> {*|<legacyItalic>/</legacyItalic>} <legacyItalic>factor</legacyItalic></para>
      <para>         <legacyItalic>unsigned-integer</legacyItalic> ::= {<legacyItalic>digit</legacyItalic>}</para>
      <para>         <legacyItalic>upper-case-letter</legacyItalic> ::= <legacyItalic>A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z</legacyItalic></para>
      <para>         <legacyItalic>user-defined-name</legacyItalic> ::= <legacyItalic>letter</legacyItalic>[<legacyItalic>digit</legacyItalic> | <legacyItalic>letter</legacyItalic> | <legacyItalic>_</legacyItalic>]...</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>