---
title: "Position Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d
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
# Position Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the current position within a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Long</languageKeyword> value that specifies the offset, in number of bytes, of the current position from the beginning of the stream. The default is 0, which represents the first byte in the stream.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The current position can be moved to a point after the end of the stream. If you specify the current position beyond the end of the stream, the <legacyLink xlink:href="a487c241-d953-4c31-ae7e-6358d5cf6733">Size</legacyLink> of the <legacyBold>Stream</legacyBold> object will be increased accordingly. Any new bytes added in this way will be null.</para>
      <alert class="note">
        <para>  <legacyBold>Position</legacyBold> always measures bytes. For text streams using multibyte character sets, multiply the position by the character size to determine the character number. For example, for a two-byte character set, the first character is at position 0, the second character at position 2, the third character at position 4, and so on.</para>
      </alert>
      <alert class="note">
        <para>Negative values cannot be used to change the current position in a <legacyBold>Stream</legacyBold>. Only positive numbers can be used for <legacyBold>Position</legacyBold>.</para>
      </alert>
      <alert class="note">
        <para>For read-only <legacyBold>Stream</legacyBold> objects, ADO will not return an error if <legacyBold>Position</legacyBold> is set to a value greater than the <legacyBold>Size</legacyBold> of the <legacyBold>Stream</legacyBold>. This does not change the size of the <legacyBold>Stream</legacyBold>, or alter the <legacyBold>Stream</legacyBold> contents in any way. However, doing this should be avoided because it results in a meaningless <legacyBold>Position</legacyBold> <?Comment JT: deleted broken link to Visual Basic Example mdhowstep4populatedetailstextbox | 2006-02-02T19:47:00Z  Id='0?>value<?CommentEnd Id='0'
    ?>.</para>
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
<link xlink:href="e42507cb-9b46-4ce4-8191-2948eaf14ca2">Charset Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>