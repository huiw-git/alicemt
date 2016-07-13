---
title: Date, Time, and Timestamp Escape Sequences
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 67b7dee0-e5b1-4469-a626-0c7767852b80
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Date, Time, and Timestamp Escape Sequences
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC defines escape sequences for date, time, and timestamp literals. The syntax of these escape sequences is as follows:</para>
  </introduction>
  <section>
    <content>
      <code>
{<legacyItalic>d</legacyItalic> '<legacyItalic>value</legacyItalic>'}
{<legacyItalic>t </legacyItalic>'<legacyItalic>value</legacyItalic>'}
{<legacyItalic>ts </legacyItalic>'<legacyItalic>value</legacyItalic>'}</code>
      <para>In BNF notation, the syntax is as follows:</para>
      <code>
<legacyItalic>ODBC-date-time-escape</legacyItalic> ::=
     <legacyItalic>ODBC-date-escape</legacyItalic>
     | <legacyItalic>ODBC-time-escape</legacyItalic>
     | <legacyItalic>ODBC-timestamp-escape</legacyItalic>
<legacyItalic>ODBC-date-escape</legacyItalic> ::=
     <legacyItalic>ODBC-esc-initiator</legacyItalic> d '<legacyItalic>date-value</legacyItalic>' <legacyItalic>ODBC-esc-terminator</legacyItalic>
<legacyItalic>ODBC-time-escape </legacyItalic>::=
     <legacyItalic>ODBC-esc-initiator</legacyItalic> t '<legacyItalic>time-value</legacyItalic>' <legacyItalic>ODBC-esc-terminator</legacyItalic>
<legacyItalic>ODBC-timestamp-escape </legacyItalic>::=
     <legacyItalic>ODBC-esc-initiator</legacyItalic> ts '<legacyItalic>timestamp-value</legacyItalic>' <legacyItalic>ODBC-esc-terminator</legacyItalic>
<legacyItalic>ODBC-esc-initiator </legacyItalic>::= {
<legacyItalic>ODBC-esc-terminator </legacyItalic>::= }
<legacyItalic>date-value</legacyItalic> ::= 
     <legacyItalic>years-value date-separator months-value date-separator days-value</legacyItalic>
<legacyItalic>time-value</legacyItalic> ::= 
     <legacyItalic>hours-value time-separator minutes-value time-separatorseconds-value</legacyItalic>
<legacyItalic>timestamp-value </legacyItalic>::= <legacyItalic>date-value timestamp-separator time-value</legacyItalic>
<legacyItalic>date-separator </legacyItalic>::= -
<legacyItalic>time-separator </legacyItalic>::= :
<legacyItalic>timestamp-separator </legacyItalic>::=
     <legacyItalic>(The blank character)</legacyItalic>
<legacyItalic>years-value</legacyItalic> ::= <legacyItalic>digit digit digit digit</legacyItalic>
<legacyItalic>months-value</legacyItalic> ::= <legacyItalic>digit digit</legacyItalic>
<legacyItalic>days-value</legacyItalic> ::= <legacyItalic>digit digit</legacyItalic>
<legacyItalic>hours-value</legacyItalic> ::= <legacyItalic>digit digit</legacyItalic>
<legacyItalic>minutes-value</legacyItalic> ::= <legacyItalic>digit digit</legacyItalic>
<legacyItalic>seconds-value </legacyItalic>::= <legacyItalic>digit digit</legacyItalic>[<legacyItalic>.digit...</legacyItalic>]</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The date, time, and timestamp literal escape sequences are supported if the date, time, and timestamp data types are supported by the data source. An application should call <legacyBold>SQLGetTypeInfo</legacyBold> to determine whether these data types are supported.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>