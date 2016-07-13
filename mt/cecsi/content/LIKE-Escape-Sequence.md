---
title: LIKE Escape Sequence
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# LIKE Escape Sequence
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC uses escape sequences for the LIKE clause. The syntax of this escape sequence is as follows: </para>
  </introduction>
  <section>
    <content>
      <code>{'<legacyItalic>escape-character</legacyItalic>'}</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>In BNF notation, the syntax is as follows:</para>
      <para>
        <legacyItalic>ODBC-like-escape</legacyItalic> ::= </para>
      <para>     <legacyItalic>ODBC-esc-initiator</legacyItalic> escape '<legacyItalic>escape-character</legacyItalic>' <legacyItalic>ODBC-esc-terminator</legacyItalic></para>
      <para>
        <legacyItalic>escape-character </legacyItalic>::= <legacyItalic>character</legacyItalic></para>
      <para>
        <legacyItalic>ODBC-esc-initiator</legacyItalic> ::= {</para>
      <para>
        <legacyItalic>ODBC-esc-terminator </legacyItalic>::= }</para>
      <para>To determine if the driver supports the LIKE escape sequence, an application can call <legacyBold>SQLGetInfo</legacyBold> with the SQL_LIKE_ESCAPE_CLAUSE information type.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>