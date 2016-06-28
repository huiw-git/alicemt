---
title: Scalar Function Escape Sequence
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
translation.priority.ht: 
  - en-gb
---
# Scalar Function Escape Sequence
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC uses escape sequences for scalar functions. The syntax of this escape sequence is as follows: </para>
  </introduction>
  <section>
    <content>
      <code>{fn <legacyItalic>scalar-function</legacyItalic>}</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>In BNF notation, the syntax is as follows:</para>
      <para>
        <legacyItalic>ODBC-scalar-function-escape</legacyItalic> ::= </para>
      <para>     <legacyItalic>ODBC-esc-initiator</legacyItalic> fn <legacyItalic>scalar-function ODBC-esc-terminator</legacyItalic></para>
      <para>
        <legacyItalic>scalar-function</legacyItalic> ::= <legacyItalic>function-name</legacyItalic> (<legacyItalic>argument-list</legacyItalic>) </para>
      <para>(The definitions for the nonterminals <legacyItalic>function-name</legacyItalic> and <legacyItalic>function-name</legacyItalic> (<legacyItalic>argument-list</legacyItalic>) are derived from the list of scalar functions in <legacyLink xlink:href="59c7cd5e-32d6-43ab-bac3-7010322d105a">Appendix E: Scalar Functions</legacyLink>.)</para>
      <para>
        <legacyItalic>ODBC-esc-initiator </legacyItalic>::= {</para>
      <para>
        <legacyItalic>ODBC-esc-terminator </legacyItalic>::= }</para>
      <para>To determine whether the data source supports procedures and the driver supports the ODBC procedure invocation syntax, an application can call <legacyBold>SQLGetInfo</legacyBold>. For more information, see <legacyLink xlink:href="59c7cd5e-32d6-43ab-bac3-7010322d105a">Appendix E: Scalar Functions</legacyLink>.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>