---
title: Interval Literal Syntax
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Interval Literal Syntax
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following syntax is used for interval literals in ODBC.</para>
    <para>
      <legacyItalic>interval-literal ::= INTERVAL </legacyItalic>[+<legacyItalic>|</legacyItalic>-]<legacyItalic> interval-string interval-qualifier</legacyItalic></para>
    <para>
      <legacyItalic>interval-string</legacyItalic> ::= <legacyItalic>quote</legacyItalic> { <legacyItalic>year-month-literal</legacyItalic> | <legacyItalic>day-time-literal</legacyItalic> } <legacyItalic>quote</legacyItalic></para>
    <para>
      <legacyItalic>year-month-literal</legacyItalic> ::= <legacyItalic>years-value</legacyItalic> | [<legacyItalic>years-value</legacyItalic> -] <legacyItalic>months-value</legacyItalic></para>
    <para>
      <legacyItalic>day-time-literal</legacyItalic> ::= <legacyItalic>day-time-interval</legacyItalic> | <legacyItalic>time-interval</legacyItalic></para>
    <para>
      <legacyItalic>day-time-interval</legacyItalic> ::= <legacyItalic>days-value</legacyItalic> [<legacyItalic>hours-value</legacyItalic> [:<legacyItalic>minutes-value</legacyItalic>[:<legacyItalic>seconds-value</legacyItalic>]]]</para>
    <para>
      <legacyItalic>time-interval</legacyItalic> ::= <legacyItalic>hours-value</legacyItalic> [:<legacyItalic>minutes-value</legacyItalic> [:<legacyItalic>seconds-value</legacyItalic> ] ]  </para>
    <para>     | <legacyItalic>minutes-value</legacyItalic> [:<legacyItalic>seconds-value</legacyItalic> ]  </para>
    <para>     | <legacyItalic>seconds-value</legacyItalic></para>
    <para>
      <legacyItalic>years-value</legacyItalic> ::= <legacyItalic>datetime-value</legacyItalic></para>
    <para>
      <legacyItalic>months-value</legacyItalic> ::= <legacyItalic>datetime-value</legacyItalic></para>
    <para>
      <legacyItalic>days-value</legacyItalic> ::= <legacyItalic>datetime-value</legacyItalic></para>
    <para>
      <legacyItalic>hours-value</legacyItalic> ::= <legacyItalic>datetime-value</legacyItalic></para>
    <para>
      <legacyItalic>minutes-value</legacyItalic> ::= <legacyItalic>datetime-value</legacyItalic></para>
    <para>
      <legacyItalic>seconds-value</legacyItalic> ::= <legacyItalic>seconds-integer-value</legacyItalic> [.[<legacyItalic>seconds-fraction</legacyItalic>] ]</para>
    <para>
      <legacyItalic>seconds-integer-value</legacyItalic> ::= <legacyItalic>unsigned-integer</legacyItalic></para>
    <para>
      <legacyItalic>seconds-fraction</legacyItalic> ::= <legacyItalic>unsigned-integer</legacyItalic></para>
    <para>
      <legacyItalic>datetime-value</legacyItalic> ::= <legacyItalic>unsigned-integer</legacyItalic></para>
    <para>
      <legacyItalic>interval-qualifier</legacyItalic> ::= <legacyItalic>start-field</legacyItalic> TO <legacyItalic>end-field</legacyItalic> | <legacyItalic>single-datetime-field</legacyItalic></para>
    <para>
      <legacyItalic>start-field</legacyItalic> ::= <legacyItalic>non-second-datetime-field</legacyItalic> [(<legacyItalic>interval-leading-field-precision</legacyItalic> )]</para>
    <para>
      <legacyItalic>end-field</legacyItalic> ::= <legacyItalic>non-second-datetime-field</legacyItalic>       | SECOND[(<legacyItalic>interval-fractional-seconds-precision</legacyItalic>)]</para>
    <para>
      <legacyItalic>single-datetime-field</legacyItalic> ::= <legacyItalic>non-second-datetime-field</legacyItalic> [(<legacyItalic>interval-leading-field-precision</legacyItalic>)] | SECOND[(<legacyItalic>interval-leading-field-precision </legacyItalic>[, (<legacyItalic>interval-fractional-seconds-precision</legacyItalic>)]</para>
    <para>
      <legacyItalic>datetime-field</legacyItalic> ::= <legacyItalic>non-second-datetime-field</legacyItalic> | SECOND</para>
    <para>
      <legacyItalic>non-second-datetime-field</legacyItalic> ::= YEAR | MONTH | DAY | HOUR | MINUTE</para>
    <para>
      <legacyItalic>interval-fractional-seconds-precision</legacyItalic> ::= <legacyItalic>unsigned-integer</legacyItalic></para>
    <para>
      <legacyItalic>interval-leading-field-precision</legacyItalic> ::= <legacyItalic>unsigned-integer</legacyItalic></para>
    <para>
      <legacyItalic>quote</legacyItalic> ::= '</para>
    <para>
      <legacyItalic>unsigned-integer</legacyItalic> ::= <legacyItalic>digit...</legacyItalic></para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>