---
title: "WriteText Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
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
# WriteText Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Writes a specified text string to a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Stream</parameterReference><legacyBold>.WriteText</legacyBold> <parameterReference>Data</parameterReference><legacyBold>,</legacyBold> <parameterReference>Options</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Data</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>String</legacyBold> value that contains the text in characters to be written.</para>
        </definition>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7">StreamWriteEnum</legacyLink> value that specifies whether a line separator character must be written at the end of the specified string.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Specified strings are written to the <legacyBold>Stream</legacyBold> object without any intervening spaces or characters between each string.</para>
      <para>The current <legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> is set to the character following the written data. The <legacyBold>WriteText</legacyBold> method does not truncate the rest of the data in a stream. If you want to truncate these characters, call <legacyLink xlink:href="707c18ca-6a56-4970-bbd6-ae1fb86a0b8a">SetEOS</legacyLink>.</para>
      <para>If you write past the current <legacyLink xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS</legacyLink> position, the <legacyLink xlink:href="a487c241-d953-4c31-ae7e-6358d5cf6733">Size</legacyLink> of the <legacyBold>Stream</legacyBold> will be increased to contain any new characters, and <legacyBold>EOS</legacyBold> will move to the new last byte in the <legacyBold>Stream</legacyBold>.</para>
      <alert class="note">
        <para>The <legacyBold>WriteText</legacyBold> method is used with text streams (<legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type</legacyLink> is <legacyBold>adTypeText</legacyBold>). For binary streams (<legacyBold>Type</legacyBold> is <legacyBold>adTypeBinary</legacyBold>), use <legacyLink xlink:href="02982e6a-ac5f-4af2-b82e-ce12534b84b2">Write</legacyLink>.</para>
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
<link xlink:href="02982e6a-ac5f-4af2-b82e-ce12534b84b2">Write Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>