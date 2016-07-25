---
title: "Read Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
caps.latest.revision: 12
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
# Read Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Reads a specified number of bytes from a binary <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Variant = Stream</parameterReference><legacyBold>.Read ( </legacyBold><parameterReference>NumBytes</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>NumBytes</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Long</legacyBold> value that specifies the number of bytes to read from the file or the <legacyLink xlink:href="cfa1b416-003a-436f-a21b-bd2397e54db3">StreamReadEnum</legacyLink> value <legacyBold>adReadAll</legacyBold>, which is the default.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <returnValue>
    <content>
      <para>The <legacyBold>Read </legacyBold>method reads a specified number of bytes or the entire stream from a <legacyBold>Stream</legacyBold> object and returns the resulting data as a <legacyBold>Variant</legacyBold>.</para>
    </content>
  </returnValue>
  <languageReferenceRemarks>
    <content>
      <para>If <legacyItalic>NumBytes</legacyItalic> is more than the number of bytes left in the <legacyBold>Stream</legacyBold>, only the bytes remaining are returned. The data read is not padded to match the length specified by <legacyItalic>NumBytes</legacyItalic>. If there are no bytes left to read, a variant with a null value is returned. <legacyBold>Read</legacyBold> cannot be used to read <?Comment JT: deleted broken link to VB example 2006-02-02T19:38:00Z  Id='0?>backwards<?CommentEnd Id='0'
    ?>.</para>
      <alert class="note">
        <para> <legacyItalic>NumBytes</legacyItalic> always measures bytes. For text <legacyBold>Stream</legacyBold> objects (<legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type</legacyLink> is <legacyBold>adTypeText</legacyBold>), use <legacyLink xlink:href="be5a409e-cf87-4859-9ea5-713401755a77">ReadText</legacyLink>.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="be5a409e-cf87-4859-9ea5-713401755a77">ReadText Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>