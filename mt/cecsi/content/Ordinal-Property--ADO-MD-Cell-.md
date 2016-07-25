---
title: "Ordinal Property (ADO MD Cell)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
caps.latest.revision: 11
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Ordinal Property (ADO MD Cell)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Uniquely identifies a <legacyLink xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">cell</legacyLink> by its position within a cellset.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns a <languageKeyword>Long</languageKeyword> integer and is read-only.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The cell's ordinal value uniquely identifies the cell within a cellset. Conceptually, cells are numbered in a cellset as if the cellset were a <legacyItalic>p</legacyItalic>-dimensional array, where <legacyItalic>p</legacyItalic> is the number of <legacyLink xlink:href="072fb21a-ec0f-4b02-9022-1cef3ad4bfff">axes</legacyLink>. Cells are numbered starting from zero in row-major order. Here is the formula for calculating the ordinal number of a cell:</para>
      <para>The cell's ordinal value can be used with the <legacyLink xlink:href="0e93d79b-b12e-4e98-889e-c2dfcca20fd0">Item</legacyLink> property of the <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> object to quickly retrieve the <legacyLink xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell</legacyLink>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell Object (ADO MD)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b4647211-2566-4657-ae7b-3dd761457d7b">VBScript Example</link>
<link xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset Object</link>
<link xlink:href="0e93d79b-b12e-4e98-889e-c2dfcca20fd0">Item Property (Cellset)</link>
<link xlink:href="6efe8b5d-a2d5-43a9-a5ea-f9244f8d4ec9">Ordinal Property (Position)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>