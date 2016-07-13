---
title: GUID Escape Sequences
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# GUID Escape Sequences
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC uses escape sequences for GUID literals. The syntax of this escape sequence is as follows:</para>
  </introduction>
  <section>
    <content>
      <code>{<legacyItalic>guid</legacyItalic> '<legacyItalic>nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn</legacyItalic>'}</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>In BNF notation, the syntax is as follows:</para>
      <para>
        <legacyItalic>ODBC-guid-escape</legacyItalic> ::=
     <legacyItalic>ODBC-esc-initiator guid</legacyItalic> '<legacyItalic>guid-value</legacyItalic>' <legacyItalic>ODBC-esc-terminator</legacyItalic></para>
      <para>
        <legacyItalic>ODBC-esc-initiator</legacyItalic> ::= {</para>
      <para>
        <legacyItalic>ODBC-esc-terminator</legacyItalic> ::= }</para>
      <para>
        <legacyItalic>guid-value</legacyItalic> ::= <legacyItalic>clock-low-value guid-separator clock-middle-value guid-separator clock-high-value guid-separator clock-seq-value guid-separator node-value</legacyItalic></para>
      <para>
        <legacyItalic>guid-separator</legacyItalic> ::= -</para>
      <para>
        <legacyItalic>clock-low-value</legacyItalic> ::= <legacyItalic>hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit</legacyItalic></para>
      <para>
        <legacyItalic>clock-middle-value</legacyItalic> ::= <legacyItalic>hex_digit hex_digit hex_digit hex_digit</legacyItalic></para>
      <para>
        <legacyItalic>clock-high-value</legacyItalic> ::= <legacyItalic>hex_digit hex_digit hex_digit hex_digit </legacyItalic></para>
      <para>
        <legacyItalic>clock-seq-value</legacyItalic> ::= <legacyItalic>hex_digit hex_digit hex_digit hex_digit</legacyItalic></para>
      <para>
        <legacyItalic>clock-node-value</legacyItalic> ::= <legacyItalic>hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit</legacyItalic></para>
      <para>
        <legacyItalic>hex_digit</legacyItalic> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F</para>
      <para>The GUID literal escape sequence is supported if the GUID data type is supported by the data source. An application should call <legacyBold>SQLGetTypeInfo</legacyBold> to determine whether this data type is supported.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>