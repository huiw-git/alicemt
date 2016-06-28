---
title: Numeric Literal Syntax
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
translation.priority.ht: 
  - en-gb
---
# Numeric Literal Syntax
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following syntax is used for numeric literals in ODBC:</para>
  </introduction>
  <section>
    <content>
      <para>
        <legacyItalic>numeric-literal</legacyItalic> ::= <legacyItalic>signed-numeric-literal | unsigned-numeric-literal </legacyItalic></para>
      <para>
        <legacyItalic>signed-numeric-literal </legacyItalic>::= [<legacyItalic>sign</legacyItalic>]<legacyItalic> unsigned-numeric-literal</legacyItalic></para>
      <para>
        <legacyItalic>unsigned-numeric-literal</legacyItalic> ::= <legacyItalic>exact-numeric-literal | approximate-numeric-literal</legacyItalic></para>
      <para>
        <legacyItalic>exact-numeric-literal </legacyItalic>::= <legacyItalic>unsigned-integer </legacyItalic>[<legacyItalic>period</legacyItalic>[<legacyItalic>unsigned-integer</legacyItalic>]]<legacyItalic> |period unsigned-integer</legacyItalic></para>
      <para>
        <legacyItalic>sign </legacyItalic>::=<legacyItalic> plus-sign | minus-sign</legacyItalic></para>
      <para>
        <legacyItalic>approximate-numeric-literal </legacyItalic>::= <legacyItalic>mantissa E exponent</legacyItalic></para>
      <para>
        <legacyItalic>mantissa </legacyItalic>::= <legacyItalic>exact-numeric-literal</legacyItalic></para>
      <para>
        <legacyItalic>exponent</legacyItalic> ::= <legacyItalic>signed-integer</legacyItalic></para>
      <para>
        <legacyItalic>signed-integer</legacyItalic> ::= [<legacyItalic>sign</legacyItalic>] <legacyItalic>unsigned-integer</legacyItalic></para>
      <para>
        <legacyItalic>unsigned-integer</legacyItalic> ::= <legacyItalic>digit...</legacyItalic></para>
      <para>
        <legacyItalic>plus-sign </legacyItalic>::= <legacyItalic>+</legacyItalic></para>
      <para>
        <legacyItalic>minus-sign </legacyItalic>::= -</para>
      <para>
        <legacyItalic>digit</legacyItalic> ::= 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 0</para>
      <para>
        <legacyItalic>period</legacyItalic> ::= .</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>