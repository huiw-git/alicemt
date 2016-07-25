---
title: "Optimize Property-Dynamic (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
caps.latest.revision: 10
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
# Optimize Property-Dynamic (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether an index should be created on a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">field</legacyLink>.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Boolean</languageKeyword> value that indicates whether an index should be created.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>An index can improve the performance of operations that find or sort values in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. The index is internal to ADO; you cannot explicitly access or use it in your application.</para>
      <para>To create an index on a field, set the <legacyBold>Optimize</legacyBold> property to <languageKeyword>True</languageKeyword>. To delete the index, set this property to <languageKeyword>False</languageKeyword>.</para>
      <para>
        <legacyBold>Optimize</legacyBold> is a dynamic property appended to the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection when the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property is set to <legacyBold>adUseClient</legacyBold>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Usage</title>
    <content>
      <code>Dim rs As New Recordset
Dim fld As Field
rs.CursorLocation = adUseClient      'Enable index creation
rs.Fields.Append "Field1", adChar, 35, adFldIsNullable
rs.Open
Set fld = rs.Fields(0)
fld.Properties("Optimize") = True    'Create an index
fld.Properties("Optimize") = False   'Delete an index</code>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">field</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="652194af-cfa4-4aa0-a6d6-fa409bbc3f98">Visual Basic Example</link>
<link xlink:href="cb335455-b027-4f66-868d-d0d8b2175de1">Visual C++ Example</link>
<link xlink:href="a75d5239-54a9-4eec-b144-a5848cdbf265">Visual J++ Example</link>
<link xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter Property</link>
<link xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find Method</link>
<link xlink:href="3683ffa0-6f93-4906-9533-ef6942f24f39">Sort Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>