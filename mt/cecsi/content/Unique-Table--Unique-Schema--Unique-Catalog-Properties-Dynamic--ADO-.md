---
title: "Unique Table, Unique Schema, Unique Catalog Properties-Dynamic (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d0e775d8-e353-46a1-ad10-ed4cc240dfaa
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
# Unique Table, Unique Schema, Unique Catalog Properties-Dynamic (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Enables you to closely control modifications to a particular base table in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> that was formed by a JOIN operation on multiple base tables.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Unique Table</legacyBold> specifies the name of the base table upon which updates, insertions, and deletions are allowed.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Unique Schema</legacyBold> specifies the <legacyItalic>schema</legacyItalic>, or name of the owner of the table.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Unique Catalog</legacyBold> specifies the <legacyItalic>catalog</legacyItalic>, or name of the database containing the table.</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value that is the name of a table, schema, or catalog.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The desired base table is uniquely identified by its catalog, schema, and table names. When the <legacyBold>Unique Table</legacyBold> property is set, the values of the <legacyBold>Unique Schema</legacyBold> or <legacyBold>Unique Catalog</legacyBold> properties are used to find the base table. It is intended, but not required, that either or both the <legacyBold>Unique Schema</legacyBold> and <legacyBold>Unique Catalog</legacyBold> properties be set before the <legacyBold>Unique Table</legacyBold> property is set.</para>
      <para>The primary key of the <legacyBold>Unique Table</legacyBold> is treated as the primary key of the entire <legacyBold>Recordset</legacyBold>. This is the key that is used for any method requiring a primary key.</para>
      <para>While <legacyBold>Unique Table</legacyBold> is set, the <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink> method affects only the named table. The <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink>, <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>, <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink>, and <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> methods affect any appropriate underlying base tables of the <legacyBold>Recordset</legacyBold>.</para>
      <para>
        <legacyBold>Unique Table</legacyBold> must be specified before doing any custom resynchronizations. If <legacyBold>Unique Table</legacyBold> has not been specified, the <legacyLink xlink:href="4e2bb601-0fe8-4d61-b00e-38341d85a6bb">Resync Command</legacyLink> property will have no effect.</para>
      <para>A run-time error results if a unique base table cannot be found.</para>
      <para>These dynamic properties are all appended to the <legacyBold>Recordset</legacyBold> object <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection when the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property is set to <legacyBold>adUseClient</legacyBold>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>