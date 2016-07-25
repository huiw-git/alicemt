---
title: "AbsolutePage Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ddb58a35-ec3a-423c-a504-3c65e62c23d4
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
# AbsolutePage Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates on which page the current record resides.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>For 32-bit code, sets or returns a <languageKeyword>Long</languageKeyword> value from 1 to the number of pages in the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object (<legacyLink xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount</legacyLink>), or returns one of the <legacyLink xlink:href="e69af0a5-3405-4b72-9c6e-6b188ff746fd">PositionEnum</legacyLink> values.</para>
      <para>For 64-bit code, use a data type that provides for storage of a 64-bit value. For example, you can use either <languageKeyword>Long</languageKeyword> or another value that can be 64-bit length such as DBORDINAL. Do not use <legacyBold>PositionEnum</legacyBold> values because they are limited to 32-bit length.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>This property can be used to identify the page number on which the current record is located. It uses the <legacyLink xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize</legacyLink> property to logically divide the total rowset count of the <legacyBold>Recordset</legacyBold> object into a series of pages, each of which has the number of records equal to <legacyBold>PageSize</legacyBold> (except for the last page, which may have fewer records). The provider must support the appropriate functionality for this property to be available.  </para>
      <list class="bullet">
        <listItem>
          <para>When getting or setting the <legacyBold>AbsolutePage</legacyBold> property, ADO uses the <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink> property and the <legacyLink xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize</legacyLink> property together as follows:</para>
        </listItem>
        <listItem>
          <para>To get the <legacyBold>AbsolutePage</legacyBold>, ADO first retrieves the <legacyBold>AbsolutePosition</legacyBold>, and then divides it by the <legacyBold>PageSize</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>To set the <legacyBold>AbsolutePage</legacyBold>, ADO moves the <legacyBold>AbsolutePosition</legacyBold> as follows: it multiplies the <legacyBold>PageSize</legacyBold> by the new <legacyBold>AbsolutePage</legacyBold> value and then adds 1 to the value. As a result, the current position in the <legacyBold>Recordset</legacyBold> after successfully setting <legacyBold>AbsolutePage</legacyBold> is the first record in that page.</para>
        </listItem>
      </list>
      <para>Like the <legacyBold>AbsolutePosition</legacyBold> property, <legacyBold>AbsolutePage</legacyBold> is 1-based and equals 1 when the current record is the first record in the <legacyBold>Recordset</legacyBold>. Set this property to move to the first record of a particular page. Obtain the total number of pages from the <legacyBold>PageCount</legacyBold> property.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="5aaada64-5115-4adc-8668-827348f32566">Visual Basic Example</link>
<link xlink:href="38ca4e1b-c109-4fba-b590-bdd6994f770e">Visual C++ Example</link>
<link xlink:href="05f9f20e-0697-46bf-b004-76d7fc2e5d52">Visual J++ Example</link>
<link xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition Property</link>
<link xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount Property</link>
<link xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>