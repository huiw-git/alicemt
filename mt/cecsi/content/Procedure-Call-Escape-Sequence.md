---
title: Procedure Call Escape Sequence
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Procedure Call Escape Sequence
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC uses escape sequences for procedure calls. The syntax of this escape sequence is as follows: </para>
  </introduction>
  <section>
    <content>
      <para>
        <legacyBold>{</legacyBold>[?=]<legacyBold>call</legacyBold> <legacyItalic>procedure-name</legacyItalic>[<legacyBold>(</legacyBold>[<legacyItalic>parameter</legacyItalic>][,[<legacyItalic>parameter</legacyItalic>]]...<legacyBold>)</legacyBold>]<legacyBold>}</legacyBold></para>
      <para>In BNF notation, the syntax is as follows:</para>
      <para>
        <legacyItalic>ODBC-procedure-escape</legacyItalic> ::= </para>
      <para>     | <legacyItalic>ODBC-esc-initiator</legacyItalic> [?=] call <legacyItalic>procedure ODBC-esc-terminator</legacyItalic></para>
      <para>
        <legacyItalic>procedure</legacyItalic> ::= <legacyItalic>procedure-name</legacyItalic> | <legacyItalic>procedure-name</legacyItalic> (<legacyItalic>procedure-parameter-list</legacyItalic>)</para>
      <para>
        <legacyItalic>procedure-identifier</legacyItalic> ::= <legacyItalic>user-defined-name</legacyItalic></para>
      <para>
        <legacyItalic>procedure-name</legacyItalic> ::= <legacyItalic>procedure-identifier</legacyItalic> </para>
      <para>     | <legacyItalic>owner-name</legacyItalic>.<legacyItalic>procedure-identifier</legacyItalic> </para>
      <para>     | <legacyItalic>catalog-name catalog-separator</legacyItalic> <legacyItalic>procedure-identifier</legacyItalic> </para>
      <para>     | <legacyItalic>catalog-name catalog-separator</legacyItalic> [<legacyItalic>owner-name</legacyItalic>].<legacyItalic>procedure-identifier</legacyItalic> </para>
      <para>(The third syntax is valid only if the data source does not support owners.)</para>
      <para>
        <legacyItalic>owner-name</legacyItalic> ::= <legacyItalic>user-defined-name</legacyItalic></para>
      <para>
        <legacyItalic>catalog-name</legacyItalic> ::= <legacyItalic>user-defined-name</legacyItalic></para>
      <para>
        <legacyItalic>catalog-separator</legacyItalic> ::= {<legacyItalic>implementation-defined</legacyItalic>} </para>
      <para>(The catalog separator is returned through <legacyBold>SQLGetInfo </legacyBold>with the SQL_CATALOG_NAME_SEPARATOR information option.)</para>
      <para>
        <legacyItalic>procedure-parameter-list</legacyItalic> ::= <legacyItalic>procedure-parameter</legacyItalic> </para>
      <para>     | <legacyItalic>procedure-parameter</legacyItalic>, <legacyItalic>procedure-parameter-list</legacyItalic></para>
      <para>
        <legacyItalic>procedure-parameter</legacyItalic> ::= <legacyItalic>dynamic-parameter</legacyItalic> | <legacyItalic>literal</legacyItalic> | <legacyItalic>empty-string</legacyItalic></para>
      <para>
        <legacyItalic>empty-string </legacyItalic>::= </para>
      <para>
        <legacyItalic>ODBC-esc-initiator </legacyItalic>::= {</para>
      <para>
        <legacyItalic>ODBC-esc-terminator </legacyItalic>::= } </para>
      <para>(If a procedure parameter is an empty string, the procedure uses the default value for that parameter.)</para>
      <para>To determine whether the data source supports procedures and the driver supports the ODBC procedure invocation syntax, an application can call <legacyBold>SQLGetInfo</legacyBold> with the SQL_PROCEDURES information type.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>