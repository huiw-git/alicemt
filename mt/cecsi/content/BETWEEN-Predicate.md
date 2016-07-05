---
title: BETWEEN Predicate
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
translation.priority.ht: 
  - en-gb
---
# BETWEEN Predicate
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The syntax:</para>
  </introduction>
  <section>
    <content>
      <code>expression1 BETWEEN expression2 AND expression3</code>
      <para>returns true only if <legacyItalic>expression1</legacyItalic> is greater than or equal to <legacyItalic>expression2</legacyItalic> and <legacyItalic>expression1</legacyItalic> is less than or equal to <legacyItalic>expression3</legacyItalic>.</para>
      <para>The semantics of this syntax are different for the Desktop Database Drivers and the Microsoft Jet engine. In Microsoft Jet SQL, <legacyItalic>expression2</legacyItalic> can be greater than <legacyItalic>expression3 </legacyItalic>so that the statement will return TRUE only if <legacyItalic>expression1</legacyItalic> is greater than or equal to <legacyItalic>expression3</legacyItalic>, and <legacyItalic>expression1</legacyItalic> is less than or equal to <legacyItalic>expression2</legacyItalic>.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>