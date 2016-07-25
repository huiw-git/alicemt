---
title: "StayInSync Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
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
# StayInSync Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates, in a hierarchical <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, whether the reference to the underlying child records (that is, the <legacyItalic>chapter</legacyItalic>) changes when the parent row position changes.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Boolean</languageKeyword> value. The default value is <languageKeyword>True</languageKeyword>. If <languageKeyword>True</languageKeyword>, the chapter will be updated if the parent <legacyBold>Recordset</legacyBold> object changes row position; if <languageKeyword>False</languageKeyword>, the chapter will continue to refer to data in the previous chapter even though the parent <legacyBold>Recordset</legacyBold> object has changed row position.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>This property applies to hierarchical recordsets, such as those supported by the <legacyLink xlink:href="523009ce-e01b-4e2d-a7df-816d7688aff0">Microsoft Data Shaping Service for OLE DB</legacyLink>, and must be set on the parent <legacyBold>Recordset</legacyBold> before the child <legacyBold>Recordset</legacyBold> is retrieved. This property simplifies navigating hierarchical recordsets.</para>
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
<link xlink:href="b682bcc3-04b3-42b0-86f4-c17e0cd29baf">Visual Basic Example</link>
<link xlink:href="523009ce-e01b-4e2d-a7df-816d7688aff0">Microsoft Data Shaping Service for OLE DB</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>