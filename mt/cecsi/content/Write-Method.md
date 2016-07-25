---
title: "Write Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
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
# Write Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Writes binary data to a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Stream</parameterReference><legacyBold>.Write</legacyBold> <parameterReference>Buffer</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Buffer</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>Variant</languageKeyword> that contains an array of bytes to be written.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Specified bytes are written to the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> object without any intervening spaces between each byte.</para>
      <para>The current <legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> is set to the byte following the written data. The <unmanagedCodeEntityReference>Write</unmanagedCodeEntityReference> method does not truncate the rest of the data in a stream. If you want to truncate these bytes, call <legacyLink xlink:href="707c18ca-6a56-4970-bbd6-ae1fb86a0b8a">SetEOS</legacyLink>.</para>
      <para>If you write past the current <legacyLink xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS</legacyLink> position, the <legacyLink xlink:href="a487c241-d953-4c31-ae7e-6358d5cf6733">Size</legacyLink> of the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> will be increased to contain any new bytes, and <unmanagedCodeEntityReference>EOS</unmanagedCodeEntityReference> will move to the new last byte in the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference>.</para>
      <alert class="note">
        <para>The <unmanagedCodeEntityReference>Write</unmanagedCodeEntityReference> method is used with binary streams (<legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type</legacyLink> is <legacyBold>adTypeBinary</legacyBold>). For text streams (<legacyBold>Type</legacyBold> is <legacyBold>adTypeText</legacyBold>), use <legacyLink xlink:href="7a669048-13f4-4574-a2b1-985e089729d5">WriteText</legacyLink>.</para>
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
<link xlink:href="7a669048-13f4-4574-a2b1-985e089729d5">WriteText Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>