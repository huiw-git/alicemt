---
title: "Interval Escape Sequences"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Interval Escape Sequences
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC uses escape sequences for interval literals. The syntax of this escape sequence is as follows: </para>
    <para>{<legacyItalic>interval-literal</legacyItalic>}</para>
    <para>For the BNF syntax of <legacyItalic>interval-literal</legacyItalic>, see the <legacyLink xlink:href="2f2d22c1-51d6-4055-9f5a-53bc31e9fea0">Interval Literal Syntax</legacyLink> section later in this appendix.</para>
    <para>The interval literal escape sequence is supported if the interval data types are supported by the data source. An application should call <legacyBold>SQLGetTypeInfo</legacyBold> to determine whether these data types are supported.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>