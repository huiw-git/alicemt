---
title: "PageCount Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
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
# PageCount Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates how many pages of data the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object contains.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <languageKeyword>Long</languageKeyword> value that indicates the number of pages in the <legacyBold>Recordset</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>PageCount</legacyBold> property to determine how many pages of data are in the <legacyBold>Recordset</legacyBold> object. <legacyItalic>Pages</legacyItalic> are groups of records whose size equals the <legacyLink xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize</legacyLink> property setting. Even if the last page is incomplete because there are fewer records than the <legacyBold>PageSize</legacyBold> value, it counts as an additional page in the <legacyBold>PageCount</legacyBold> value. If the <legacyBold>Recordset</legacyBold> object does not support this property, the value will be -1 to indicate that the <legacyBold>PageCount</legacyBold> is indeterminable.</para>
      <para>See the <legacyBold>PageSize</legacyBold> and <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink> properties for more on page functionality.</para>
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
<link xlink:href="5aaada64-5115-4adc-8668-827348f32566">Visual Basic Example</link>
<link xlink:href="38ca4e1b-c109-4fba-b590-bdd6994f770e">Visual C++ Example</link>
<link xlink:href="05f9f20e-0697-46bf-b004-76d7fc2e5d52">Visual J++ Example</link>
<link xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage Property</link>
<link xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize Property</link>
<link xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>