---
title: "Parameter Markers"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Parameter Markers
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In accordance with the SQL-92 specification, an application cannot place parameter markers in the following locations. For a more comprehensive list, see the SQL-92 specification.  </para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>In a <legacyBold>SELECT</legacyBold> list</para>
        </listItem>
        <listItem>
          <para>As both <legacyItalic>expressions</legacyItalic> in a <legacyItalic>comparison-predicate</legacyItalic></para>
        </listItem>
        <listItem>
          <para>As both operands of a binary operator</para>
        </listItem>
        <listItem>
          <para>As both the first and second operands of a <legacyBold>BETWEEN </legacyBold>operation</para>
        </listItem>
        <listItem>
          <para>As both the first and third operands of a <legacyBold>BETWEEN</legacyBold> operation</para>
        </listItem>
        <listItem>
          <para>As both the expression and the first value of an <legacyBold>IN</legacyBold> operation</para>
        </listItem>
        <listItem>
          <para>As the operand of a unary + or – operation</para>
        </listItem>
        <listItem>
          <para>As the argument of a <legacyItalic>set-function-reference</legacyItalic></para>
        </listItem>
      </list>
      <para>For more information about parameter markers, see the SQL-92 specification. For more information about parameters, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>