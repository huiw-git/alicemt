---
title: "CopyTo Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b4aa5714-916b-48b8-8b09-cc2708379602
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
# CopyTo Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Copies the specified number of characters or bytes (depending on <legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type</legacyLink>) in the <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> to another <legacyBold>Stream</legacyBold> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Stream</parameterReference><legacyBold>.CopyTo</legacyBold> <parameterReference>DestStream</parameterReference><legacyBold>, </legacyBold><parameterReference>NumChars</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>DestStream</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable value that contains a reference to an open <legacyBold>Stream</legacyBold> object. The current <legacyBold>Stream</legacyBold> is copied to the destination <legacyBold>Stream</legacyBold> specified by <legacyItalic>DestStream</legacyItalic>. The destination <legacyBold>Stream</legacyBold> must already be open. If not, a run-time error occurs.</para>
          <alert class="note">
            <para>The <legacyItalic>DestStream</legacyItalic> parameter may not be a proxy of <legacyBold>Stream</legacyBold> object because this requires access to a private interface on the <legacyBold>Stream</legacyBold> object that cannot be remoted to the client.</para>
          </alert>
        </definition>
        <definedTerm> <legacyItalic>NumChars</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. An <languageKeyword>Integer</languageKeyword> value that specifies the number of bytes or characters to be copied from the current position in the source <legacyBold>Stream</legacyBold> to the destination <legacyBold>Stream</legacyBold>. The default value is –1, which specifies that all characters or bytes are copied from the current position to <legacyLink xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS</legacyLink>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>This method copies the specified number of characters or bytes, starting from the current position specified by the <legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> property. If the specified number is more than the available number of bytes until <legacyBold>EOS</legacyBold>, then only characters or bytes from the current position to <legacyBold>EOS</legacyBold> are copied. If the value of <legacyItalic>NumChars </legacyItalic>is –1, or omitted, all characters or bytes starting from the current position are copied.</para>
      <para>If there are existing characters or bytes in the destination stream, all contents beyond the point where the copy ends remain, and are not truncated. <legacyBold>Position</legacyBold> becomes the byte immediately following the last byte copied. If you want to truncate these bytes, call <legacyLink xlink:href="707c18ca-6a56-4970-bbd6-ae1fb86a0b8a">SetEOS</legacyLink>.</para>
      <para>
        <legacyBold>CopyTo</legacyBold> should be used to copy data to a destination <legacyBold>Stream</legacyBold> of the same type as the source <legacyBold>Stream</legacyBold> (their <legacyBold>Type</legacyBold> property settings are both <legacyBold>adTypeText</legacyBold> or both <legacyBold>adTypeBinary</legacyBold>). For text <legacyBold>Stream</legacyBold> objects, you can change the <legacyLink xlink:href="e42507cb-9b46-4ce4-8191-2948eaf14ca2">Charset</legacyLink> property setting of the destination <legacyBold>Stream</legacyBold> to translate from one character set to another. Also, text <legacyBold>Stream</legacyBold> objects can be successfully copied into binary <legacyBold>Stream</legacyBold> objects, but binary <legacyBold>Stream</legacyBold> objects cannot be copied into text <legacyBold>Stream</legacyBold> objects.</para>
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
  <relatedTopics />
</developerReferenceWithSyntaxDocument>