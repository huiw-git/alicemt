---
title: Outer Join Escape Sequence
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Outer Join Escape Sequence
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC uses escape sequences for outer joins. The syntax of this escape sequence is as follows: </para>
  </introduction>
  <section>
    <content>
      <code>{oj <legacyItalic>outer-join</legacyItalic>}</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>In BNF notation, the syntax is as follows:</para>
      <para>
        <legacyItalic>ODBC-outer-join-escape</legacyItalic> ::= </para>
      <para>     <legacyItalic>ODBC-esc-initiator</legacyItalic> oj <legacyItalic>outer-join ODBC-esc-terminator </legacyItalic></para>
      <para>
        <legacyItalic>outer-join</legacyItalic> ::= <legacyItalic>table-name</legacyItalic> [<legacyItalic>correlation-name</legacyItalic>] {LEFT | RIGHT | FULL} </para>
      <para>     OUTER JOIN{<legacyItalic>table-name</legacyItalic> [<legacyItalic>correlation-name</legacyItalic>] | <legacyItalic>outer-join</legacyItalic>} ON </para>
      <para>
        <legacyItalic>search-</legacyItalic> </para>
      <para>     <legacyItalic>condition</legacyItalic></para>
      <para>
        <legacyItalic>correlation-name </legacyItalic>::= <legacyItalic>user-defined-name</legacyItalic></para>
      <para>
        <legacyItalic>ODBC-esc-initiator </legacyItalic>::= {</para>
      <para>
        <legacyItalic>ODBC-esc-terminator </legacyItalic>::= }</para>
      <para>To determine which parts of this statement are supported, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_OJ_CAPABILITIES information type. For outer joins, <legacyItalic>search-condition</legacyItalic> must contain only the join condition between the specified <legacyItalic>table-names</legacyItalic>.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>